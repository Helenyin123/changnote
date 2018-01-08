# Backend Part

## 1. Backend Basics

**Process of entering an url to browser:**

1. query ISP\(Internet service provider\) + DNS\(Domain Name Service\), get the IP address for the domain name
2. send an HTTP request to the IP address
3. server get the request and builds up the right content by pulling data from database, then send a HTTP response to the user
4. browser receive the HTTP response and render the page

#### **Static vs. Dynamic Website**

**Static Website: **runs the same html, css, javascript file every time. It will never be different.

**Dynamic Website: **sites that are compiled on the server side where the server is constructing the webpage before it sends back response. The website is dynamic for different user and timestamp.

#### Generic Web Technology Stack

**Frontend: **HTML, CSS, Javascript

**Backend: **Backend language\(Java, Python, NodeJS\), Framework\(Flask, Spring, Express\), Server\(Tomcat\), Database\(MySQL, MongoDB\)

#### HTTP - Hyper Text Transfer Protocol

**HTTP Request:** There are many HTTP request API, eg. Get, Post, Put, Delete. We can make a HTTP Get request by url, we need a html form to make a HTTP post request.

**HTTP Response: **Response is consists of body and header.** **Body includes main content \(all html, css and javascript files\). Headers contains the metadata about the response. One of header data is status code, a number that represent the status of whole response cycle.

**Server Code Structure:** \(1\) Set up server \(2\) Set up database \(3\) Routes \(4\) Start the server

## 2. The Command Line

**cd**: change to another directory/path  
**ls**: list all the files and directories in current directory  
**touch**: create a new file, it could be any form, for example .java .txt .xls  
**mkdir**: create a new directory  
**rm**: remove a file  
**rmdir/rm - rf**: remove a directory. rm -rf can delete non-empty directory while rmdir can't.

## 3. Node JavaScript

Originally, javascript is used only for browser, which means it can only be used in frontend side.  
NodeJS enable us to write javascript on both frontend side and server side

To enter node, open terminal and enter node. To quit node, enter control+c twice. To run a file with node, just type `node filename.js`to the terminal.

Notice that some functions that is only for browser won't work in node.js, because node.js works in server side, there is no browser on server side. eg. alert\(\), document object model\(DOM\), selector, manipulation.

**REPL:** Read, Evaluate, Print, Loop

#### npm - Node Package Manager

npm is the package manager for javascript. Package is same with libraries, it is code that someone else written that you can add to your own code, like Bootstrap, jQuery, Paper.js, Howler.js. But we can't use `<script>` tag to link them since we don't have html file.

To install a package, type command line `npm install packageName`

To import a package, assign a variable `var name = require("packageName");` in your js file

## 4. Server Side Framework

**Library: **It's a collection of functions\(routines\) or classes. The reason behind is simply code reuse. The routines and classes normally define specific operations in a domain specific area.

**Framework: **It's also external code that you include in you application, framework provides a standard way to build and deploy application. In framework, all the control flow is already there, and there are bunch of predefined white spots that we should fill out with our code. A framework is normally more complex. It defines a skeleton where the application defines its own features to fill out the skeleton. In this way, your code will be called by the framework when appropriately. The benefit is that developers do not need to worry about if a design is good or not, but just about implementing domain specific functions.

**Key Difference between Framework and Library: "**Inversion of control": When you call a method from a library, you are in control. But with a framework, the control is inverted, the framework calls you. It's called the "Hollywood Principle": Don't call us, we call you.

![](https://i.stack.imgur.com/DqCkT.png)

**Heavy weight vs. Light weight framework:** heavy weight framework write most of the code for you, you just need to fill in a few blanks, light weight framework have more blanks and let you fill in your code more often.

#### [Express Framework](https://expressjs.com/)

a minimal and flexible node.js web application framework that provide a robust set of features for web and mobile application.

Install express framework by `npm install express --save`

**Route:** server side code that are responsible for listening and receiving HTTP request and deciding what to send back as a response.

```js
// import and initialize express, save it to a variable
var express = require("express"); // import express
var app = express(); // execute express and initial it to a variable

//Define routes  app.httpMethod("url(route path)", callback function(request, respond){})
app.get("/bye", function(req, res) {
    res.send("Goodbye");
});

// add a listener to the certain Port and Ip address request(start the server)
app.listen(process.env.PORT, process.env.IP, function(){
    console.log("The server has start");
});
```

**package.json**: all npm package contains "package.json", it holds metadata relevant to the project. It give the information to nmp that allows it to identify the project and handle project dependencies. project dependency is the package you need to install before you install this package. It's like a recipes for a meal.

If we create a new package of our own, go to the package folder and type command line `npm init` , the terminal will walk you through to create a new package.json file for this package. And if you install any package using `npm install packageName --save`.The package.json file's package dependency will automatically add the package name and version you installed. so that you don't need to update package.json by yourself.

**"\*" Router Matcher**: it will catch all route path that doesn't exist,  and execute the same callback function, like "page not found", etc. The order of this route function matters, because if you put it before other routes function, then all the page will go to "\*". Because the first route that matches the url request will only be run. So normally, we put it in the end.

```js
app.get("*", function(req, res) {
    res.send("Sorry, page not found... What are you doing with your life?");
})
```

**Route Params:** we don't want to write a function for every different route, instead we want to find a pattern and execute the function to every url that matches that pattern. So we need route parameter to represent that pattern.

```js
// "/speak/:animal" will take all the str after "speak/" as a parameter called animal
// we get the string value from req.params.animal. Then find the corresponding sound for that animal.
app.get("/speak/:animal", function(req, res){
    var animal = req.params.animal.toLowerCase();
    var sounds = {
        pig:"'Oink'", 
        cow:"'Moo'", 
        dog:"'Woof Woof!'"};
    res.send("The " + animal + " says " + sounds[animal]);
});
```

**res.render\("fileName", object\)**: a method used to send back content of a file, the file need to exist in a directory called "views", res will automatically looks for the file in that directory. To pass data to ejs template, we create an object, link all data send in request to its corresponding variable name in ejs template. so that the page will be loaded dynamically.

[**Embedded JavaScript \(ejs\)**](http://ejs.co/)

EJS enable us to have dynamic templates, we can embed some javascript code inside html file, for every line of javascript use`<% %>`to tell the browser, it's a embedded javascript code.

Before using ejs template, install ejs in npm: `npm install ejs --save`

`<%  %>`: it won't display the value returned, it just execute the logic like control flow, loop, if statement

`<%= %>`: it will render the value that is returned by javascript to HTML

`<%- %>`: it will evaluate the value as html code, so if we have \`&lt;%- "&lt;strong&gt;This is HTML Code&lt;/strong&gt;"%&gt; , the text will be bolded when display.

**EJS Control Flow: **you must have `<% %>`  in every line for javascript

```js
// ejs if statement
<% if (name.toLowerCase() == "chang") { %>
<p> Good Choice, Chang is the Best! </p>
<% } else { %>
<p>Bad choice, you should have choose Chang.</p>
<% }%>

// ejs for loop
<% for (var i = 0; i < posts.length; i++) { %>
    <li>
        <%= posts[i].title%>  -  <strong><%=posts[i].author%></strong> 
    </li>
<% } %>
```

**Serving Custom Assets**

The css and javascript file stores in a directory called "public", all webpage's ejs file stores in a directory called "views", the header and footer are stored in a directory under "views" called "partials". To add header and footer, use `<% include partials/finelName %>`.when add css link, don't forget to add "/" before file name, which shows find css file under root directory.

```js
var express = require("express");
var app = express();

// add "public" directory to app, so it will automatically look for public
app.use(express.static("public"));
// set view engine so that we don't need to write "home.ejs" every time. 
app.set("view engine", "ejs");

app.get("/r/:name", function(req, res){
    var name = req.params.name;
    res.render("home", {nameVar: name}); // No need to write "home.ejs"
});
```

```html
<!--in here can't use "/partials/header" because partials is inside views directory-->
<%include partials/header%>  <!--Attach header.ejs-->
<!--can't use "/public/app.css", because express will find public itself-->
<!--very important to have a slash before app.css, which means look for app.css in the root directory, not the same with views directory-->
<link rel="stylesheet" href="/app.css"> 

<h1>This is the home page for <%= nameVar %></h1>
<p> Do you know 5 + 5 = ?  It's <%= 5 + 5 %></p>
<img src="https://timeincsecure-a.akamaihd.net/rtmp_uds/416418724/201705/2262/416418724_5444908038001_5444174709001-vs.jpg?pubId=416418724&videoId=5444174709001">
<%include partials/footer%>   <!--Attach footer.ejs-->
```

**Handle Get Request**

for get request, if we want to get some value from the page, we need to use HTML form and set the action to this url, method as "GET". In the node, extract the data from req.query.

```js
// handle get resuest
app.get("/result", function(req, res){
    var web = "http://www.omdbapi.com/?s=";
    var key = "&apikey=thewdb"
    // for get request extracted from req.query!
    var title = req.query.title;
    var url = web + title + key;
    request(url, function(error, response, body){
        if (!error && response.statusCode == 200) {
            var movies = JSON.parse(body)["Search"];
            res.render("result", {title:title, movies:movies});
        }
    }); 
});
```

```html
<form action="/result" method="GET">
<label>Please enter the movie title: <input type="text" name="title" placeholder="movie name"></label>
<input type="submit">
</form>
```

**Handle Post Request:**

In ejs file, we need to create a form and define the "action" and "method" property, in javascript, we define a new post route, get the data from  req.body, and add it to the dataset, then redirect to original page.

We need to install "body-parser" package. `npm install body-parser --save`

```js
var bodyParser = require("body-parser");
var friends = ["Tony", "Justin", "Miranda", "Fan", "Bob"];

// make app use body parser to make req.body a javascript object
app.use(bodyParser.urlencoded({extended: true}));
app.set("view engine", "ejs");

app.post("/addfriend", function(req, res){
    // extract friend name from req.body
    var newfriend = req.body.newfriend;
    // add it to the list
    friends.push(newfriend);
    // redirect to "/friends" page
    res.redirect("/friends"); 
});

app.get("/friends", function(req, res){
    res.render("friends", {friends:friends});
});
```

```html
<!--Once hit submit, the form value will sent to this url by post http method-->
<form action="/addfriend" method="POST">
    <label>Friend Name:<input type="text" placeholder="name" name="newfriend"></label>
    <button>I made a new friend!</button>
</form>
```

If there are many inputs in the form, when sending data from a form, instead of using `<input type="text" name="title">` we could have `<input type="text" name="blog[title]">`. What this will do, instead of making title available directly from `req.body.title`. It will put it inside of an object, like `req.body.blog.title`. In this way, the form created an object and every input in the object exist in that object. We could obtain that object directly from `req.body.blog`.

```html
<form action="/blogs" method="POST">
    <input type="text" name="blog[title]" placeholder="title">
    <input type="date" name="blog[created]" placeholder="created date">
    <input type="text" name="blog[image]" placeholder="image url">
    <input type="text" name="blog[body]" placeholder="content">
    <button>Submit!</button>
</form>
```

## 5. **API - Application Programming Interface**

It's ways for you to write code that interact with other application services. Web API is api that you interact with through the web \(http request\).

If we make HTTP request by website domain, we will get HTML back. It contains the structure of a page. If we make HTTP request by web API URL, it respond with data, in the format of XML or JSON.

**XML - Extended Markup Language**

Its syntax is similar to HTML, but it doesn't describe structure, it represent data key-value pair. There is no functional tag.

A well formed XML document requires :

* Content must be defined.
* Content must be delimited with a beginning and end tag.
* Content must be properly nested without overlapping or missing. Parents within roots, children within parents. 
* The tags are case-sensitive, the beginning and end tags must match exactly. Tag name can't contain space or start with digit number.
* There should be a root element that wrap every element inside it.

```markdown
<person>
    <name>Travis</name>
    <age>21</age>
    <city>Los Angeles</city>
</person>
```

**JSON - JavaScript Object Notation**

JSON likes exactly like JavaScript Object, but key is also a string.

```js
{
 "person" :{
    "name": "Travis", 
    "age": "21",
    "city": "Los Angeles"        
 } 
}
```

**Request Package: **in order to send http request in a code program, we need to install a package called request `npm install request --save`

**JSON.parse\(string\): **the body we get from request argument is not JSON, it's a string. We need to transfer it to JSON using this method.

```js
var request = require("request");
// request callback function have three arguments: error, response and body
request("https://query.yahooapis.com/v1/public/yql?q=select%20astronomy.sunset%20from%20weather.forecast%20where%20woeid%20in%20(select%20woeid%20from%20geo.places(1)%20where%20text%3D%22maui%2C%20hi%22)&format=json&env=store%3A%2F%2Fdatatables.org%2Falltableswithkeys", 
function(error, response, body){
    if (error) {
        console.log(error);
    } else if (response.statusCode == 200) {
        var parsed = JSON.parse(body); // parse string the JSON
        console.log("Today's sunset time in Hawaii is ");
        console.log(parsed["query"]["results"]["channel"]["astronomy"]["sunset"]);
    }
});
```

## 6. DataBase

database is a collection of information/data. It has an interface for CRUD\(create, read, update, delete\) operations.

**SQL\(Relation\) vs. NoSQL\(Not only SQL\) Database:**

* SQL data schema is fixed. The relation between two entities is represented by  join table. Everything is tabula so it's difficult to add a new column afterwards. We need to define the exact pattern for an entity beforehand, and every entity follows that same pattern. 
* NoSQL data schema is very flexible. It doesn't have tables.The data format is like javascript object in key-value pairs called BSON\(Binary Javascript Object Notation\). A certain key can exist or not exist in an entity. Value can be an object or a list. Things can be nested. 

#### MongoDB

mongoDB is a scalable, high-performance, open source  NoSQL database.

**Mongo Commands:**

* **mongod:** stand for Mongo Demon, it start the mongo process. it will keep running in the background.
* **mongo:** open up the mongo shell which is like javascript console, used to debug and test.
* **help:** give a list of basic features of mongo.
* **showdbs: **show all databases name
* **use database name: **if this database exist, we will use it. If it doesn't exist, we will create a new database called this name. 
* **show collections: **show all exist collections in this database.
* **db.collection.insert\(object\): **insert an object to this collection, if the collection doesn't exist, create a new one.
* **db.collection.find\(object\):** find objects in the collection that have the same property value with input object.
* **db.collection.update\(firstObject, {$set:secondObject}\):** find the object that have same property value with first input object and update its other property value according to the second input object. The rest property will remain unchanged.
* **db.collection.remove\(object\): **remove every object that matches with input object. If we want to only remove a certain number, we can add `.limit(n)` at the end of the command.
* **db.collection.drop\(\): **delete all data in that collection.

**Mongoose**

mongoose provide a schema-based solution to model application data. It's a mongoDB object data mapper\(ODM\) for node.js.

```js
// import mongoose
var mongoose = require("mongoose");
// connect mongoose with mongoDB database, if the database doesn't exist, create one
mongoose.connect("mongodb://localhost/cat_app");
// create a mongoose schema
var catSchema = new mongoose.Schema({
    name: String,
    age: Number,
    temperament: String
});

// Cat is the collection name and catSchema is the schema for this collection
var Cat = mongoose.model("Cat", catSchema);

// create a cat object and add to database
// The callback function is the code that will execute after create operation is done
// err is error message if this operation went wrong 
// cat is the object returned from database, not the variable in express
Cat.create({
    name:"Snow White",
    age: 15,
    temperament: "Bland"
}, function(err, cat){
    if (err) {
        console.log(err);
    } else {
       console.log(cat); 
    }
});

// retriev a cat from the DB
Cat.find({}, function(err, cats){
    if (err) {
        console.log("Oh no, error");
        console.log(err);
    } else {
        console.log("All the cats:");
        console.log(cats);
    }
});
```

#### Data Association

Associations allows us to have multiple collections of data related to each other. Data is related and there are different types of relationships:** one to one, one to many, many to many.** eg. one book have one publisher, one user can have many photos, students can sign up many courses and each course can have many students.

**Embedding Data**

We can add one data schema into the other data schema definition, so that two data are related to each other. Notice that the order of schema definition matters. The added data schema must be defined first. Th example below is a user will have many posts, we want to relate user and post.

```js
//Post Schema
var postSchema = new mongoose.Schema({
    title: String,
    content: String
});
var Post = mongoose.model("Post", postSchema);
// User Schema, postSchema is embeded in userSchema
// postSchema need to be defined before userSchema
var userSchema = new mongoose.Schema({
    name: String,
    email: String,
    posts: [postSchema]
});
var User = mongoose.model("User", userSchema);

// add a new post to user
// User.find() will return an array of find objects
// user.findOne() will return one object
User.findOne({name:"Hermione Granger"}, function(err, user){
    user.posts.push({
        title: "Three Things I really Hate",
        content: "Voldemort. Voldemort. Voldemort"
    });
    // need to save the modified user
    user.save(function(err, user){
      if (err) {
          console.log(err);
      } else {
          console.log(user);
      }
    });
});
```

**Referencing Data**

Instead of adding data schema to another data schema, we could add reference/id of a data to another data schema.

```js
//Post Schema
var postSchema = new mongoose.Schema({
    title: String,
    content: String
});
// return the model
var Post = mongoose.model("Post", postSchema);
// User Schema stores reference
// postSchema need to be defined before userSchema
var userSchema = new mongoose.Schema({
    name: String,
    email: String,
    posts: [{type: mongoose.Schema.Types.ObjectId, ref: "Post"}]
});
var User = mongoose.model("User", userSchema);

// add a new post to the user
Post.create({
    title: "This is another post",
    content: "learn how to reference data"
}, function(err, post){
    User.findOne({email: "bob@gmail.com"}, function(err, user){
        user.posts.push(post);
        // if user.save doesn't work, try user.update
        user.save(function(err, updateUser){
            if (err) {
                console.log(err);
            } else {
                console.log(updateUser);
            }
        });
    });
});
// find all posts for a certain user
User.findOne({email:"bob@gmail.com"}).populate("posts").exec(function(err, user){
    if (err) {
        console.log(err);
    } else {
        console.log(user);
    }
});
```

**module.exports**

To clean up the code and make it more module, we can separate data schema definition with other javascript code. We put all data schema definition files under "models" directory. It will be convenient for code reuse. eg. create a "user.js" file in "models" directory, use `module.exports`to export the schema out. Then require the file in "app.js" file.

```js
var mongoose = require("mongoose");
// User Schema stores reference
// postSchema need to be defined before userSchema
var userSchema = new mongoose.Schema({
    name: String,
    email: String,
    posts: [{type: mongoose.Schema.Types.ObjectId, ref: "Post"}]
});
// return the schema 
module.exports = mongoose.model("User", userSchema);
```

```js
var mongoose = require("mongoose");
mongoose.Promise = global.Promise;
mongoose.connect("mongodb://localhost/demo_1", {useMongoClient: true});
// require data schema
var Post = require("./models/post");
var User = require("./models/user");
```

## 7. RESTful Routes

**REST\(Representational State Transfer\):** a mapping between HTTP method and CRUD.

There are 7 RESTful routes, it's a pattern and a convention to structure your routes :

| Route Name | Path \(URL\) | HTTP Method | Description | Mongoose Method |
| :---: | :---: | :---: | :---: | :---: |
| Index | /dogs | GET | list all dogs in DB | Dogs.find\(\) |
| New | /dogs/new | GET | show new dog form | N/A |
| Create | /dogs | POST | create a new dog and redirect to somewhere | Dogs.create\(\) |
| Show | /dogs/:id | GET | shows info about one dog | Dogs.findById\(\) |
| Edit | /dogs/:id/edit | GET | show edit form for one dog | Dogs.findById\(\) |
| Update | /dogs/:id | PUT | update a dog, then redirect to somewhere | Dogs.findByIdAndUpdate\(\) |
| Destroy | /dogs/:id | DELETE | delete a dog, then redirect to somewhere | Dogs.findByIdAndDelete\(\) |



