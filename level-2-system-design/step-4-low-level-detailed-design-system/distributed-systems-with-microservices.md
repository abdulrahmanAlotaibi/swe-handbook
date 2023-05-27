# Distributed Systems with Microservices

## Going to microservices checklist ✅

* Volume: the volume of activities outgrow the current technology stack
* New features: better new technologies for certain new features (Using python for example for a report/analytics microservice)
* Engineering team growth: lines of communication increased, the source code is becoming bigger, the cognitive load of an engineer is increasing which slows down the process of developing and maintaining source code (more on that later)
* Technical debt: debt from previous build decision, now it's becoming difficult to make changes
* Distributed system for distributed team: promoting end-to-end ownership for small set of teams with different responsibilities where each team is responsible for it own development and deployment line (frequent small releases by each team rather than a 1 big deployment release), and they communicate through defined contracts and documentation

## Challenges of microservices that you should consider

* Domain knowledge
* Maintaining contracts
* Distributed system challenges
* Operational challenges
* Observability
* Increase points of failure

## Designing phase 🎨

1. Implement most meaningful separation using bounded context
2. Design functions inside capability
3. Implement service contracts
4. Standardize the development, automate, and deployment processes

## Implementing a microservice

### Communication

![](https://imgr.whimsical.com/object/5pAjAUiuq1VcHUvTJ7tswS)

* #### Asynchronous communication
  * Multiple receivers / Fun-out / Pub-Sub (NATS, Kafka, Kinesis)
  * Single Receiver (using NATS broker or without broker)
    * Point to point (subject-based using NATS for example)
    * HTTP pooling

{% embed url="https://docs.microsoft.com/en-us/azure/architecture/patterns/async-request-reply" %}
how client cope with async microservices ?&#x20;
{% endembed %}

* **Synchronous communication**
  * Single Receiver &#x20;
    * HTTP REST
    * gRPC
  * Multiple Receivers
    * Web-hooks

{% hint style="info" %}
ACID distributed Transactions in microservices : [https://developers.redhat.com/blog/2018/10/01/patterns-for-distributed-transactions-within-a-microservices-architecture](https://developers.redhat.com/blog/2018/10/01/patterns-for-distributed-transactions-within-a-microservices-architecture)
{% endhint %}



### API Gateway

**Use cases**&#x20;

* Authentication and authorization
* Service discovery integration
* Response caching
* Retry policies, circuit breaker, and QoS
* Rate limiting and throttling
* Load balancing
* Logging, tracing, correlation
* Headers, query strings, and claims transformation
* IP allow listing

{% embed url="https://docs.microsoft.com/en-us/dotnet/architecture/microservices/architect-microservice-container-applications/direct-client-to-microservice-communication-versus-the-api-gateway-pattern" %}



## Refs

![](<../../.gitbook/assets/image (12).png>)

![](<../../.gitbook/assets/image (1) (1).png>)

![](<../../.gitbook/assets/image (5).png>)

{% embed url="https://www.youtube.com/watch?ab_channel=MIT6.824:DistributedSystems&list=PLrw6a1wE39_tb2fErI4-WkMbsvGQk9_UB&v=cQP8WApzIQQ" %}
<mark style="background-color:yellow;">This has nothing to do with microservices but the challenges of distributed systems</mark>
{% endembed %}
