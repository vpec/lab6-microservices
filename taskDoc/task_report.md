# Lab 6 - Microservices

## Author

* **Víctor Peñasco** - [vpec](https://github.com/vpec)

## Task report

### Registration server

First, the Eureka registration service is launched.

![Eureka registration service log](images/1_registration_server_log.png)

Euroka dashboard can be accessed on localhost port 1111.

![Eureka registration service dashboard](images/2_registration_server.png)

### Accounts microservice

Second, the accounts service is launched. As you can see, it is automatically registered by the Eureka registration service.

![Accounts service log](images/3_accounts_registered.png)

It can be accessed on localhost port 2222.

![Accounts service](images/4_accounts_2222.png)


### Web server

Third, the web server is launched. As you can see, it is automatically registered by the Eureka registration service.

![Web service log](images/5_web_registered.png)

It can be accessed on localhost port 3333.

![Web service](images/6_web_3333.png)

Now, Eureka dashboard shows both microservices: accounts and web server.

![Updated Eureka dashboard](images/7_eureka_dashboard.png)

### Another accounts microservice

Fourth, a second accounts microservice is launched. As you can see, it is automatically registered by the Eureka registration service.

![Second accounts service log](images/8_accounts2_registered.png)

It can be accessed on localhost port 4444.

![Second accounts service](images/9_accounts_4444.png)

Now, Eureka dashboard shows 1 web server registered and 2 accounts services (one is a replica).

![Updated Eureka dashboard](images/10_eureka_replica_up.png)

### Kill first accounts microservice

The accounts service that was launched in first place is killed. Eureka registers in its logs this issue.

![Kill accounts service log](images/11_accounts_down.png)

If you update Eureka dashboard, you can see that indeed it has updated the instances information.

![Updated Eureka dashboard](images/12_eureka_accounts_down.png)

BUT, when you try to access to accounts information through the web server, the information can still be retrieved because the accounts service in port 4444 has replaced the one in 2222.

![Successful accounts service replacement](images/13_test_web_after.png)

