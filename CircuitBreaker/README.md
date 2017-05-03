# Circuit Breaker Pattern

Modern app have many depandancies which maybe external to the application wach of this may have many components and each maybe using other expernal depandancies

This can increase the chance of your application to suffer from any form of faults either:

- Transient Faults where the application will solve itself in matter of seconds
- Non Transient Faults where the app will suffer for minutes if not hours

Having this component or caller retrying the call to the do operation or to request an api will waste your cloud resources, and waiting for timeout and handling it will waste even more resources, hence the *Circuit Breaker Pattern* come to resolve this problem to shield your application aginst non-transient and here is how it works

You create an intermediate components lets call it `CircuitBreaker` that set between the `Caller` and the `EndPoint` that act in the folowing way:

- In the stable state `caller` will send request to the `CircuitBreaker` it will be deligated to the `Endpoint` and then the response will be returned all the way back back to the `Caller`  at this point the circuit has `closed` state


- In the faulty state `caller` will send request to the `CircuitBreaker` it will be deligated to the `Endpoint` and when it timeout exception will be returned all the way back back to the `Caller` also the state of the circuit switched from `close` to `open`


- During the recovery state `caller` will send another request to the `CircuitBreaker` it will be deligated to the `Endpoint` and then the response will be returned all the way back back to the `Caller`  at this point the circuit has `half open` state


- Final when the state becomes stable again the `caller` will send a request to the `CircuitBreaker` it will be deligated to the `Endpoint` and then the response will be returned all the way back back to the `Caller`  and the circuit will have `closed` state


This pattern will ensure that no resources are wasted, note that this pattern is often used with the [Retry Pattern](#) and can be implmented in a way that it switch the state based on % of faulty requests or number of failiure or type of errors, the stability also can be detirmined by checking a specific health check endpoint using pub/sub pattern or event emitter pattern, so you can make this pattern as smart as needed

### Things to consider:

`Caller` must know what to do with each exepction thrown by the `CircuitBreaker`

`CircuitBreaker` must be designed in away that it examin failures and changes strategy based on that, it should log this errors and have a manual change state implmentation in case admins want to force it, should be thread safe and support async operations should act as facad of the `Endpoint`