# Runtime Reconfiguration Pattern

Regular application have thier own configuration that is deployed along side with the application, so changing it often means redeploying the application or at least restart the application so that it can load the new configiuration, *Runtime Reconfiguration Pattern* is all about changing the configuration at runtime with the minimum downtime if no downtime

The pattern introduce an external configuration system that is not part of the application, the application would use the hosting enviroment to subscribe to change event otherwise it may uses poll mechanism to get changes in regular basis finally the application apply the changes at runtime if the application require restart it should happen with the minimum downtime

- Configuration must be external
- Polling changes must be performant
- Identify what changes require application restart and what would be the impact