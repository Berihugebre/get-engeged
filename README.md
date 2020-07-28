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
    "email":"alumni@gmail.com",
    "password": "123456"
 } 
 ```

#### b. login an Alumni 

 ```POST``` request to ```https://hyf-almuni.herokuapp.com/alumni/login``` with the following input: 

 ```js
  {
    "email":"alumni@gmail.com",
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
 
 ```
 HEADER => Authorization : <the token form the login response > 
 ```
 
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
```
#### D. UPDATE paricular alumni: (```https://hyf-almuni.herokuapp.com/alumni/:alumniId```)

 ```PTTCH``` request to ```https://hyf-almuni.herokuapp.com/alumni/:5f201524c652920017ed9eeb``` with: 
 ```
 HEADER => Authorization : <the token form the login response > 
 ```
 On this request you can edit Alumni's ```name and surname```
 
 #### E. Get all skills of a paricular alumni: (```https://hyf-almuni.herokuapp.com/alumni/:alumniId/skill```)
  ```GET``` request to ```https://hyf-almuni.herokuapp.com/alumni/:5f201524c652920017ed9eeb/skill``` with: 
 ```
 HEADER => Authorization : <the token form the login response > 
 ```
  #### F. Get all language of a paricular alumni: (```https://hyf-almuni.herokuapp.com/alumni/:alumniId/language```)
  ```GET``` request to ```https://hyf-almuni.herokuapp.com/alumni/:5f201524c652920017ed9eeb/language``` with: 
 ```
 HEADER => Authorization : <the token form the login response > 
 ```
  #### G. Get all social media info of a paricular alumni: (```https://hyf-almuni.herokuapp.com/alumni/:alumniId/meida```)
  ```GET``` request to ```https://hyf-almuni.herokuapp.com/alumni/:5f201524c652920017ed9eeb/media``` with: 
 ```
 HEADER => Authorization : <the token form the login response > 
 ```
 In General you can perform the following CRUD actions on t: 
 
 
| METHOD        | ROUTE         | Description  |
| ------------- |:-------------:| -----:|
| POST         | /register      | Register or sign up  alumni |
| POST         | /login         | login alumni |
| GET         | /               | Get all alumni (with COMPANY TOKEN) |
| GET         | /:alumniId      | List a paricular Alumni |
| PATCH         | /:alumniId    | Update a paricular Alumni |
| GET         | /:alumniId/skill | List all programing language skills of a paricuar Alumni |
| GET         | /:alumniId/language | List all language skills of a paricuar Alumni |
| GET         | /:alumniId/media | List all social media details of a paricuar Alumni |

### 2. Skill Main Endpoint: (```https://hyf-almuni.herokuapp.com/skill```)

#### a. createing a new skill for a particular Alumni 

 Note: In every request don't forget to send the Autorizaion token in the header As every route is protected!
 Now let's add a skill for the alumni we created above 
 ```POST``` request to ```https://hyf-almuni.herokuapp.com/skill``` with the following input: 

 ```js
  {
    "student":"5f201524c652920017ed9eeb", // which is the Id of the alumni
    "skill": "javaScript",
    "rate":4
 } 
 ```
 In General CRUD actions on the endpoint (```https://hyf-almuni.herokuapp.com/skill```) are : 
  
| METHOD        | ROUTE         | Description  |
| ------------- |:-------------:| -----:|
| GET         | /               | List all skills  |
| POST         | /               |Create a new skill  |
| GET         | /:skillId      | List a paricular skill |
| PATCH         | /:skillId    | Update a paricular skill |
| DELETE         | /:skillId | Delete a paricular skill |

### 3. Language Main Endpoint: (```https://hyf-almuni.herokuapp.com/language```)

#### a. createing a new language for a particular Alumni 

 Note: In every request don't forget to send the Autorizaion token in the header As every route is protected!
 Now let's add a lnguage for the alumni we created above 
 ```POST``` request to ```https://hyf-almuni.herokuapp.com/language``` with the following input: 

 ```js
  {
    "student":"5f201524c652920017ed9eeb", // which is the Id of the alumni
    "language": "English",
    "rate":5
 } 
 ```
 In General CRUD actions on the endpoint (```https://hyf-almuni.herokuapp.com/language```) are : 
  
| METHOD        | ROUTE         | Description  |
| ------------- |:-------------:| -----:|
| GET         | /               | List all languages  |
| POST         | /               |Create a new language  |
| GET         | /:languageId      | List a paricular language |
| PATCH         | /:languageId    | Update a paricular language |
| DELETE         | /:languageId | Delete a paricular language |

### 4. Social media Main Endpoint: (```https://hyf-almuni.herokuapp.com/media```)

#### a. createing a new social media info for a particular Alumni 

 Note: In every request don't forget to send the Autorizaion token in the header As every route is protected!
 Now let's add a lnguage for the alumni we created above 
 ```POST``` request to ```https://hyf-almuni.herokuapp.com/media``` with the following input: 

 ```js
  {
    "student":"5f201524c652920017ed9eeb", // which is the Id of the alumni
    "media": "github",
    "url":"https://github.com/alumni"
 } 
 ```
 In General CRUD actions on the endpoint (```https://hyf-almuni.herokuapp.com/language```) are : 
  
| METHOD        | ROUTE         | Description  |
| ------------- |:-------------:| -----:|
| GET         | /               | List all sociamedia  |
| POST         | /               |Create a new media  |
| GET         | /:mediaId      | List a paricular media |
| PATCH         | /:mediaId    | Update a paricular media |
| DELETE         | /:mediaId | Delete a paricular media |

### 5. CV Main Endpoint: (```https://hyf-almuni.herokuapp.com/cv```)

#### a. upload a cv for a particular Alumni 

 Note: In every request don't forget to send the Autorizaion token in the header As every route is protected!
 Now let's add a lnguage for the alumni we created above 
 ```POST``` request to ```https://hyf-almuni.herokuapp.com/cv``` with the following input: 

 ```js
  {
    "student":"5f201524c652920017ed9eeb", // which is the Id of the alumni
    "image": alumni.pdf
 } 
 ```
 In General CRUD actions on the endpoint (```https://hyf-almuni.herokuapp.com/cv```) are : 
  
| METHOD        | ROUTE         | Description  |
| ------------- |:-------------:| -----:|
| POST         | /               |upload a new cv  |
| GET         | /:cvId      | List a cv|
| PATCH         | /:cvId    | Update a paricular cv |
| DELETE         | /:cvId | Delete a paricular cv |


### 6. Profile Image Main Endpoint: (```https://hyf-almuni.herokuapp.com/image```)

#### a. upload a an image for a particular Alumni 

 Note: In every request don't forget to send the Autorizaion token in the header As every route is protected!
 Now let's add a lnguage for the alumni we created above 
 ```POST``` request to ```https://hyf-almuni.herokuapp.com/image``` with the following input: 

 ```js
  {
    "student":"5f201524c652920017ed9eeb", // which is the Id of the alumni
    "image": alumni.jpg
 } 
 ```
 In General CRUD actions on the endpoint (```https://hyf-almuni.herokuapp.com/image```) are : 
  
| METHOD        | ROUTE         | Description  |
| ------------- |:-------------:| -----:|
| POST         | /               |upload a new image  |
| GET         | /:cvId      | List an image|
| PATCH         | /:cvId    | Update a paricular image |
| DELETE         | /:cvId | Delete a paricular image |

## 7 . Company main Endpoint: (```https://hyf-almuni.herokuapp.com/company```)

#### a. Registering a company

 ```POST``` request to ```https://hyf-almuni.herokuapp.com/company/register``` with the following input: 

 ```js
  {
    "name":"Marry",
    "surname": "Katherina",
    "companyName": "Twipe Mobile",
    "email":"twipe@gmail.com",
    "password": "123456"
 } 
 ```

#### b. login a Company

 ```POST``` request to ```https://hyf-almuni.herokuapp.com/company/login``` with the following input: 

 ```js
  {
     "email":"twipe@gmail.com",
     "password": "123456"
 } 
 ```
 
  In General CRUD actions on the endpoint (```https://hyf-almuni.herokuapp.com/company```) are : 
  
| METHOD        | ROUTE         | Description  |
| ------------- |:-------------:| -----:|
| POST         | /register      | register a comapny  |
| POST         | / login        | login a company |
| GET          | /:companyId    | List a paricular company |
| PATCH        | /:companyId    | list a paricular company |




