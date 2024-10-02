# RevueCrafters-API-Automation-Testing
This repository contains Postman collections and scripts for automating the testing of the RevueCrafters API. It includes API calls for user authentication and managing revues.

## Table of Contents

1. Project Overview
2. Postman Collection
3. Scripts
4. Tested Endpoints
5. Environment Variables
6. How to Run the Tests
7. Test Results
   
## Project Overview
The RevueCrafters API provides endpoints for managing user authentication and revue operations. This project focuses on automating API testing using Postman collections.

## Postman Collection
- Collection Name: RevueCrafters
- Collection File: RevueCrafters.postman_collection.json
  
The collection contains automated requests for:

- User Authentication
- Creating, Editing, and Deleting Revues
- Fetching Revue Details

## Scripts
The requests are tested using Postman’s built-in JavaScript scripting to validate responses. Some of the key scripts include:


pm.test("Code is 200", function () {
    pm.response.to.have.status(200);
});

const responseData = pm.response.json();
pm.collectionVariables.set("accessToken", responseData.accessToken);

pm.test("Response body has email, password, and accessToken", function() {
    pm.expect(responseData.email).not.to.be.empty;
    pm.expect(responseData.password).not.to.be.empty;
    pm.expect(responseData.accessToken).not.to.be.empty;
});

## Tested Endpoints

POST /api/User/Authentication
Authenticates the user and returns an access token.

POST /api/Revue/Create
Creates a new revue.

GET /api/Revue/List
Lists all available revues.

PUT /api/Revue/Edit
Edits the selected revue.

DELETE /api/Revue/Delete
Deletes the selected revue.

## Environment Variables
The collection uses environment variables to store and reuse values such as base URL and access tokens. Key environment variables:

- baseURL: The base URL of the API
- accessToken: Token obtained from the authentication request
  
## How to Run the Tests
1. Download and import the Postman collection into Postman.
2. Set up the required environment variables (baseURL, accessToken).
3. Run the collection or individual requests.
   
## Test Results
The tests include assertions for:

- Status code (200 for successful requests)
- Presence of important fields in the response body (e.g., email, accessToken)
- Validation of revue creation and deletion.
