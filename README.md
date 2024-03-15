# Using Postman to Access WHM API with Session Token

## Overview

This guide outlines how to use Postman to access the WebHost Manager (WHM) API with a session token for authentication. 
WHM API allows you to perform server administration tasks, manage cPanel & WHM services, and administer reseller accounts.

## Prerequisites

- Postman Online or installed on your computer ([Download Postman](https://www.postman.com/downloads/))
- A collection ready to start programming in Postman
- Access to a WHM server with appropriate reseller permissions

## Steps

### 1. Creating a Service Account and API Key in WHM
You need to use a reseller account with API access. Some documentation calls for root but I think that's overkill.
For Testing and getting used to the API you should give it least priveleges possible. 

#### 1.1 Log in to WHM
1. Open a web browser and navigate to your WHM login page.
2. Enter your WHM username and password, then click "Log in".

#### 1.2 Access Manage API Tokens Interface
1. In WHM, navigate to **Home** > **Development** > **Manage API Tokens**.

#### 1.3 Generate API Token

1. Click on the "Generate Token" button.
2. Enter a description for the API token to identify its purpose.
3. Select the desired privileges for the service account. You can choose from predefined roles or customize the privileges.
4. Click on the "Generate" button to create the API token.

#### 1.4 Note Down API Token

1. After the API token is generated, note down the token value. This is the API key that will be used to authenticate API requests.
2. Save the API key in a secure location. Treat it like a password and avoid sharing it publicly.
### > Ensure that only authorized users have access to the API key.



### 2. Set Up Environment in Postman

1. Open Postman and create a new environment.
2. Add variables for the following:
   - `whm_username`: Your WHM APIs username
   - `whm_password`: Your WHM API password
   - `whm_hostname`: Your WHM server hostname or IP address
   - `session_token`: Variable to store the session token obtained from WHM API

### 3. Create Pre-request Script

1. Open the request where you want to access the WHM API.
2. Go to the "Pre-request Script" tab.
3. Copy and paste the JavaScript code from repo into your pre-request script for the collection

#### Requesting Commands From the Server
Now you are autheticated, request your applist from the server to understand what commands you have at your disposal

### 1. Create a New Request

1. Click on the "New" button in the top left corner to create a new request.
2. Enter a name for your request, such as "Get Server Commands".

### 2. Set Request Type and URL

1. Set the request type to `GET`.
2. In the URL field, enter the following URL:
`https://{{whm_hostname}}:2087/cpsess{{session_token}}/json-api/applist?api.version=1`

> Note: `{{whm_hostname}}` will be replaced with your WHM server's hostname or IP address from the Enviromental Variables and `{{session_token}}` with the session token obtained from the pre-request script.

### 4. Send Request

1. Click on the "Send" button to execute the request.
2. Postman will send the request to WHM API and display the response containing the list of available commands.

## Read The Documentation and Explore the API
Explore and interact with various WHM API endpoints using Postman for server administration tasks and repeat the above process to add the requests in postman
https://api.docs.cpanel.net/whm/introduction/
