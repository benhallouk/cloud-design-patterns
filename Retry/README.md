# Retry Pattern

Applications often have depandancies that comes in many form could be backend service and API or database, temporal issues may happen due to many factors like for instance temporal network failure this will result in exception temporally but will resolve itself once the network is back but the problem is that the request has already failed this could happen frequently the the application timeout and becomes unstable very quickly the *Retry Pattern* would solve this transient (temporal) errors

The pattern simply addreses the issue by retriying the transient failure for number of times, sometimes it can use a heartbeat strategy to retry after an incremental amount of time

- You should only retry transient failures
- Design the retry policy to much the functionality
- Becarfull on chaining retries reaction (to retry a a request that fail and retry another request that failed)
- Log all the retry attempts for further investigations