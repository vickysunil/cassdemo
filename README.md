# cassdemo
Here are the instructions to setup a simple cassandra cluster of 3 replicas in k8s.
The K8s has 
  - One master node aka **master-node**
  - 2 worker nodes aka **worker01** and **worker02**

![image](https://user-images.githubusercontent.com/24431738/123548239-9413a300-d781-11eb-97bc-6d6e27ec8241.png)


# Login to cassandra instance

> nodetool status to verify the cluster status

![image](https://user-images.githubusercontent.com/24431738/123549029-e3a79e00-d784-11eb-930c-b3fcb9af60ab.png)

> kubectl exec -it cassandra-0 bash

> type the cqlsh command to initiate the terminal

![image](https://user-images.githubusercontent.com/24431738/123549102-29646680-d785-11eb-857f-6346c39b2daf.png)

