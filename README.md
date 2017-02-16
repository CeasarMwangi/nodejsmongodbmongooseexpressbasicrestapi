>git init

>git add .

>git commit -m "first commit"


>git remote add origin https://github.com/CeasarMwangi/nodejsmongodbmongooseexpressbasicrestapi.git


>git push -u origin master




MongoDB
CURL
NodeJS
Express
Mongoose
Robomongo

Bootstrapping ExpressJS
install it globally using -g 

>npm install express-generator -g


create todo-app API with EJS views (instead the default Jade)

>express todo-api -e

install dependencies

>cd todo-api && npm install

run the app on Linux/Mac

>PORT=4000 npm start

run the app on WINDOWS

>SET PORT=4000 & npm start

Start mongodb

>mongod

>mongod.exe


Install mongoose the MongoDB driver for NodeJS.
NB: --save. It will add it to the package.json file

>npm install mongoose --save


Mongoose is used for:
1. validations and 
2. enforcing a schema to keep a consistent structure

DATA TYPES:
String
Boolean
Date
Array
Number
ObjectId
Mixed
Buffer

Using CURL to create a todo

>curl -XPOST http://localhost:3000/todos -d 'name=Master%20Routes&completed=false&note=soon...'


>curl -XGET http://localhost:3000/todos

>curl http://localhost:3000/todos



install nodemon globally

>npm install nodemon -g

Run your web server with nodemon

>nodemon


>curl -XPOST http://localhost:4000/todos -d "name=Master%20Routes&completed=false&note=soon..."

>curl -XGET http://localhost:4000/todos/57a655997d2241695585ecf8


>curl -XPUT http://localhost:4000/todos/57a655997d2241695585ecf8 -d "note=hola"

>>curl -XDELETE http://localhost:4000/todos/57a655997d2241695585ecf8





Default Express 4.0 middlewares

morgan: logger

body-parser: parse the body so you can access parameters in requests in req.body. e.g. req.body.name.

cookie-parser: parse the cookies so you can access parameters in cookies req.cookies. e.g. req.cookies.name.

serve-favicon: exactly that, serve favicon from route /favicon.ico. Should be call on the top before any other routing/middleware takes place to avoids unnecessary parsing.


Other ExpressJS Middlewares

The following middlewares are not added by default, but it’s nice to know they exist at least:

compression: compress all request. e.g. app.use(compression())

session: create sessions. e.g. app.use(session({secret: 'Secr3t'}))

method-override: app.use(methodOverride('_method')) Override methods to the one specified on the _method param. e.g. GET /resource/1?_method=DELETE will become DELETE /resource/1.

response-time: app.use(responseTime()) adds X-Response-Time header to responses.

errorhandler: Aid development, by sending full error stack traces to the client when an error occurs. app.use(errorhandler()). It is good practice to surround it with an if statement to check process.env.NODE_ENV === 'development'.

vhost: Allows you to use different stack of middlewares depending on the request hostname. e.g. app.use(vhost('*.user.local', userapp)) and app.use(vhost('assets-*.example.com', staticapp)) where userapp and staticapp are different express instances with different middlewares.

csurf: Adds a Cross-site request forgery (CSRF) protection by adding a token to responds either via session or cookie-parser middleware. app.use(csrf());

timeout: halt execution if it takes more that a given time. e.g. app.use(timeout('5s'));. However you need to check by yourself under every request with a middleware that checks if (!req.timedout) next();.