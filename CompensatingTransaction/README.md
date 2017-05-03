# Compensating Transaction Pattern 

Large applications will have distrubuted processes or micro services each of this components will be doing some specific job but what if a fault happen in one of this components, then you will have to revert the errorto keep the entire application consistent *Compensating Transaction Pattern* will help you do just that

Lets take this senario, imagine that we have a distributed application process that help users to purchase a domain name you can imagine the proccess in this way:

```
(1) Registred User ---> 
                    (2) Aquire a Domain ----> 
                                    (2) Choose a Plan ----> 
                                                (3) Issue the payment ---->
                                                                (4) Recive confirmation email
```

The process can not be completed if any of this steps fail for example if user is not registred he can not have identity and login to the admin panel to utilise his/her domain, same goes for every step. when a semilar situation happens it is important to revert the state so that the process can work properly in this example it would be important to either retry the missing step or to revert all the other steps so that we do not have a domain that is aquired by a user but can not be used or a payment issued for a service that has not be provided, reverting the steps can be very hard but when using *Compensating Transaction Pattern* this becomes more managable, to implement this pattern you wll need:


- Global shared storage that store the process state
- Create a compensating trsansaction for each step to revert it (example delete user step for register user)
- The compensating transaction will use the store to determine what state/step needs to be reverted
- Some steps can not be reverted automatically so admins needs to be informed


Here is the compensating transaction for our example

```
(1) Delete User ---> 
                    (2) Freeup a Domain ----> 
                                    (2) Delete User/Plan association ----> 
                                                (3) Refund the payment ---->
                                                                (4) Inform Admin
```