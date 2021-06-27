# cassdemo
Here are the instructions to setup a simple cassandra cluster of 3 replicas in k8s.
The K8s has 
  - One master node aka **master-node**
  - 2 worker nodes aka **worker01** and **worker02**

![image](https://user-images.githubusercontent.com/24431738/123548239-9413a300-d781-11eb-97bc-6d6e27ec8241.png)


## Login to cassandra instance

- Run the below command to login to the cassandra instance
- 
> kubectl exec -it cassandra-0 bash
![image](https://user-images.githubusercontent.com/24431738/123549200-8b24d080-d785-11eb-802f-8920af66496d.png)


- nodetool status to verify the cluster status
> cassandra-0:/# nodetool status
![image](https://user-images.githubusercontent.com/24431738/123549029-e3a79e00-d784-11eb-930c-b3fcb9af60ab.png)


> type the cqlsh command to initiate the terminal
![image](https://user-images.githubusercontent.com/24431738/123549102-29646680-d785-11eb-857f-6346c39b2daf.png)

## Creating a keyspace

> create keyspace tars_db with replication = {'class':'SimpleStrategy', 'replication_factor':3};
> use tars_db;
> create table planets (name varchar primary key);
![image](https://user-images.githubusercontent.com/24431738/123549390-71d05400-d786-11eb-9a63-ab9080decbe8.png)


