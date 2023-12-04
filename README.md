# aws-dynamodb-api-CRUD
This is an aws serverless application that implements an API gateway to perform create,read,update,delete operations on a dynamoDB table.

user table schema:

| attribute | data type | notes |
|-----------|-----------|-------|
| userName_pk0 | String | primary key , indexed with userName-Index|
| firstName | String | |
| lastName | String | |
| postalCode | Number | |


## Deployment

sam deploy --template-file dynamo-api-CRUD.yaml --stack-name dynamo-api

or

sam deploy --template-file dynamo-api-CRUD.yaml --guided

```
CloudFormation outputs from deployed stack
----------------------------------------------------------------------------------------------------------------------------------------------------
Outputs                                                                                                                                            
----------------------------------------------------------------------------------------------------------------------------------------------------
Key                 ApiKeyId                                                                                                                       
Description         API Key Id                                                                                                                     
Value               XXXXXXXXXX                                                                                                                     

Key                 ApiRootUrl                                                                                                                     
Description         Root Url of the API                                                                                                            
Value               https://XXXXXXXXXX.execute-api.us-east-1.amazonaws.com/v1                                                                      
----------------------------------------------------------------------------------------------------------------------------------------------------
```

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



## Usage
