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

### 1. Alumni 

| Column 1       | Column 2     | Column 3     |
| :------------- | :----------: | -----------: |
|  Cell Contents | More Stuff   | And Again    |
| You Can Also   | Put Pipes In | Like this \| |
