
# Federated Identity Pattern

In secure applications or applications that have some part of it secured users will have to authenticate, but the users can login only if the application knows about thier identity so the application must hold record of all the avalaible users in some sort of storage often as database, this may sounds simple but imagine that an organisation have hundred applications and each application require authentcation so each application would have its own idendity records database and will be very complex to manage, luckly *Federated Identity Pattern* come to solve this problem

The Federated Identity Pattern allow the application to delegate the authentication to an external identity managment system that implements password policy and multifactor authentication, the users would request the application if this require authentication the application would redirect the user to the identity managment system, once the user is authenticated the identity provider would redirect the user back to the application along side with access token and any other claims or metadata in the headers, the application then check token and see if it comes from a trusted identity managment system if that's the case the user is authenticated and the application will grant the right permessions to the user depending upon the access token and the claims


- Identity managment system must be external to the application
- Identity managment system must be avalaible performant and secure
- Identity managment system should only provide authentication and not authorization
- Application must implement the authorization using the claims