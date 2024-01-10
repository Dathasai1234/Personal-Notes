
- [[#Benefits|Benefits]]
	- [[#Benefits#2 types of Functions|2 types of Functions]]



Azure Functions is a **serverless compute service** that lets you run code in response to events or triggers without managing servers. You write your code in small, single-purpose functions, and Azure Functions handles the infrastructure, scaling, and execution of your code.

- ! Azure Functions is an **event-driven**, **serverless** compute option that doesn’t require maintaining virtual machines or containers.

- If you build an app using VM’s or containers, those resources have to be “running” in order for your app to function.
- With Functions, <u>an event wakes the function</u>, alleviating the need to keep resources provisioned when there are no events.
## Benefits

- Using Azure functions is ideal when you’re only concerned about the code running your service and not about the underlying platform or infrastructure.
- & Commonly used when you need to perform **work** in response to an **event** (often via a <u>REST</u> request).
- Functions scale automatically based on *demand*.
- Azure Functions runs your code when it’s triggered and automatically deallocates resources when the function is finished.
- ! Only charged for the <u>CPU time used while your function runs</u>.

### 2 types of Functions

- `stateless (default)`:
they behave as if they're restarted every time they respond to an event.
- `statefull`:
(called Durable Functions), a context is passed through the function to track prior activity.

---

