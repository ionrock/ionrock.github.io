---
date: 2024-03-24
draft: true
---

# Don't Copy Your Data Model

If you're building something, avoid copying your data model as much as possible



I remember when AJAX became a thing and it was really exciting. Making your frontend a client of a backend API felt like a natural way to decouple systems. But, that wasn't true. Let's look at why.

The theory when decoupling your frontend from your backend is you gain flexibility.

```sequence
Frontend->Backend: Req to API
Backend->Frontend: Resp from API
```

In this diagram, there is no coupling between the backend and frontend. You have complete freedom in the frontend to do whatever you want. The backend may not even be your own service. You can easily scale to infinity because these are completely decoupled.

The frontend folks arguably get freedom and the backend folks gain purity. Win win.

The reality is much different.

```sequence
UI->Frontend Data Model: Validations
Frontend Data Model-->UI: Errors!
Frontend Data Model->API Client: Convert to API
API Client->API Server: API to Server Models
API Server->Data Model: Validations
Data Model-->UI: Errors!
Data Model->Data Store: Saved

```

I've excluded the response here because it is effectively the same process of converting the data back into models that can be rendered by the UI.

What is painful is that
