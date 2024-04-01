---
date: 2024-03-24T16:57:45Z
description: ""
draft: false
title: "The Law of Data Transformation"
---

I have a theory that I'm calling the Law of Data Transformation. I can imagine someone has already researched this idea and communicated it with more rigor, so apologies if I'm late to the party.

The essential idea is that **for every layer of data transformation a system requires, the cost of that system will increase logarithmically.**

## A Basic Example

Let's start with an extremely basic example.

```go
x := 10
fmt.Println(x)
```

Here we take a value and transform it into a string. This is exceptionally inexpensive and we do it all the time when programming.

What happens when we accept a value from outside our program? What if we read an environment variable?

```go
import (
	"os"
	"fmt"
)

func main() {
	xStr := os.Getenv("X")

	x, err := strconv.Atoi(xStr)
	if err != nil {
		panic(err)
	}

	fmt.Prinln(x)
}
```

There is likely more error checking to do, but we start to see the Law of Data Transformation rear its head. In our initial example, `x` is an integer. When we think of what `x` is within the scope of our system, it is an integer. While we are simply printing it, and turning it into a string in the process, the idea here is that **variables contain data that has a specific shape and meaning that is most often identified by a type**.

Let's keep moving.

Another realistic example is accepting data via command line flags. I'm a fan of [urfave/cli](https://cli.urfave.org/), so we'll use that. n

```go
import (
	"fmt"
	"log"
	"os"

	"github.com/urfave/cli/v2"
)

func main() {
	app := cli.App{
		Name: "tlodt",
		Flags: []cli.Flag{
			cli.IntFlag{Name: "x"},
		},
		Action: func(c *cli.Context) {
			x := cli.GetInt("x")
			fmt.Println(x)
		},
	}

	if app.Run(os.Args); err != nil {
		log.Fatal(err)
	}
}
```

One argument is that we could have used the standard library [flag](https://pkg.go.dev/flag) package, but it doesn't look radically different.

What does look different is the [code](https://github.com/urfave/cli/blob/main/flag_int.go) necessary to access the `x` value as an integer from a flag. To be clear, I'm not criticizing `urfave/cli` or any other cli library or framework. The point is to make it clear that simply by introducing a transformation from a command line flag to an integer, there results in a lot more code.

One could argue that much of the code in `urfave/cli` has more to do with providing a framework for writing cli apps and you'd be right! At the core of a cli framework is how you parse and transform data to structures your program can use. **Any **transformation** requires documentation** and configuration to make sure the system or person providing the input can react when something goes wrong.**

Let's look at another example.

Rather than a simple cli app, let's look at a simple web application. I'll use [gin](https://gin-gonic.com/), again, because that is my preference.

```go

import (
	"github.com/gin-gonic/gin"
)

type RequestX struct {
	X int `form:"x"`
}

func main() {
	r := gin.Default()

	r.POST("/echo", func(c *gin.Context) {
		var reqX RequestX
		err := c.ShouldBind(&reqX)
		if err != nil {
			c.JSON(400, gin.H{"error": err})
		}

		x := reqX.X

		c.JSON(200, gin.H{"X": x})
	})

	r.Run()
}
```

This is a **very** minimal example, but we see another facet when it comes to data transformation. **As a system becomes distributed, data transformation becomes more complex.**

While the code we're looking at here is simple, the reality is there is a web server that has parsed the HTTP request to process the headers and prepare a request body. Gin then takes on some of the complexity hiding the transformation from a generic form value to a typed struct. Finally, once I have the value, I have to transform it once again to respond.

We haven't even stored anything in a database yet!


## Isn't this just a part of the software development?

In many ways, data transformation is just part of life. I, for one, am extremely thankful for all the hard work folks have done to make the majority of basic transformations necessary to make software.

With that in mind, we often assume that many transformations are required when they are not.

One example is the [htmx tabs example using hateoas](https://htmx.org/examples/tabs-hateoas/). When implementing something like tabs you need to maintain state around what tab is selected and when that state changes. If you're using JavaScript, it isn't a ton of code, but it also isn't intuitive. You've got to find the tab that was selected and unselect it, then set the new tab as selected and show the content.

React and other frameworks have made the code more formalized around state management. There is also Typescript to help ensure data the frontend leverages is correct. But, just as we saw the complexity rise transforming data from a simple variable to a web request, we see the same sort of complexity grow on the frontend.

Based on the htmx hateoas example, this doesn't have to be the case. Rather than taking your application's data, transforming it to an API-compatible format, loading the resulting data into the frontend from the API, validating the data, and finally leveraging it, you could just return the HTML that the frontend is going to end up writing. This reduces the data transformation and greatly reduces the complexity and cost.

Before folks start getting the pitchforks, I want to talk a little about why the Law of Data Transformation is all about cost.

Most applications that become large also have a larger organization. A natural specialization for engineers generally between "frontend" and "backend". The result is the "frontend" teams leverage things like React to be as decoupled from the backend as possible. The "backend" teams do the same thing as it gets them out of having to think about user interfaces at all. They can effectively return JSON and call things done.

The contrast this, take a look at [hey](https://hey.com), which uses the HTML over the Wire ([Hotwire](https://hotwired.dev/)) to create an extremely dynamic application. The other important aspect of Hey is that it was built by [37signals](https://37signals.com/), which is a rather small organization considering they also run [Basecamp, alongside shepherding [Rails](https://rubyonrails.org/) and many other projects.

More importantly though, looking at their book [Shape Up](https://basecamp.com/books/shapeup), which outlines the way they work, you see a team of a designer and an engineer execute on building things. They don't have a frontend vs. backend or specialization, and yet they deliver successful products and projects. Put another way, they are optimizing their business according to the Law of Data Transformation by keeping transformation to a minimum.

The important point here is to recognize there is a business impact in terms of organizational cost (hiring isn't cheap), communication, and people the more data is transformed. Thankfully, the penalty is logarithmic, so over time data transformation eventually becomes a reasonably well-defined function with fewer requirements to add major changes.

## Where It Really Hurts

The arena where the Law of Data Transformation is much more obvious is in the data engineering space. There is a much more direct correlation between ETL/ELT given compute is necessary to perform the transforms.

Consider how data goes from an application to a data warehouse via a data lake.

![image](/images/transforms-diagram.png)

With each transformation, the meaning becomes fuzzier. If we have a field that is an enum defined in the code but is a string or integer in the database, we lose some data. If we are ingesting an event, we get integers or floats when it comes to numbers. Generally, I doubt it is a problem, but the underlying application might have something more specific in mind. In Go, we have float32, float64, etc. In Python, the standard library includes fractions and decimal types. SQLite has an integer and real type whereas Postgres has multiple integer and floating point types to represent different constraints on the size of the numbers. Again, none of this is generally problematic in practice, but when it is a problem, it costs to fix it.

Programmatically adjusting types adds complexity and time. It is possible to decorate data to document the transforms alongside their constraints. Data lineage is a thing. A quick search shows most data lineage products require contacting a salesperson. This means a high Average Contract Value (ACV) and likely a long integration process.

Also, each of these transformations likely happens in discrete infrastructure and/or with discrete systems. You may have [fivetran](https://www.fivetran.com/), [dbt](https://www.getdbt.com/), [airflow](https://airflow.apache.org/), [dagster](https://dagster.io/), [debezium](https://debezium.io/), etc. in the mix, each with its configuration, infrastructure, and observability in place.

The question then is how could you optimize?

The key is avoiding transformations, but assuming the elements of the data pipeline are critical, how can you simply remove transforms?

## Maybe a Data Mesh isn't so hard?

I heard [mixed reviews](https://youtu.be/PhBTci_1aKA?si=QZ83RIbDNvsUR8SR) about Data Mesh. Based on my limited understanding and the discussion of the culture required, I can understand why it is a challenge to do wholistically. But why do you have to have every team in a company delivering data APIs?

One thing that was interesting about a Service Mesh is the concept of a sidecar that controls the connection to the rest of a system. We all have used load balancers. A Service Mesh takes that load balancer and moves it closer to the app. The result is,

1. Everything routes to a single hostname for the service builder
2. Health is considered locally and remotely
3. When a service comes up, it must be allowed into the mesh by upstream sources.

When I first of a Data Mesh, I assumed it would have similar characteristics.

1. Data Producers, such as an eng team, write to a local data sidecar they run within their system.
2. The sidecar ensures local "health" (data validation, transforms functioning, etc.) while remote "health" is considered (data governance).
3. When producers create new types of data, it can be introduced with precision and incrementally.

The question is why does this reduce transformations?

When data leaves the confines of an application, that is a transformation. When the data must cross organizational lines, that is also a transformation. Much like in my HATEOS tabs example, if a team can deliver the precise output that is desired, rather than output that needs to be processed, you will avoid transformations.

For example, in previous roles we had our tables pulled into the warehouse. The data eng team needed to set up the job to pull the data and transform it into a table. What struck me was that the table was essentially the same table that was in our DB. And, in our scenario, we could query our local database without concern about the performance implications. Therefore, I often just queried the database myself rather than going to the warehouse. I had the context and there was no reason to add the overhead.

This context is another important aspect of a service mesh. When your service becomes unhealthy, it will alert, there are logs to help debug, there are metrics to understand performance, and in some cases, the system can try to heal itself. All these features come with the context the team owns. They can add instrumentation to the code, log statements, and scripts to perform operations directly.

In a data mesh (from my perspective) the local data sidecar can be utilized to answer questions directly and within the context of the team and the code. Teams can formalize metrics that impact the business and format those metrics via BI tooling to communicate that impact. When a team increases X by Y, the business impact is made visible. In this way, teams reduce the cognitive transformation needed to take system data and present it to the business.

After all, the reason for all this data and analysis is to influence how we behave. If you are delivering software, then changing the behaviors of the software or those writing the software goes a long way to realize and test ideas that were inspired by the data. The graphs aren't the goal.

## Wrapping Up with some pining about REST

One aspect of REST that I always felt got lost was the concept of a document. The association of CRUD to HTTP methods quickly became the standard without recognizing the power of the documents returned. The examples in [the book](https://www.amazon.com/RESTful-Web-Services-Leonard-Richardson/dp/0596529260) were often just HTML (or xhtml which was more popular at the time) rather than JSON. A suggestion from the book was to leverage query string parameters to communicate with the service what you want in the output. We obviously do this today, but what is interesting is that with HTML and XML, you could encapsulate multiple document types. An XML document could contain HTML documents, binary data, etc. Therefore, assuming the service supported it, you could simply ask it to create the document you needed, rather than the data. Put another way, REST started with ideas of how to keep transformations to a minimum.

At its core, the Law of Data Transformation describes the cost of working with raw data and the price of flexibility. There are times when that cost is completely justified, while other times, you could save some money by simplifying.

Personally, I'm a fan of simplifying.

If you want to disagree or discuss any of this, hit me up on [LinkedIn](https://www.linkedin.com/in/ericlarson/).
