# aws-dynamodb-api-CRUD
This is an aws serverless application that implements an API gateway to perform create,read,update,delete operations on a dynamoDB table.

user table schema:

| attribute | data type | notes |
|-----------|-----------|-------|
| userName_pk0 | String | primary key , indexed with userName-Index|
| firstName | String | |
| lastName | String | |
| postalCode | Number | |


## API Usage
Create:
POST
/v1/user
Body:

Read
GET
/v1/user/{username}

Update
PUT
/v1/user/{username}

Delete
DELETE
/v1/user/{username}