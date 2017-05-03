# Cloud Design Patterns

This is set of best practices and design patterns that must be used in the cloud to improve the availability and resilience

## Circuit Breaker Pattern

Modern app have many depandancies which maybe external to the application wach of this may have many components and each maybe using other expernal depandancies

This can increase the chance of your application to suffer from any form of faults either:

- Transient Faults where the application will solve itself in matter of seconds
- Non Transient Faults where the app will suffer for minutes if not hours

Having this component or caller retrying the call to the do operation or to request an api will waste your cloud resources, and waiting for timeout and handling it will waste even more resources, hence the *Circuit Breaker Pattern* come to resolve this problem to shield your application aginst non-transient and [here is how it works](CircuitBreaker/README.md)


## Compensating Transaction Pattern

Large applications will have distrubuted processes or micro services each of this components will be doing some specific job but what if a fault happen in one of this components, then you will have to revert the errorto keep the entire application consistent *Compensating Transaction Pattern* will help you do just that [find out more here](CompensatingTransaction/README.md)


## Health Endpoint Monitoring Pattern

Applications that contains many sub systems require advanced monitoring of the health of this application and its subsystems, this design pattern allow you to have an elegent way to achieve that [more details can be found here](HealthEndpointMonitoring/README.md)

## Queue-based Load Leveling Pattern

When designing applications arround concurrency it is important to distribute the load on your services/processes that the application uses so that the application will stay avalaible and performaned the *Queue-based Load Leveling Pattern* can help a lot by adding an intermediate queue that keep track of the messages sent to be proccesed by the the right application services [find out more on how that works](Queue-basedLoadLeveling/README.md)


## Retry Pattern

Applications often have depandancies that comes in many form could be backend service and API or database, temporal issues may happen due to many factors like for instance temporal network failure this will result in exception temporally but will resolve itself once the network is back but the problem is that the request has already failed this could happen frequently the the application timeout and becomes unstable very quickly the *Retry Pattern* would solve this transient (temporal) errors, [see how that would work](Retry/README.md)

## Throttling Pattern

Unpredictable traffic is always a problem for applications, suppose you have an application that its traffic suddenly increases this means that the application resources will become insufficient if not unavalaible with time, that will result in users having very poor experiance which you want to avoid, luckly the [**Throttling Pattern** will help you avoid that](Throttling/README.md)