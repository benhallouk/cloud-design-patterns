# Queue-based Load Leveling Pattern

When designing applications arround concurrency it is important to distribute the load on your services/processes that the application uses so that the application will stay avalaible and performaned the *Queue-based Load Leveling Pattern* can help a lot by adding an intermediate queue that keep track of the messages sent to be proccesed by the the right application services.

Suppose you have a web application with a API backend, it would be very hard to guess the number of requests per second the application can make to the backedn API this would depend upon the users and what they try to do, worst then that the application may suffer from overloaded requests that can make the entire application unavalaible and of course the application is unscalable as we can not predict the right numbers to scale the application or we may choose to scale to the maximum either way we have wasted resources and this would not go in the right direction.

Luckly the *Queue-based Load Leveling Pattern* will allow us to solve all this issue by placing a queue between the application and the backend API

```
Application ----->   Queue  -----> API
```

This would change the application to send messages to a `Queue` that can be consumed by the `API` the API would then communicate back to the application `asynchronously` if needed as we do not know when the message would be pickedup

- Application would have to create messsages that fit in the Queue
- Application would have to encrypt the messages
- When scaling there will be multiple queue which means the application will need a strategy to relay on to determin the right queue to use
- To get the data asynchronously from the API you would use Pub/Sub such as WebHooks or to use Async Task that uses same data source
- Services have to use the Queue either by subscrbing to the queue or by Fetching/Geting messages manually
