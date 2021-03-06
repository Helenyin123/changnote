# Frontend Part

## 1. HTML - Hyper Text Markup Language

**Boilerplate**

sublime text: html + tab

```html
<!DOCTYPE html>
<html>
<head>
    <title></title>
</head>
<body>

</body>
</html>
```

**Header**

**&lt;h1&gt; &lt;h2&gt; &lt;h3&gt; &lt;h4&gt; &lt;h5&gt; &lt;h6&gt;**

**Inline**

&lt;em&gt; or &lt;i&gt;  Italic  
&lt;strong&gt; or &lt;b&gt;  Bold  
&lt;u&gt;  underline

#### List

**1.Ordered List**

```html
<ol>
    <li>point 1</li>
    <li>point 2</li>
    <li>point 3</li>
</ol>
```

**2. UnOrdered List**

```html
    <li>point 1</li>
    <li>point 2</li>
    <li>point 3</li>
</ul>
```

**General Container**

&lt;div&gt;&lt;/div&gt;   block level container

&lt;span&gt;&lt;/span&gt;  inline level container

#### HTML Attributes

Attributes add additional information to tags. It's in key-value pair form like &lt;tag name="content"&gt;&lt;/tag&gt;

name is the name of the attributes, content is the content of the attributes

&lt;a href="linkToGoogle"&gt;Go to Google&lt;/a&gt;  Insert a Link

&lt;img src=""&gt;  Insert an image

#### HTML Table

&lt;table border="1"&gt; &lt;/table&gt; define a table

&lt;thead&gt;&lt;/thead&gt; header of table

&lt;tbody&gt;&lt;/tbody&gt; body of table

&lt;th&gt;&lt;/th&gt; a head for a colume

&lt;tr&gt;&lt;/tr&gt; a single row of the table

&lt;td&gt;&lt;/td&gt; a single cell of the table

```html
<table border="1">
    <thead>
        <tr>
            <th>Name</th>
            <th>Age</th>
            <th>Breed</th>    
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Alice</td>
            <td>3</td>
            <td>Poodle</td>
        </tr>
        <tr>
            <td>Sam</td>
            <td>10</td>
            <td>Alaska</td>
        </tr>
    </tbody>
</table>
```

**compress images:** set the size of image smaller

**multiple cursors in sublime text:** click and press command, you can get multiple cursors

#### HTML Form

**form tags:** &lt;form action="send to this url" method="post"&gt;&lt;/form&gt; create a form. action attributes is the url the form will sent to. method attributes is the http method the form will send as.

**input tags:** &lt;input type="text"/"email"/"password"/"file"/"checkbox" placeholder="Password" name=""&gt;  input tag create interactive controls. The "type" attribute determines the type of input. The "placeholder" is the text that will show in the box.

**button tags:**&lt;button&gt;Submit&lt;/button&gt; and &lt;input type="submit"&gt; will create a submit button

**label tags:** add captions to individual elements in the form, important to make the form accessible. There are two ways to add labels:

```html
<label>Username:<input type="text" placeholder="username" name="username"></label>
<label>Password:<input type="password" placeholder="password" name="password"></label>
```

```html
<label for="username">Username:</label>
<input id="username" type="text" placeholder="username">
<label for="password">Password: </label>
<input id="password" type="password" placeholder="password">
```

**form validation:** "required" attribute validate that am input isn't empty

**radio box:** you can only choose one radio box under the same name

```html
<h1>Are you a boy or a girl?</h1>
<label for="girls">Girls:</label>
<input id="girls" type="radio" name="gender" value="girls">
<label for="boys">Boys: </label>
<input id="boys" type="radio" name=gender value="boys">
```

**select box:** you can have a scroll down select box

```html
<h1>Which color is your favorite?</h1>
<select name="color">
    <option value="yellow">Yellow</option>
    <option value="orange">Orange</option>
    <option value="red">Red</option>
</select>
```

**text area:** you can type in text within this region, "rows" and "cols" attributes set the size of the text area.

```html
<h1>Do you have any comments?</h1>
<textarea name="comments" rows="10" cols="50"></textarea>
```

**Canvas: **&lt;canvas&gt; element can be used to draw graphics via scripting in JavaScript, it can be used to draw graphs, create animations or video processing or rendering. In HTML, canvas just exist, it doesn't do anything. In JavaScript, we will shape it.

`<canvas id="canvas"></canvas>`

## 2. CSS - Cascading Style Sheet

**General Rule**

```css
selector {
    property:value;
}
```

**Connect CSS and HTML file **

Inline and style tag method are not very good method to add css to html. Inline will need to change every elements in the html even if they are in  the same style, it will be a very heavy work if the page is very large. The problem of style tag is that we want to separate css with html, we don't want css nested in html.

we want to add a link tag in html head tag \(sublime: link + tab\)

```html
<head>
    <title>Demo</title>
    <link rel="stylesheet" type="text/css" href="filename.css">
</head>
```

**Color in CSS**

1.Hexadecimal: \# + 6 hexadecimal numbers\(0-F\)

6 hexadecimal numbers = RGB\(256, 256, 256\) \(Red + Green + Blue\)  `color:#FF0401;`

1. RGB: 3channels: Red, Green, Blue, each range from 0-255

`color:rgb(0,255,0);`

1. RGBA : like RGB, but with an alpha\(transparent\) channel, range from 0.0-1.0\(0.0 means total transparent\)

`color:rgba(11, 99, 150, 0.6)`

**Background**

we use color to set text color and use background to set background color. background could also set as an image.

```css
body {
    background: url(http://anguerde.com/pics/main/56/406435-wooden-wallpaper.jpg);
    background-repeat: no-repeat;
    background-size: cover;
}
```

**Border**

border setting consists of three parts: color, width, style

```css
h1 {
    border: 2px dashed rgb(255,0,0);
}
OR
h1 {
    border-color: purple;
    border-width: 1px;
    border-style: solid/dashed;
}
```

#### Selector

**1.Element/ Type Selector**

```css
li {}  h1 {}  p{}
```

**2. ID - an unique id can only appear once in html page**

```css
#name{} #id{} #special{}
```

**3. Class - a class can be used many times**

```css
.completed{} .done{}
```

**4.** **Star - select every element in the page**

```css
*{}
```

**5. Descendant Selector -  the second element must nested in the first element**

```css
li a {} /*select all the <a> inside of <li>*/
p div {} /*select all <div> inside of <p>*/
```

**6. Adjacent Selector - the second element is next to the first element**

```css
h1 + h2 {} /*select all h2 that is adjacent to h1*/
```

**7. Attribute Selector - select all elements based on that attribute**

```css
tag[attribute="content"] {} /*select all tags with that attribute="content"*/
a[href="http://www.google.com"] {} /*select all <a> with href="http://www.google.com"*/
input[type="text"] {} /*select all <input> with type="text"*/
```

**8. nth of type - select the nth element of that type**

```css
ul:nth-of-type(3) {} /*select the 3rd ul*/
```

**9. Special Selectors**

```css
h1:hover {} /*change the style of h1 when mouse hover on it*/
h1:first-letter {} /*change the style of first letter of h1*/
a:visited{} /*change the style of a link if it's visited*/
input:checked{} /*change the style of a checkbox if it's checked*/
```

**Inheritance: **Children will inherit the css style of its parent.

**Specificity: **if there are more than one style targeting an element,  whichever selector that is more specific will win. To know which selector wins, we can use css specificity calculator.

Type selector &lt; class selector/attribute selector &lt; ID selector

#### Font

**1.font family**

font family property specifies a font name from the font family for the selected element. If font name have digit at the beginning, you must add double quotes to the font

```css
p {font-family: Arial} 
h1 {font-family: "1sansif"}
```

**2. font size**

one method to set font size is specifies the pixels of the font size. The other is using "em" values, it is relatively font size means dynamic. it will automatically adapts its length relative to the font that the reader choose to use. It might cause compounding problem. Another value is "rem", it is relative to the root html element\(default setting or personal setting\), not parent element. It let you specify a font size in a relative fashion without being affected by the size of the parent, thereby eliminating compounding problem.

em = desired element pixel value / parent element font-size in pixels

rem = desired element pixel value / root element font-size in pixels

```css
body {font-size: 10px;}
p {font-size：2em;} /*value 2 is a multiplier of the current em size*/
div {font-size: 0.65rem} /*font size is 0.65 * body font size*/
```

**3. font weight**

font-weight specifies the boldness of the font. The values of this property are normal, bold, bolder, lighter, 100, 200, 300, ... , 800, 900.

**4. line height**

line height specifies the amount of space between lines. The value of this property are normal, 3.5, 3em, 50%

**5. text align**

text align specifies how the text is aligned. The value are right, center, left

**6. text decoration**

text decoration gives underline or line through or overline effect

#### **The Box Model**

In a document, each element is represented as a rectangular box. In CSS, each of this rectangular boxes is described using box model. Each box has four edges: the margin edge, border edge, padding edge and content edge.

![](https://www.codeproject.com/KB/HTML/567385/boxmodel-image.png)

**Content, Padding\(space between content and border\), Border, Margin\(space outside of border\)**

```css
p {
    /*content*/
    width: 100px;
    width: 50% /*50% of its parent element, if the window size change, the width of p will also change.*/ 
    height: 100px;
    /*padding*/
    padding: 100px;
    padding-top: 20px;
    padding-bottom : 30px;
    /*border*/
    border: 1px purple solid
    border-left: 1px black solid
    border-right: 2px orange dashed
    /*margin*/
    margin: 20px, 40px, 400px, 100px; /*top, right, bottom, left*/
    margin: 0 auto; /*top, right and repeat on bottom, left*/
    /*auto means that the value of that property is adjusted automatically according to the content*/
    margin-top: 20px; 
    }
```

#### Notice:

a percentage value for `height` doesn’t work but a percentage value for `width` does.

In CSS an element's padding will be calculated by it's parent element's width if the padding is set using percent instead of pixels.

To center text, use `text-align: center`. To center box model, use `margin: 0 auto` + define width of the container.

`border-radius: 15%` can make the border have round effect

`transition: background 0.3s` will have fade out effect whenever the background is changed

## 3. Bootstrap

Bootstrap is the most popular HTML, CSS and JS framework for designing website. You can download it and link to the file locally, or use CDN\(Content Distributed Network\)support, which is an online server for bootstrap, you just need to add a link to the html header.

**Button, Jumbotron, **

**Navigation Bar**

Sample code for navigation bar, before use collapse button, add bootstrap javascript cdn and jQuery cdn link to the head.

```html
<nav class="navbar navbar-default navbar-fixed-top">
    <div class="container">
        <div class="navbar-header">
            <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#bs-navbar-collapse" aria-expanded="false">
                <span class="sr-only">Toggle navigation</span>
                <span class="icon-bar"></span>
                <span class="icon-bar"></span>
                <span class="icon-bar"></span>
            </button>
            <div class="navbar-brand"><i class="fa fa-picture-o" aria-hidden="true"> IMGS</i></div>
        </div>
        <div class="collapse navbar-collapse" id="bs-navbar-collapse">
            <ul class="nav navbar-nav">
                <li><a href="#">About</a></li>
                <li><a href="#">Contact</a></li>
            </ul>
            <ul class="nav navbar-nav navbar-right">
                <li><a href="#">Sign Up</a></li>
                <li><a href="#">Login</a></li>
            </ul>
        </div>
    </div>
</nav>
```

**Form**

classes to make the form organized. _**".form-group"** \_add some spacing between each group of elements. _**".form-control" **_add focus effect, padding, border to the input tag. _**".form-inline"**\_ wrap the entire form in one line.

#### **Grid System**

Use grid to build layout by 12 column system.

**Container: **container provide a means to center and horizontally pad site's content**.**

**Rows: **wrappers for columns. Each column has horizontal padding for controlling the space between them. This padding is counteracted on the rows with negative margins.

**Columns:** content must be placed within columns and only columns may be immediate children of rows. Columns without a specified width will automatically layout as equal width columns. Column width are set in percentages, so they're dynamic and sized relative to their parent element.

**Four Different Sizes: **Extra Small\(Phone\)         Small\(Tablet\)         Medium\(Desktop\)      Large\(Desktop\)

## 4. JavaScript

Link HTML and JavaScript file: use &lt;script src="url"&gt;&lt;/script&gt; tag, in sublime do script + tab

```html
<head>    
    <title>Demo</title>
    <script src="app.js"></script>
</head>
```

#### Primitive Type

There are five primitive types: Numbers, Strings, Boolean, Null, Undefined.

**find console in chrome: **chrome -view- javascript console

**Numbers:** numbers include all kinds of form, eg. positive number, negative number, integer, float number

**String:** both single or double quote is ok for string. When there is a single quote in the string, we must use double quote, like `"I can't stop imagine".`

When we want to use double quote inside a string, use escape character "\" `"I know \"king of mine\" means" = "I know "king of mine" means".` When we want to use backslash, do `backslash \\" = backslash \`

**Boolean: **true and false. Value aren't actually true or false, are still inherently "truthy" or "falsey" when evaluated in a boolean context. Falsy value: false, 0, "", null, undefined, NaN.

```js
!!"" // false
!!NaN // false
!!"false" //true
!!-1 //true
// Falsy value: false, 0, "", null, undefined, NaN
//  everything else is truthy
```

**Comparison Operators:  **"==" equal to value, "!=" not equal to value, "===" equal value and type, "!==" not equal value or equal type.

"==" performs type coercion, while "=== does not."

```js
var a = 5; var b = "5"
a == b; // true
a != b; // false
a === b;  //False
a !== b; // true

var y = null;
y == undefined; //true
y === undefined; //false

true == "1"; //true
true == "12"; //false
false == "0"; //true
null == undefined; //true
NaN == NaN //false
// NaN: not a number
```

**Variable: **A container that stores different value, define a variable: `var name = value;`

In Javascript, variable name follows **camel case:** the first name is lowercase, next word be uppercase. eg. camelCase.

**snake case:** words are separated by \__. eg. \_snake_\_\_case

**kebab case:** words are separated by -. eg. kebab-case

**Dynamic Typing:** variable can change from one type to another.

```js
var name = 80;
name = "Sally"
name = "80" - 10 = "70"
```

**Cast Type:** If we want to convert a string to number, we can use Number\("80"\) to cast the type, or String\(90\), Boolean\("Helllo"\)

**Null: **explicitly nothing or empty

**Undefined: **Variables that are declared, but not initialized. If a variable is not declared at all, the system will throw an error message, not undefined value.

```js
var currentPlayer = "charlie";
currentPlayer = null;

//undefined
var name;
var age;

//throw reference error
color
```

#### Built in Methods

**alert\(content\): **pops up a message to alert user

**prompt\(content\): **get input from user

**console.log\(content\):** print something to javascript console

**clear\(\): **clear the javascript console

**typeof\(varName\):** return the type of this variable in string form

```js
alert("You can't open this page");
alert(900 * 40);
console.log("This can only show in console");
var username = prompt("what is your username?");
clear();
typeof(70); //"number"
typeof("false"); // "string"
```

#### Functions

functions are building blocks of JavaScript. It lets us wrap up code segment into reusable package.

```js
function playMusic() {
}
// playMusic means pass a function as a reference, but not execute it
// playMusic() means execute the function immediately
```

**Declaration & Expression**

The difference between declaration and expression is that if we use expression, once we reassign the variable name to another type, the function will be lost.

```js
// function declaration
function name(argument1, argument2) {
    return result;
}
// function expression, once assign the var name to another type, the function will be lost.
var name = function(argument1, argument2) {
    return result;
}
// Anonymous Function
function(argument1, argument2) {
    return result;
}
```

**Scope: **context that code is executed in. When we define a function, we had a new scope for that function. Child scope have access to variables in parent scope, but parent scope don't have access to child scope.

```js
var a = 4; var b = 9;
function doMath() {
    a = 5; 
    var b = 12;
    return a * a;
}
doMath(); // return 25
x; // return 5
y;// return 9
function doOther() {
    var y = 7;
    return 2 * y + 10; 
}
doOther(); // return 24
y; // throw error message
```

**Higher Order Function: **functions that are either pass a function as an argument or return a function

**Array: **group data in consecutive memory, we can retrieve, update, or add them by index. For empty space, the default value is undefined. If you access an index that is out of bound, it will return undefined. Array can hold any type of data.

```js
// Define an array
var array = [];
var array = new Array();
var friends = ["Charlie", false, null, 70];
friend.length; // return 4
```

**push/pop: **append or remove element to the end of the array

**unshift/shift**: add or remove element to the start of the array

**indexOf\(element\):** return the first index of that element in the array, if not exist, return -1.

**slice\(start index, end index\):** deep copy a part of the array, the original array won't be changed

**splice\(start index, number of element to be remove\): **remove element from array given index and range

**forEach\(function\): **iterate over the array. forEach\(\) takes in a callback function, it execute for each element in array. It has three argument: the element value, element index, the array being traversed. The syntax is like array.forEach\(function\(element, index, array\)\);

```js
var colors = ["Green", "Red", "Yellow", "Blue"];
colors.forEach(function(color, i){ // input is an anonymous function
    console.log(i + "th color is " + color); // color is a placeholder for element value, i is the index 
});
```

#### Object

Object store data in key-value pairs. Object can hold all sorts of data, eg. number, string, boolean, array, or object.

```js
// create a new object
var person = {}
var person = new Object();
var person = {name: "Travis", age: 21, city: "LA" }

// add element
person.age = 6;


// retrieve data using bracket or dot notation
person["name"];
person.name; 

// you can't use dot notation if the property name start with number or name with space
person.1house //Invalid
person.house wife //Invalid
person["1house"] // valid
person["house wife"] // valid

// you can't use dot notation for a variable
var str = "age";
person.str // Invalid, won't look for "age"
person[str] // valid, will look for "age"
```

**Methods: **we can add methods to object, it's like a a property of an object that is a function. We can customize the same method for different object. Same as polymorphism in java.

```js
var person = {name = "chunk" add: function(x, y) {return x + y;}};
person.add(30, 7); // return 37

// customize method for different object, avoid namespace collision
var cats = {speak: function(){return "MEOW!"}};
var dogs = {speak: function(){return "WOOF!"}};
cats.speak();
dogs.speak();
```

**"This" Keyword:** In an object, if we want to add a method and use the data of the object, we use "this" to represent this object.

```js
var movie = {title: "Titanic", comments: ["So Great", "Don't like it", "Excellent"]};
movie.printComments = function() {
    for (var i = 0; i < this.comments.length; i++) {
        console.log(this.comments[i]);
    }
}
movie.printComments();
```

## 5. DOM - Document Object Model

The DOM is the interface between Javascript and HTML + CSS. It all starts with the root node - document object. The process is that we first select an element, then manipulate it.

#### DOM Selector

The document object have many method to select element. The selector will return a javascript object.

* **document.getElementById\(\) : **take a string argument as ID and return the one element with a matching ID.
* **document.getElementsByClassName\(\): **take a string argument as class name and return a node list of elements with a matching class. The node list is not an array, can't use forEach function to iterate.
* **document.getElementsByTagName\(\): **take a string argument as tag name, and return a node list of elements with a matching tag.
* **document.querySelector\(\):** take a string argument as CSS-style selector, and return the first element that matches the selector. eg. "\#ID", ".class", ''tag", "li a"
* **document.querySelectorAll\(\): **take a string argument as CSS-style selector, and return a list of all elements that matches the selector

#### Manipulation

**Style Property**: it's one way to manipulate an element. The style property allows for quick styling, eg testing. It's recommended for styles to be defined in a separate file. There is a concept of "separation of concerns", which includes three parts: structure\(HTML\), presentation\(CSS\), behavior\(Javascript\) to be separated.

classList is a read only list that contains the classes for a given element. It's not an array.We use add, remove, toggle to update it.

```js
// create a new CSS class
.highlight {
    color: red;
    border: 1px solid orange;
}

// select an element
var h1 = document.querySelector("h1");

// manipulate method 1
// add a class to that element classList
h1.classList.add("highlight");
// remove a class to that element classList
h1.classList.remove("highlight");
// if the class exist in classList, toggle will remove it from classList. 
// If it doesn't exist, toggle will add it to classList.
h1.classList.toggle("highlight");

// manipulate method 2
h1.style.color = "red";
h1.style.border = "1px solid orange";
```

**Text and Content: **there are two methods to change text and content

* **element.textContent: **return an extract** **pure text without html tags inside that element as string.
* **element.innerHTML:** return the html inside that element as string.

```js
var h1 = document.querySelector("h1");
// notice there is no ()
h1.textContent = "You are the best";
h1.innerHTML = "<em>You<em> are the <strong>best</strong>";
```

**Attributes:** there are two methods to read and write attributes.

* **element.getAttribute\("attribute"\): **get the value of given attribute in the element.
* **element.setAttribute\("attribute", "content"\): **set the value of given attribute in the element.

```js
//<a href="www.google.com">Link</a>
var link = document.querySelector("a");
link.getAttribute("href"); // "www.google.com"
link.setAttribute("href", "www.dogs.com");
```

#### DOM Events

Events are everywhere, like click the mouse, press the keyboard, hover over a link, drag and drop. The process is that first select an element, then add an event listener. An element can have several event listeners.

**element.addEventListener\(type, function\): **Given the type of event we want to listen and function to execute when the event happen, we add an event listener to that element.

**element.removeEventListener\(type, function\): **remove the event listener of certain type and function from element.

```js
var button = document.querySelector("button");
button.addEventListener("click", clicked);
button.removeEventListener("click",clicked);
function clicked(){console.log("Button has been clicked!")};
```

[**Event Types**](https://developer.mozilla.org/en-US/docs/Web/Events)**: **

* **"click": **fires when an element is clicked by user.** **
* **"change": **when a change to the element value is committed by the user. eg. &lt;input&gt; &lt;select&gt; &lt;textarea&gt;. The difference between "change" and "input" event is change event is not necessarily fired for each change to an element's value.
* **"input": **when a change to the element value is changed. eg. &lt;input&gt;&lt;select&gt;&lt;textarea&gt;. This event fires more often.
* **"mouseover": **fires when the mouse hover over this element.
* **"mouseout": **fires when the mouse hover out this element

## 6. jQuery

jQuery is a javascript library, or DOM manipulation library. It have many useful methods like: select elements, manipulate elements, create elements, add event listener, animate elements, add effects, make http requests\(AJAX\), etc.

The reason why we use jQuery is: \(1\) Fixes "broken" DOM API \(2\) Brevity and Clarity \(3\) Cross browser support \(4\) AJAX.

To add jQuery to HTML and CSS, use a `<script>` tag to link CDN or local file to html header.

**jQuery Selector:**`$("CSS-style selector")` will return a list of all the elements that matches the css-style selector.  it's similar to document.querySelectorAll\(\).

`$("selector:first")` or `$(selector).first()`: select the first element that matches the selector

`$(selector).last()`: select the last element in the list

#### Manipulation:

A big difference is that we can manipulate using jQuery methods to a collection of elements without for loop. It automatically apply the method to all selected elements. Secondly, each method in jQuery is both a getter and a setter, so be careful about distinguish which function does it use.

**Style Property: **`$("selector").css("property", "value")`.css\(\) method is jQuery's interface to styling. You can either add an object in CSS\(\) too. The style will effect on every element selected in the list, we don't need to write a for loop.

* **addClass\("class1 class2"\): **add the specific class or classes to the list of matched elements
* **removeClass\("className"\): **remove the specific class or classes to the list of matched elements
* **toggleClass\("className"\): **add the class if not exist or remove the class if existed in the matched elements

```js
// get the value of width of img
var width = $("img").css("width");

// change all <a> 's background color to blue
$("a").css("backgroundColor", "blue"); 
// change all element in class "selected" to these styles
$(".selected").css({border: "1px solid blue", color: "purple"});
```

**Text and Content:**

* **text\("new text"\):** get or set the combined text \(a single string\) content of each element in the list of matched elements, including their descendant. It's similar to `element.textContent`
* **html\("new html"\): **get the html contents of the first element in the list of matched elements, or set the html contents of every matched element. It's similar to `element.innerHTML`

```js
// get the text content of body
var body = $(body).text();

// set the text of all list to "You are the best"
$("li").text("You are the best");
$("h1").html("<strong>Nobody</strong> can destroy <em>you<em>");
```

**Attribute and Value: **

* **attr\("attribute name", "new value"\): **get the value of an attribute for the first element in the list of matched elements, or set one or more attributes for every matched element. It's similar to `element.getAttribute()` and `element.setAttribute()`

```js
// get the link address of the first <a> 
var link = $("a").attr("href");

// set the type of input to button
$("input").attr("type", "button");
$("input").attr({type: "text", placeholder:"your name"});
```

* **val\("new value"\): **get the value of the first element in the list of matched element, or set the value of every matched element. it's like a wrapper for value, text\(\) is a wrapper for text content. It's similar to `element.value`

```js
// get the value of text input
$("input:text").val()
$("select").val // get the value of a dropdown menu

// set the value of number input
$("input:number").val("4")
```

**"This" keyword:** in jQuery, this is written as `$(this)`

#### jQuery Event

**click\(function\): **add a click listener to element.

**keydown/keypress/keyup\(function\): **function will be triggered** **when the key is pressed down/between key down and key up/when the key is relieved, it's used to add a key listener to element. keyup\(\) and keydown\(\) provide a code indicating which key is pressed. While keypress indicates which character was entered, like a lowercase 'a' will be reported as 65 by keydown and keyup, but as 97 by keypress. an uppercase 'A' = keypress shift + 'a' will be reported as 65 by all events. Every key have its own keycode. we can search which key was pressed by event.which.

```js
// The console will show "You hit enter" every time you press enter key 
// the first argument of keypress callback function is an event object 
$(input).keypress(function(event) {
    if (event.which === 13) {
        console.log("You hit enter");
    }
});
```

**on\(type, function\): **let you specify the type of event to listen for, similar to addEventListener\(\).

**Difference between click\(\) and on\("click"\):** click\(\) will only add listener for existing element, on\("click"\) will add listener for all potential future elements. Usually, we use on\("click"\) rather than click\(\) to make all potential elements to add listeners.

```js
$("button").on("click", function(){
    console.log("button clicked!");
});
```

**Some Events:** "mouseenter", "mouseleave", "dbclick"\(double click\),

#### jQuery Effect

* **fadeOut\(duration, function\):** hide the matched elements by fading them to transparent. It can fade in the duration time period and also execute a function when the animation complete.
* **fadeIn\(duration, function\): **we can first set some element's style as "display: none", then fade it in to the page.
* **fadeToggle\(duration, function\): **if the element is on display currently, fade it out. else if it's not on display, fade it in.

```js
// all div will fade out when button is clicked, the animation will last 1s
// after the animation is completed, remove all div
$(button).on("click", function() {
    $("div").fadeOut(1000, function(){
        $(this).remove() ;
    });
});
```

* **slideDown\(\): **animated the height of an element, display the matched elements with a sliding down motion
* **slideUp\(\): **hide** **the matched elements with a sliding up motion.
* **slideToggle\(\): **if the element is on display, hide it, else if the element is not on display, show it.

[**Paper JavaScript**](http://paperjs.org/tutorials/)

It's an open source vector graphics scripting framework that runs on top of HTML canvas. It offers a clean document object model and a powerful functionality to create and work with vector graphics.

[**Howler JavaScript**](https://github.com/goldfire/howler.js)

It's an audio library for the modern web. It defaults to Web Audio API and falls back to HTML5 Audio. This makes working with audio in JavaScript easy and reliable across all platforms.

**Notice**

In oder to get rid of the Cross Origin errors in the console, you'll need to run a local HTTP server from your project's directory and load the circles.html file from there. The steps are:

1. Navigate to your project folder in the terminal 
2. Run `python -m simpleHTTPServer`
3. Open up your browser and navigate to [http://localhost:8000](http://localhost:8000)
4. Select the html file



