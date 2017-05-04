# Gatekeeper Pattern

The cloud is all about exposing services while this comes with a lot of beneftis it is also insecure and could lead to many attackers trying to compromise this services using either Dos, Sql injections, cross site scripting or many more type of attacks so how wecan take advantages of the cloud and levraging functionality to users while keeping our services secure ? *Gatekeeper Pattern* is the solution to this problem

First step is to minimalise the exposure of this services second part is to implement application gateway that it is the only component that it is exposed to the internet and it is the only way to get to the services that way the gateway provide barrier between services and the outside world.

The getway can then filter and validate any requests comming to this services it also does not know anything about this services so does not hold any connection string or any secrets.

If an attacker tries to compromise it the gateway detect it and reject the request, while if regular users try to use it it will detect that and delegate the request and return the right response back from this services

- Gateway job is only to validate and filter requests
- Gateway should not hold any secrets
- Gateway must be simple and if compromised nothing valuable must be found
- Gateway must be secure avalaible and performant
- Services must have static Name or static IP
- Gateway must have monitoring and alerting systems
