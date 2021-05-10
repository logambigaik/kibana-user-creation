# kibana-user-creation
```
 amazon-linux-extras install ansible2
 ansible-palybook -v ansible-elasticserach.yml
 
 cd /usr/share/elasticsearch
./bin/elasticsearch-setup-passwords interactive

 ansible-palybook -v ansible-kibana.yml
 ```

# Index creation of kibana with the help of KQL:

# Sample PUT command:

```

PUT /my-index-000001
{
  "settings": {
    "number_of_shards": 3,
    "number_of_replicas": 2
  }
}
```

# Sample GET method

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
# Sample USER Creation KQL:
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

# Curl command to create user
curl -H Content-type:application/json -u elastic:test123 -XPUT http://18.130.54.13:9200/_security/user/jacknich -d '
{
  "password" : "l0ng-r4nd0m-p@ssw0rd",
  "roles" : [ "admin", "other_role1" ],
  "full_name" : "Jack Nicholson",
  "email" : "jacknich@example.com",
  "metadata" : {
    "intelligence" : 7
  }
}
'
```
![image](https://user-images.githubusercontent.com/54719289/117687312-9446e780-b1af-11eb-8472-abd0d63128b8.png)

```

# Curl Command with KQL in json file format - for user creation
curl -H Content-type:application/json -u elastic:test123 -X PUT http://18.130.54.13:9200/_security/user/archu -d '@user.json'

```
![image](https://user-images.githubusercontent.com/54719289/117687685-edaf1680-b1af-11eb-9ceb-aaa2030721cb.png)

```

# With ansible for user creation:

usercreation.yml
----------------

---
- hosts: localhost
  tasks:
  - name: user creation
    uri:
         url: http://18.130.54.13:9200/_security/user/{{ user }}
         user: "elastic"
         password: "test123"
         method: PUT
         body: "{{ lookup('file','user.json') }}"
         body_format: json
         return_content: yes
         status_code: 200
         headers:
            Content-Type: "application/json"


user.json:
----------

{
  "password" : "test123",
  "roles" : [ "admin", "other_role1" ],
  "full_name" : "Jack Nicholson",
  "email" : "jacknich@example.com",
  "metadata" : {
    "intelligence" : 7
  }
}


# Command to execute:
----------------------


ansible-playbook -v usercreation.yml --syntax-check
ansible-playbook -v usercreation.yml -e user="ganesh"
```
![image](https://user-images.githubusercontent.com/54719289/117688135-69a95e80-b1b0-11eb-884b-66b50fd18e48.png)

