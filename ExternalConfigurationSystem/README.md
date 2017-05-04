# External Configuration System Pattern

Could based applications has many services thatthey depends on they all live in the cloud, hence the application needs to know how to connect or deal with this services, they maybe connection strings or cache settings or search endpoints etc ..., this are often stored in .net applications in the `web.config` and will get deployed within the application, the problem with that started when you have multiple applications it becomes hard to maintain each configuration that may use the same resources for example if the connectiuon string changes every `web.config` will have to be updated, ideally we will want the operation team to take care of any secrets while devs they only care about the application level and all that makes the configuration to be somehow complex however, *External Configuration System Pattern* will help on that

The *External Configuration System Pattern* separates the application from the configuration system and provides configuration as service external to the application

The configuration system contains a store of the configuration along side with a set of logic and strategies to deal with empty or non existing configuration then it exposes this settings as an end point API that will be consumed by multiple application, the configuration system may retrive diffrent settings for diffrent applications, it is also recommended to have an alternative storage like SQL database and a cache layer to enhance the performance as the system is empowering multiple applications

- Configuration system must be always avalaible
- It needs to be performant
- It must be secured and support authentication/authorisation as it store secrets
- It must have a good error handling and strategy for non existing confguration
- It must be flexible
- It must expose Endpoint to get settings by scope, organisation, enviroment
- It must support typed format (Xml,JSON,Key/Value)
- Operations only must have write authorisation access