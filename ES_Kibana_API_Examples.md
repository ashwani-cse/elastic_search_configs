## Kibana dashboard Dev Tool Examples
### Create Index
```json
  PUT /product
```

### Insert Data
1. Insert data without providing id
```json
  POST product/_doc
  {
    "title": "Nokia",
    "price": 1500,
    "description": "Nokia yellow",
    "imageUrl": "https://i.pravatar.cc",
    "category": {
      "name": "Phone"
    }
  }
```
- Output: A default id is generated for above product
```json
{
  "_index": "product",
  "_id": "5zSbJI4BRKal20cAk5_a",
  "_version": 1,
  "result": "created",
  "_shards": {
    "total": 2,
    "successful": 1,
    "failed": 0
  },
  "_seq_no": 0,
  "_primary_term": 1
}
```
2. Insert data with id
```json
  POST product/_doc/1
  {
    "title": "Redmi",
    "price": 2500,
    "description": "Redmi yellow",
    "imageUrl": "https://i.pravatar.cc",
    "category": {
      "name": "Phone"
    }
  }
```
- Output:
```json
{
  "_index": "product",
  "_id": "1",
  "_version": 1,
  "result": "created",
  "_shards": {
    "total": 2,
    "successful": 1,
    "failed": 0
  },
  "_seq_no": 2,
  "_primary_term": 1
}
```

### Get Data
1. Get All record from product index
```json
  GET /product/_search
```
- Output:
```json
{
  "took" : 6,
  "timed_out" : false,
  "_shards" : {
    "total" : 1,
    "successful" : 1,
    "skipped" : 0,
    "failed" : 0
  },
  "hits" : {
    "total" : {
      "value" : 2,
      "relation" : "eq"
    },
    "max_score" : 1,
    "hits" : [
      {
        "_index" : "product",
        "_id" : "1",
        "_score" : 1.0,
        "_source" : {
          "title" : "Redmi",
          "price" : 2500,
          "description" : "Redmi yellow",
          "imageUrl" : "https://i.pravatar.cc",
          "category" : {
            "name" : "Phone"
          }
        }
      },
      {
        "_index" : "product",
        "_id" : "5zSbJI4BRKal20cAk5_a",
        "_score" : 1.0,
        "_source" : {
          "title" : "Nokia",
          "price" : 1500,
          "description" : "Nokia yellow",
          "imageUrl" : "https://i.pravatar.cc",
          "category" : {
            "name" : "Phone"
          }
        }
      }
    ]
  }
}
```
2. Get record by id
```json
  GET /product/_doc/1
```

### Update Data
```json
  POST /product/_update/1
{
  "doc": {
    "price": 2000
  }
}
```
- Output:
```json
{
  "_index": "product",
  "_id": "1",
  "_version": 2,
  "result": "updated",
  "_shards": {
    "total": 2,
    "successful": 1,
    "failed": 0
  },
  "_seq_no": 4,
  "_primary_term": 1
}
```

### Delete Data
```json
  DELETE /product/_doc/1
```

### Match queries
1. match query on title
```json
  GET /product/_search
  {
    "query": {
      "match": {
        "title": "nokia"
      }
    }
  }
```
2. Query for Category name
```json
  GET /product/_search
  {
    "query": {
      "match": {
        "category.name": {
          "query": "Phone"
        }
      }
    }
  }
```
### Fuzzy queries
1. Fuzzy query on title
```json
  GET /product/_search
  {
    "query": {
      "fuzzy": {
        "title": {
          "value": "nokya",
          "fuzziness": "AUTO"
        }
      }
    }
  }
```



