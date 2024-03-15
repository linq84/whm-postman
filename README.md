# Using Postman to Access WHM API with Session Token

## Overview

This guide outlines how to use Postman to access the WebHost Manager (WHM) API with a session token for authentication. WHM API allows you to perform server administration tasks, manage cPanel & WHM services, and administer reseller accounts.

## Prerequisites

- Postman installed on your computer ([Download Postman](https://www.postman.com/downloads/))
- Access to a WHM server with appropriate permissions
- WHM API username and password

## Steps

### 1. Set Up Environment in Postman

1. Open Postman and create a new environment.
2. Add variables for the following:
   - `whm_username`: Your WHM API username
   - `whm_password`: Your WHM API password
   - `whm_hostname`: Your WHM server hostname or IP address
   - `session_token`: Variable to store the session token obtained from WHM API

### 2. Create Pre-request Script

1. Open the request where you want to access the WHM API.
2. Go to the "Pre-request Script" tab.
3. Copy and paste the JavaScript code from repo into your pre-request script for the collection
