# Spark

Tuning Apache Spark

1. Dynamic Executor Allocation
   * Better Resource utilization
   * Good for multi-tenant environment

```
spark.dynamicAllocation.enabled=true
spark.dynamicAllocation.executpeIdleTimeout=2m
spark.dynamicAllocation.minExecutors=1
spark.dynamicAllocation.maxExecutors=2000
```



spark application information can be seen from Spark Context WebUI&#x20;

Client Mode -> first application statrts at port 4040













