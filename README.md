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
> 
> use tars_db;
> 
> create table planets (name varchar primary key);
![image](https://user-images.githubusercontent.com/24431738/123549390-71d05400-d786-11eb-9a63-ab9080decbe8.png)

>cqlsh> create keyspace tars_db with replication = {'class':'SimpleStrategy', 'replication_factor':3};
>
>cqlsh> use tars_db;
>
>cqlsh:tars_db> create table planets (name varchar primary key);
>
>cqlsh:tars_db> alter table planets add rotation int;
>
>cqlsh:tars_db> alter table planets add gravity varchar;
>
>cqlsh:tars_db> alter table planets add life varchar;
>
>cqlsh:tars_db> alter table courses with comment = ' In search of life near Gargantua '
![image](https://user-images.githubusercontent.com/24431738/123549615-6cbfd480-d787-11eb-8cec-d9bf153304e7.png)

```
create table planets (
name varchar primary key,
rotation int,
gravity varchar, 
life boolean,
) with comment = 'In search of life near Gargantua';
```
![image](https://user-images.githubusercontent.com/24431738/123550017-09cf3d00-d789-11eb-9aa0-0ff4ef43a3f0.png)

- To query
> **SELECT** name, title **FROM** tars_db.planets;
 - To limit the number of results 
> **SELECT** * **FROM** tars_db.planets **LIMIT** 100;

- Inserting contents
> INSERT INTO tars_db.planets (name,rotation,gravity)
> 
> VALUES ('Miller',4,'80x');
> 
![image](https://user-images.githubusercontent.com/24431738/123550389-d55c8080-d78a-11eb-9aae-8745f1460bd7.png)

- Updating tables

``` UPDATE tars_db.planets SET rotation = 20, gravity = '30x'
WHERE name = 'Miller';
```
