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

## External Configuration System Pattern

Could based applications has many services thatthey depends on they all live in the cloud, hence the application needs to know how to connect or deal with this services, they maybe connection strings or cache settings or search endpoints etc ..., this are often stored in .net applications in the `web.config` and will get deployed within the application, the problem with that started when you have multiple applications it becomes hard to maintain each configuration that may use the same resources for example if the connectiuon string changes every `web.config` will have to be updated, ideally we will want the operation team to take care of any secrets while devs they only care about the application level and all that makes the configuration to be somehow complex however, 
[*External Configuration System Pattern* will help on that](ExternalConfigurationSystem/README.md)

## Federated Identity Pattern

In secure applications or applications that have some part of it secured users will have to authenticate, but the users can login only if the application knows about thier identity so the application must hold record of all the avalaible users in some sort of storage often as database, this may sounds simple but imagine that an organisation have hundred applications and each application require authentcation so each application would have its own idendity records database and will be very complex to manage, luckly [*Federated Identity Pattern* come to solve this problem](FederatedIdentity/README.md)

## Gatekeeper Pattern

The cloud is all about exposing services while this comes with a lot of beneftis it is also insecure and could lead to many attackers trying to compromise this services using either Dos, Sql injections, cross site scripting or many more type of attacks so how wecan take advantages of the cloud and levraging functionality to users while keeping our services secure ? [*Gatekeeper Pattern* is the solution to this problem](Gatekeeper/README.md)

## Runtime Reconfiguration Pattern

Regular application have thier own configuration that is deployed along side with the application, so changing it often means redeploying the application or at least restart the application so that it can load the new configiuration, [*Runtime Reconfiguration Pattern*](RuntimeReconfiguration/README.md) is all about changing the configuration at runtime with no down time

## Valet Key Pattern

Application that does perform download and upload often uses a DMS service while the application is taking care of the bulk of the work the DMS service maybe used only as storage altough it comes with features that can help the application reduce its load, 
[*Valet Key Pattern*](ValetKey/README.md) is about off loading operations like data transfer operationsto external resources like storage that way the application does not have to deal with download and upload of the data as the storage mechanism does take care of it