---
title: "GoDataberus - Database Driver API in Golang"
date: "2017-07-12"
categories: 
  - "database"
  - "golang"
tags: 
  - "api"
  - "driver"
coverImage: "architecture-1.png"
---

[GoDataberus](https://github.com/alknopfler/GoDataberus) is a "Database Driver API" in order to reduce the complexity of the CRUD operations in some common databases. The idea is to use Databerus in order to connect to a external DB (using an available DB driver) using the same API independently of the database

# [](https://github.com/alknopfler/GoDataberus#architecture)Architecture

GoDataberus has been developed in Golang and contains:

- Connection Redis store: Redis to store the database's connection data. It return an uuid to use in the following api calls. The connection data could be a local database, external cloud provider, or whatever.
- GoDataberus go package: API to use the basic CRUD with the common databases. It based on different drivers for the databases and implements the basic functions for these databases.

[![Image of architecture](images/architecture.png)](https://github.com/alknopfler/GoDataberus/blob/master/architecture.png)

# [](https://github.com/alknopfler/GoDataberus#how-to-use-godataberus)How to use GoDataberus

## [](https://github.com/alknopfler/GoDataberus#api-definition)API Definition

| Endpoint | Method | Description |
| :-- | :-- | :-- |
| `/v0/connections/{dbType}` | PUT | Register a new Database connection entry. Return uuid to use in the following calls to this database |
| `/v0/databerus/{dbType}/resources/{uuid}` | PUT | Insert an item in the database associated to the uuid |
| `/v0/databerus/{dbType}/resources/{uuid}/fields/{field}/items/{item}` | GET | Search for an item in the database associated to the uuid |
| `/v0/databerus/{dbType}/resources/{uuid}/fields/{field}/items/{item}` | Delete | Delete an item exists in the database associated to the uuid |

## [](https://github.com/alknopfler/GoDataberus#available-db-backend-connections)Available DB Backend connections

By now, the drivers available are:

- **MongoDB (dbType: mongo)**Example:`'{ "DBconnection": { "Proto":"http", "Ipaddress":"localhost", "Port":"27017", "Name":"Databerus", "Username":"", "Password":"", "Collection":"Test" } }'`
- **ETCD (dbType: etcd)**Example:`{ "DBconnection": { "Proto":"http", "Ipaddress":"localhost", "Port":"2379", "Root":"/project/app/component/" } }`

## [](https://github.com/alknopfler/GoDataberus#register-a-database-backend-connection)Register a Database Backend connection

First of all, you have to register the information to connect to an external database:

```curl
curl --request PUT \
  --url http://localhost:8080/v0/connections/mongo \
  --header 'content-type: application/json' \
  --data '{
    "DBconnection":
        {       "Proto":"http",
                "Ipaddress":"localhost",
                "Port":"27017",
                "Name":"Databerus",
                "Username":"",      
                "Password":"",      
                "Collection":"Test"
        }
    }' 
```

Output:

```shell
"6edaa6e0-454e-11e7-88fa-3c15c2d66294"
```

For instance, we are going to use the driver "mongo" with a local Database, so we use the "mongo" driver, and the connection data to use a local database. It return an uuid that will be use in the next calls in order to use this connection to the database.

## [](https://github.com/alknopfler/GoDataberus#use-the-backend-with-basic-crud-operations)Use the Backend with basic CRUD operations

### [](https://github.com/alknopfler/GoDataberus#insert-item)Insert Item

```curl
curl --request PUT \
  --url http://localhost:8080/v0/databerus/mongo/resources/6edaa6e0-454e-11e7-88fa-3c15c2d66294 \
  --header 'content-type: application/json' \
  --data '{
    "data":
        {
            "foo":"bar",
            "foo2":"bar2",      
            "set":
                    {           
                    "pass1":"password"
                    }
        }
        }'
```

For ETCD should be:

```curl
curl --request PUT \
  --url http://localhost:8080/v0/databerus/etcd/resources/ad7be5ba-46cb-11e7-bfb2-3c15c2d66294 \
  --header 'content-type: application/json' \
  --data '{
    "data":
        {
            "root":"root",
            "key":"key1",
            "value":"value1"
        }
        }'
```

### [](https://github.com/alknopfler/GoDataberus#get-item)Get Item

```curl
curl --request GET \
  --url http://localhost:8080/v0/databerus/mongo/resources/6edaa6e0-454e-11e7-88fa-3c15c2d66294/fields/foo/items/bar \
```

In the case of ETCD:

```curl
curl --request GET \
  --url http://localhost:8080/v0/databerus/etcd/resources/8d1c6082-478d-11e7-9396-3c15c2d66294/fields/root/items/key20 \

```

The output depend on the database query:

```json
[
  {
    "_id": "5931980038136fc848d94b23",
    "foo10": "bar10",
    "foo11": "bar11",
    "set": {
      "pass1": "password"
    }
  }
]
```

In the case of ETCD, for instance, if the key does not exists the output could be:

```json
{
  "error": "100: Key not found (/rootkey20) [25]"
}
```


# Build Dockerfile

```shell
docker build -t $REPO:$VERSION -f Dockerfile .;
```
