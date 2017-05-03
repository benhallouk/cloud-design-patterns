# Throttling Pattern

Unpredictable traffic is always a problem for applications, suppose you have an application that its traffic suddenly increases this means that the application resources will become insufficient if not unavalaible with time, that will result in users having very poor experiance which you want to avoid, luckly the **Throttling Pattern** will help you avoid that by creating a `Throttling layer`

The `Throttling layer` sit between the trafic and the application its main responsability is to monitor the trafic and throttling it to a reasonable amout, usually it is a separated layer but its functionality can also be implemnted as part of the application layer

The `Throttling layer` would have a strategy that act upon when certain user/tennants excced such trafict amount, it can either deny the trafic and send erro code that maybe used to implment the retry pattern or it can filter certain IP addresses or trafic comming from certain client if the sent data lenght exceed some specific size

- Throttling needs to happen very fast
- You need to monitor trafic constantly in details
- Return a specific error details that can be utilise it to do the retry pattern