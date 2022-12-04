# Microservices

**Microservices:**

* An architectural style
* An alternative to traditional monolithic applications
* Decomposition of single system into a suite of small services, each running as independent processed and intercommunicating via open protocols (with all thr benefits/risks this implies.)
* A Microservice is a self contained process, that provide unique business capability.
* It makes system loosely coupled.
* Every Microservice is responsible for its own datamodel and data. If other microservice is also responsible for data model, they can also change the data model, that can force downstream force many microservice to change.
* Microservices usually communicate with other via REST/message queue, is always stateless. Stateless gives microservice to scale effortlessly.
* Within a system, different Microservice can be written using different languages and tools.

Other Definitions

* Developing a single application as a suite of small services, each running in its own process and communicating with lightweight mechanisms,often an HTTP resource API.
* Fine-grained SOA

### Working Definition - Microservices

* Composing a single application using a suite of small services ( rather than a single, monolithic application)
* each running as independent processes (not merely modules/ components within a single executable)
* intercommunicating via open protocols ( like HTTP/REST, or messaging)
* Separately written, deployed, scaled and maintained (potentially in different languages)
* Services encapsulate business capability ( rather than language constructs (classes, packages) as primary way to encapsulate.)
* Services are independently replaceable and upgradable

#### Challenges with Microservices

* Complexity has moved out of the application, but into the operations layer
  * Fallacies of Distribured Computing
* Services may be unaviable
  * Never needed to worry about this in monolith
  * Design for Failure, circuit breakers
  * Much more monitoring needed
* Remote calls more expensive than in-process calls
* Transactions: Must rely on eventual consistency over ACID
* Features span multiple services
* Change management becomes a different challenge
  * need to consider the interaction of services
  * Dependency management / versions
* Refactoring Module Boundaries

> Fallacies of Distributed Computing
>
> * The network is reliable.
> * Latency is Zero
> * Bandwidth is infinite
> * The network is secure
> * Topology doesn't change
> * There is on administrator
> * Transport cost is zero
> * The network is homogeneous

#### How to break a Monolith into Microservices

* Primary consideration : Business functionality
  * Single Responsibility Principle
  * Bounded Context
* Size is not the compelling factor
  * small enough for an individual developer to understand
  * small enough to be built and managed by small team
* Documentaion should be small enough to read and understand

#### Differences with SOA

* SOA address interation between systems
  * Microservices address individual applications
* SOA relies on Orchestration
  * Microsevices rely on Choreography
* SOA relies on smart integration technology, dumb services
  * Microservices rely on smart services, dump integration technology

**Advantages**

* Language Independent
* Fast Iterations
* Small Teams
* Fault Isolation
* Pair well with containers
* Scalable&#x20;





{% hint style="warning" %}
reference : Ken Krueger
{% endhint %}

