# Project

This is a simple NodeJS API that I am creating to get more familiar with
making API's with node JS

# Aspects

## Database

For this project I will be using MongoDB and Mongoose

## Libraries

These are the libraries that were used by the project that I am basing
this one off of.

### Environmental

- dotenv

npm install dotenv

This allows you to get information from a .env file.


### Development Related

- morgan

HTTP request logger middleware for node.js

### Server Related


- express
- axios

npm install express  
npm install axios

You can think of Express is being a wharehouse:

```
    app.get('/item/:name', async (req, res) => {
        res.send(await findItemByName(req.params.name));
        })

```

If you want to get an item, for example a `pencil`, from this warehouse,
you can use `axios.js`

```
    axios.get('/item/pencil')

```
**Axios** is used to **send** a web request whereas **express** is used to 
**listen and serve** these web request. 
Axios is an HTTP client. It **creates** requests!

They basically work together (axios -> express -> DB)


- slugify

Slugify a String

- nodemailer

Easy as cake e-mail sending from your Node.js applications


### Security Related

- helmet

Helmet helps secure Express apps by setting HTTP response headers.

- express-mongo-sanitize

This module searches for any keys in objects that begin with a `$` sign or
contain a `.`, from req.body, req.query, or req.params. It can then either:

1. Completely remove these keys and associated data from the object, or
2. Replace the prohibited characters with another allowed character.

- express-rate-limit

Basic IP rate-limiting middleware for Express. Use to limit repeated requests
to public APIs and/or endpoints such as password reset.

- hpp

Express middleware to protect against HTTP Parameter Pollution attacks



### Authentication Related

- bcryptjs

npm install bcryptjs

- cookie-parser

npm install cookie-parser

Parse `Cookie` header and populate `req.cookies` with an object keyed by the 
cookie names. Optionally you may enable signed cookie support by passing a `secret`
string, which assigns `req.secret` so it may be used by other middleware.

- jsonwebtoken

npm install jsonwebtoken

An implementation of JSON Web Tokens.



### Database Related

- mongoose

ORM for MongoDB

- validator

This library validates and sanitizes strings only



### Template Engine

-pug

A clean, whitespace-sensitive template language for writing HTML


# Previous Project

I am using the natours project and the libraries that it uses are out of
date and need to be updated. 

I am going to install them and see if the application is working as it should
and then I will upgrade the packages

## How do you update packages 


If you want to update all the packages

`npm update`

To update an individual package

`npm update package-name`

## How to get the database to work

So you will be running MongoDb from within a docker container

There are somethings you will need to do to get the application to run

0. make sure the connection string is right and it is in the file `config.env`

`DATABASE=mongodb://bluejet:Password@172.18.0.2:27017/natoursdb`

1. Find out what IP Address the docker container with MongoDB is running at?  

`sudo docker container inspect <container_name> | grep IPAddress`

2. Login in to the container and setup a user and password for authentication  
There is normally no authentication on MongoDB setup by default in the container  
I'm sure there is a way to get it to setup authentication from the beginning  
but I'm not sure how right now. 

Connect to the docker container
`sudo docker exec -it <container_name> /bin/bash`

To Login and setup a user with authentication you must do this:

To login to the mongo shell type `mongosh -u "admin" -p`
It will prompt for a password enter the one you set the container up with.

Then once there, select the `admin` database to setup authentication on:

`use admin`

Then add authentication

```
    db.createUser(
        {
            user: "bluejet",
            pwd: "Password",
            roles[
                { role: "userAdminAnyDatabase", db: "admin"},
                { role: "readWriteAnyDatabase", db: "admin"}
                ]
        })
```
This should give you a `{ ok: 1 }` response.

So that just made it to where you can login using the blujet user so  
go ahead a login with the bluejet user...

And then switch to the database that you want to connect to and add data.

`use natoursdb`

then create the user on that database:

`db.createUser({user:"bluejet",pwd:"Password",roles:[{role: "readWrite",db: "natoursdb"}]})`

then you will get a `{ ok: 1 }` response.

logout, then using docker restart the database and then you should be able to  
poulate the data.



Then Log out and see if you can populate the database.


## How to Run your project

To run the project type

`npm run start:dev`



