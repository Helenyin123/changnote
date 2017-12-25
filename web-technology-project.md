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

#### Table

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

one method to set font size is specifies the pixels of the font size. The other is using "em" values, it is relatively font size means dynamic. it will automatically adapts its length relative to the font that the reader choose to use.

em = desired element pixel value / parent element font-size in pixels

```css
body {font-size: 10px;}
p {font-size：2em;} /*value 2 is a multiplier of the current em size*/
div {font-size: 0.65em} /*font size is 0.65 * parent font size*/
```

**3. font weight**

font-weight specifies the boldness of the font. The values of this property are normal, bold, bolder, lighter, 100, 200, 300, ... , 800, 900.

**4. line height**

line height specifies the amount of space between lines. The value of this property are normal, 3.5, 3em, 50%

**5. text align**

text align specifies how the text is aligned. The value are right, center, left

**6. text decoration**

text decoration gives underline or line through or overline effect

**The Box Model**

In a document, each element is represented as a rectangular box. In CSS, each of this rectangular boxes is described using box model. Each box has four edges: the margin edge, border edge, padding edge and content edge.

![](https://www.codeproject.com/KB/HTML/567385/boxmodel-image.png)


# Backend Part

## 1. The Command Line

**cd**: change to another directory/path  
**ls**: list all the files and directories in current directory  
**touch**: create a new file, it could be any form, for example .java .txt .xls  
**mkdir**: create a new directory  
**rm**: remove a file  
**rmdir/rm - rf**: remove a directory

## 2. Node JavaScript

Originally, javascript is used only for browser, which means it can only be used in frontend side.  
NodeJS enable us to write javascript on both frontend side and server side

