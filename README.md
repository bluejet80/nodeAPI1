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


## How to Run your project

To run the project type

`npm run start:dev`



