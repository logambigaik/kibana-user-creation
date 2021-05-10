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
'''

#Sample GET method

'''
GET /my-index-000001
{
  "query": {
    "match_all": {}
  }
}
'''
# in ec2-linux command prompt :

![image](https://user-images.githubusercontent.com/54719289/117569875-97fb4100-b0bf-11eb-99e8-6ba8d7b5ad64.png)

![image](https://user-images.githubusercontent.com/54719289/117569906-cc6efd00-b0bf-11eb-9b8b-20b705af8468.png)


