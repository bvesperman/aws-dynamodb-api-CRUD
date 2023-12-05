# aws-dynamodb-api-CRUD
This is an aws serverless application that implements an API gateway to perform create,read,update,delete operations on a dynamoDB table. The table is the very start of a user managment system. 

user table schema:

| attribute | data type | notes |
|-----------|-----------|-------|
| userName_pk0 | String | primary key , indexed with userName-Index|
| firstName | String | user first name |
| lastName | String | user last name |
| postalCode | Number | user postal code|


## Deployment

The serverless application is intented to be delpoyed with the aws SAM cli. If there is a predefined samconfig.toml, the application will be deployed to the region defined there.

sam deploy --template-file dynamo-api-CRUD.yaml --stack-name dynamo-api

If there is no samconfig.toml, then the application can be deployed in a guided mode. The guided mode will step the user through any details necessary. 

sam deploy --template-file dynamo-api-CRUD.yaml --guided

---

Once deployed the sam cli will output the api key id and the base url to access. You will need to get the actual api key in the API gateway section of your AWS instance after deployment.

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

Here are the urls and example cURL command that use API.

Create:
POST
/v1/user
Body:
```
curl --location 'https://XXXXXXXXXX.execute-api.us-east-1.amazonaws.com/v1/user' \
--header 'Content-Type: application/json' \
--header 'x-api-key: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX' \
--data '{
    "userName":"bvesperman",
    "firstName":"brian",
    "lastName":"vesperman",
    "postalCode":"33333"
}'
```

Read
GET
/v1/user/{username}
```
curl --location 'https://XXXXXXXXXX.execute-api.us-east-1.amazonaws.com/v1/user/bvesperman' \
--header 'x-api-key: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX'
```

Update
PUT
/v1/user/{username}
```
curl --location --request PUT 'https://XXXXXXXXXX.execute-api.us-east-1.amazonaws.com/v1/user/bvesperman' \
--header 'Content-Type: application/json' \
--header 'x-api-key: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX' \
--data '{
    "firstName":"brian",
    "lastName":"vesperman-smith",
    "postalCode":"55555"
}'
```

Delete
DELETE
/v1/user/{username}
```
curl --location --request DELETE 'https://5cexo4w4kk.execute-api.us-east-1.amazonaws.com/v1/user/bvesperman' \
--header 'x-api-key: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX'
```



