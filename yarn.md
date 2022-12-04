# YARN

YARN

is resource manager for hadoop.

* It's a framework to provide **computational resources** for **execution engine**.
  * Here computational resources means -> CPU, Memory, Disk I/O, Network Bandwidth
  * execution engine example - Spark, Map Reduce, Storm, Solr, Tez

Component of YARN, Below are 2 daemon running on cluster.

* Resource Manager - One per Cluster - master service
  * deployed on high availability configuration.&#x20;
* Node Manager - One per data Node - Slave service
  * Node manager is responsible to launching and monitoring container. - Container is linux control groups that limits / isolates the resource usage (CPU, memory, disk I/O, network, etc.) to process.

job is submitted -> **resource manager** -> resource manager finds one node manager and ask to start one **container** -> its first container and called **Application Master** -> Now Application Master takes responsibility of executing job, and behave differently for different executing framework -> (next steps for **Map reduce**) -> Now Application Master will ask Resource Manager for more containers so it can start map and reduce tasks -> Once container are located, Application Master ask Node Manager to launch containers and execute the task -> Task directly report its status to Application Master -> Once all Tasks are completeed, All containers including Application Master perform necessary clean-up and terminate.

**Spark** on YARN
