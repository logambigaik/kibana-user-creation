# kibana-user-creation
```
 amazon-linux-extras install ansible2
 ansible-palybook -v ansible-elasticserach.yml
 
 cd /usr/share/elasticsearch
./bin/elasticsearch-setup-passwords interactive

 ansible-palybook -v ansible-kibana.yml
 ```

# Index creation of kibana with the help of KQL:

#Sample PUT command:

```

PUT /my-index-000001
{
  "settings": {
    "number_of_shards": 3,
    "number_of_replicas": 2
  }
}
```

#Sample GET method

```
GET /my-index-000001
{
  "query": {
    "match_all": {}
  }
}
```
# in ec2-linux command prompt :

![image](https://user-images.githubusercontent.com/54719289/117569875-97fb4100-b0bf-11eb-99e8-6ba8d7b5ad64.png)

![image](https://user-images.githubusercontent.com/54719289/117569906-cc6efd00-b0bf-11eb-9b8b-20b705af8468.png)


# Commands to automate with ansible:
```
GET /cluster/health
curl -u elastic:test123 http://18.130.54.13:9200/_cluster/health
```

```
PUT /_security/user/jacknich
{
  "password" : "l0ng-r4nd0m-p@ssw0rd",
  "roles" : [ "admin", "other_role1" ],
  "full_name" : "Jack Nicholson",
  "email" : "jacknich@example.com",
  "metadata" : {
    "intelligence" : 7
  }
}

curl -H Content-type:application/json -u elastic:test123 -X PUT http://18.130.54.13:9200/jacknich -d '
{
  "password" : "l0ng-r4nd0m-p@ssw0rd",
  "roles" : [ "admin", "other_role1" ],
  "full_name" : "Jack Nicholson",
  "email" : "jacknich@example.com",
  "metadata" : {
    "intelligence" : 7
  }
'

or 

curl -H Content-type:application/json -u elastic:test123 -X PUT http://18.130.54.13:9200/archu -d '@user.json'

```
