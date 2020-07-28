# get-engeged

# hyf-almuni-backend
RESTful API created with express and mongoose for the [frontend](https://github.com/oSoc20/hyf-alumni)

## Installation

```bash
git clone https://github.com/oSoc20/hyf-almuni-backend.git.git
cd hyf-almuni-backend
npm install
npm start
```

## Configuration
we use [MongoDB](https://www.mongodb.com) database and [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) in the cloud. So, If you want to configure on cloud, create a mongodb atlas account and create a new file ```.env``` in the main directory and configure as follow:

```js
DB_USER =<dbUser>
DB_NAME =<dbName>
DB_PASSWORD = <dbPassword> 
```

And we use [Cloudinary](https://github.com/oSoc20/hyf-alumni) to store files like CV and profile pictures. Similarly add the following configuration to your ```.env``` file

```js
CLOUD_NAME=<your_cloud_name>
API_KEY=<your_api_key>
API_SECRET=<your_secret_key>
```

## usage

This application is deployed on Heroku with [This](https://hyf-almuni.herokuapp.com) main endpoint. 

Now let's EACH ENDPOINTS

### 1. Alumni Main Endpoint: (```https://hyf-almuni.herokuapp.com/alumni```)

#### a. Registering an Alumni 

 ```POST``` request to ```https://hyf-almuni.herokuapp.com/alumni/register``` with the following input: 

 ```js
  {
    "name":"alumni",
    "surname": "hyf",
    "email":"user@gmail.com",
    "password": "123456"
 } 
 ```

#### b. login an Alumni 

 ```POST``` request to ```https://hyf-almuni.herokuapp.com/alumni/login``` with the following input: 

 ```js
  {
    "email":"user@gmail.com",
    "password": "123456"
 } 
 ```
 
 after login you will get the following response :
 ```js
 {
    "success": true,
    "alumni": {
        "cv": [],
        "profileImage": [],
        "userType": "alumni",
        "isActive": true,
        "jobTitle": "frontend",
        "languages": [],
        "skills": [],
        "media": [],
        "projects": [],
        "_id": "5f201524c652920017ed9eeb",
        "name": "alumni",
        "surname": "hyf",
        "email": "alumni@gmail.com",
        "hash": "47660d50d796fbcdd30005bb389e73e4c7179ea13cc6f83476f51593178ae8e3ab596388e3116457922189a7445d22ff73e752131c41a6416a0212ae7173052b",
        "salt": "22f8bb29c111407c0ae3531528337ffab8bb6d284819a5f0405b063fa9b887e6",
        "registeredDate": "2020-07-28T12:08:04.549Z",
        "__v": 0
    },
    "token": "Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiI1ZjIwMTUyNGM2NTI5MjAwMTdlZDllZWIiLCJpYXQiOjE1OTU5MzgwOTI5MTgsImV4cCI6MTU5NTk0MDY4NDkxOH0.C2S8fcU294ywK_Mwm8vW9Cl0FhQ7l2Ikxyv3wNDYe7934F8FtzzO0mhXAIsizA0Fn3ozqwUCIHhWO3sMX3oCqr5FMURMKsjCt28_xgzBVzooI3XEoKwxQHdCral42rKUwUD11uvLRE3z9S93lFrVnpSTiKk1Vuo9dIsEGv_6c3eH7hfJgnW1d9uD9gfHw90TDh5Nx2L6X0i6xQ25_S_vow04h1slIJr89KSB0KirdN1tYr4oi0nGNoMnMxSKotZgX99rGYNBmsPJo2wRlm3VskqV-VHduz2e0po_W_AzSU57s-su9h40uGI8vdIKZ89ZP4Z--Zx8e1tq-BdBZQPSXa4HB2WiMSQDchXeWRJtJ2U4aJUzCL9w0cnbtI_J4b3qA4UcE5KZdCa_9w-8KtHig8qlUoHjHXQ08BiXtK3RxUZ_7WvCml_BK8yCJAmM1jdhtguFwgr0QYvC7LgaHq6u-U803jldUFq3xKZEQkAKqpAYvMJrau3pBr81s9MtdpzNJj_MXvkEVSWJJbWTWIQR__47i4vyTAJmPz6RRNVA24TPdRa7pM2DvXsnlymEtNykBBw9T4hhkbOkrSVGrUv6d9k14E_QrszWIYOmePLPsCMrH7SWKxpkTK2AXgp9MtTaBPkwBqWZV_u7qKfAtPsj0Vd_OT96EZLP_Z0kTDSy-0o",
    "expiresIn": "30d"
}
```

So you need to store the token in LocalStorage or cookies to access the other routes:


#### C. Get paricular alumni: (```https://hyf-almuni.herokuapp.com/alumni/:alumniId```)

 ```GET``` request to ```https://hyf-almuni.herokuapp.com/alumni/:5f201524c652920017ed9eeb``` with: 
 
 ```header :{
 Authorization : <the token form the login response > 
 }```
 
If you make a sucessfull request with the valid token then you will get the following response : 

```js
{
    "success": true,
    "alumni": {
        "cv": [],
        "profileImage": [],
        "userType": "alumni",
        "isActive": true,
        "jobTitle": "frontend",
        "languages": [],
        "skills": [],
        "media": [],
        "projects": [],
        "_id": "5f201524c652920017ed9eeb",
        "name": "alumni",
        "surname": "hyf",
        "email": "alumni@gmail.com",
        "hash": "47660d50d796fbcdd30005bb389e73e4c7179ea13cc6f83476f51593178ae8e3ab596388e3116457922189a7445d22ff73e752131c41a6416a0212ae7173052b",
        "salt": "22f8bb29c111407c0ae3531528337ffab8bb6d284819a5f0405b063fa9b887e6",
        "registeredDate": "2020-07-28T12:08:04.549Z",
        "__v": 0
    }
}
