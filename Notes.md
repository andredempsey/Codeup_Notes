

####Helpful commands
Command-Shift-3 - takes full screen shot
Command-Shift-4 - allows select screen capture
Command-Shift-4 (then use space)- takes screen shot of a particular window


GIT Process (done in the Mac Window)
---
####Initialize a repository
git init
git status
####Add file to a repository
git add *file name*
####Commit file to repository
git commit -m *file name*
####Push to GitHub repository
git push -u origin master (only used first time); the -u stands for upstream
git push origin master (used for subsequent pushes)

####Retrieve older versions

git log (this will allow me to retrieve the key)

git checkout {key} (working version becomes the version checked out)



####Check which remotes you have
git remote
the -v option shows details

####Ternary Operator
PHP has another way of making short comparisons - the ternary operator ?:. Using this, we can make quick comparisons and return a result based on the comparison.

A comparison with the ternary operator would look like this:

```
$age = 22;
// [condition]?[value if true]:[value if false];
$is_adult = $age >= 18 ? true : false;

```

####Do-While Loop
This type of loop will execute the code at LEAST once.
```
do
{
	[some code];
	[incrementer];
}
while ([condition]);
```
---
####PHP CLI SAPI
Using I/O Streams
PHP provides us with the following standard streams.

STDIN - Accepts input from user
STDOUT - Output responses
STDERR - Output errors

The default for these outputs is to the **terminal**, however, you could output STDERR to an error log file, for example.

```
// Write the output
// Notice the space after the ?
fwrite(STDOUT, 'What is your first name? ');

// Get the input from user
$first_name = fgets(STDIN);

// Output the user's name
fwrite(STDOUT, "Hello $first_name\n");
```
You can pass arguments to a php program by using the $argc and $argv variables within your code.  The $argc returns the number of arguments which were passed and the filename (*example:  php test.php 2 will return an integer of 2*).  The $argv returns an array with the first item in the array being the filename.

Use the is_numeric() function to check if a value is numeric.

####for loop
format:

for ([start value]; [test];[incrementer/decrementer])
{
	[code]
}

sample code:

```
for ($a = 1; $a <= 5; $a++) {
    echo "\$a has a value of {$a}\n";
}
```
---
13 May 14

```fwrite(STDOUT, "What is your name? ");```

and

```echo "What is your name?\n";```

are **equivalent**.

On the input side...

```$some_var= fgets(STDIN);```

and

```$some_var= fputs(STDIN);```

are **equivalent**.

####foreach loop

```
foreach (array_expression as $value) {
    statement
}

```
Sample (using *for loop*):

```
$todos = array('A','B','C');
for ($i=0;$i < count($todos);$i++)
{
	$todo=$todos[$i];
	echo $todo . PHP_EOL;
}
```

Alternate Sample (using *foreac loop*):

```
foreach ($todos as $todo)
{
	echo $todo . PHP_EOL;
}
```
####Looping through associative arrays

```
foreach (array_expression as $key => $value) {
    statement
}
```

Other tasks:

**fruit.php** push to GitHub
1. Create an array of fruits.  Write a loop that prints the fruits
	-as a for loop 
	-as a foreach loop
1. Modify the fruit array so that the fruitname =>color
	-print out using a foreach loop
		Apples are red.
		Bananas are yellow.
		Oranges are orange.
		Grapes are purple.
		Kiwis are green.
---
14 May 14
standard example of foreach with multidimensional array.

```
$books = array(
    'The Hobbit' => array(
        'published' => 1937,
        'author' => 'J. R. R. Tolkien',
        'pages' => 310
    ),
    'Game of Thrones' => array(
        'published' => 1996,
        'author' => 'George R. R. Martin',
        'pages' => 835
    ),
    'The Catcher in the Rye' => array(
        'published' => 1951,
        'author' => 'J. D. Salinger',
        'pages' => 220
    ),
    'A Tale of Two Cities' => array(
        'published' => 1859,
        'author' => 'Charles Dickens',
        'pages' => 544
    )
);

foreach ($books as $book => $properties) 
{
    if ((int)$properties['published'] > 1950) //check published date and only show after 1950
    {
        echo "Book title = {$book}\n"; 
        foreach ($properties as $property => $value) 
        {
            echo "\t{$property} = {$value}\n";
        }
    echo "\n";
    }
}
```

**break** means exit the loop
**continue** means skip over the current iteration

break 2 will cause an exit from two levels of loops
break 3 will cause an exit from three levels of loops

Use the **switch** command in place of multiple **elseif** statements

```
$value = 'Hello!';

switch (gettype($value)) {
    case 'integer':
        echo '$value is an integer';
        break;
    case 'float':
        echo '$value is a float';
        break;
    case 'boolean':
        echo '$value is a boolean';
        break;
    case 'array':
        echo '$value is an array';
        break;
    case 'null':
        echo '$value is null';
        break;
    case 'string':
        echo '$value is a string';
        break;
}
```
use **default** at the end of the switch to snag items that don't meet any of the cases

when working with dates; make sure you set the time zone as follows:
```
// Set the default timezone
date_default_timezone_set('America/Chicago');
```
####To Do Assignment

1. Fix the todo list to allow lowercase letters
1. Fix the display to start with '1'

sequence of commands to reorder an array and set first item to use an index of 1 instead of 0

```
unset($items[$key]);
$items=array_values($items);
array_unshift($items,"");
unset($items[0]);
```

15 May 14
####Functions
```
function name($arg_1, $arg_2, /* ..., */ $arg_n) 
{
    // code goes here
}

```
if you want to set the default for a variable passed to a function (in case user doesn't pass a value), use the following format
```
function compare($a, $b, $strict=true)
{

}

```

Additional functions Ben recommended I look at...

```
Example #1 func_get_args() example

<?php
function foo()
{
    $numargs = func_num_args();
    echo "Number of arguments: $numargs<br />\n";
    if ($numargs >= 2) {
        echo "Second argument is: " . func_get_arg(1) . "<br />\n";
    }
    $arg_list = func_get_args();
    for ($i = 0; $i < $numargs; $i++) {
        echo "Argument $i is: " . $arg_list[$i] . "<br />\n";
    }
}

foo(1, 2, 3);
?>

```

and another one
```
<?php
function foobar($arg, $arg2) {
    echo __FUNCTION__, " got $arg and $arg2\n";
}
class foo {
    function bar($arg, $arg2) {
        echo __METHOD__, " got $arg and $arg2\n";
    }
}


// Call the foobar() function with 2 arguments
call_user_func_array("foobar", array("one", "two"));

// Call the $foo->bar() method with 2 arguments
$foo = new foo;
call_user_func_array(array($foo, "bar"), array("three", "four"));
?>

```
16 May 14

You can use sleep([delay]) to pause for a number of seconds.

Two useful functions are:

```isset()```

always check if a variable is set before checking a condition
for example:

if(isset([$value]) && $value !='')

and

```empty()```

caution:  '' and 0 and False will cause issues; use on strings


####Challenge assignment
<?php

$hand = array('A-H', '5-D', 'K-C', 'A-S', '4-H');

function getTotal($hand)
{
    $total = 0;

    // loop through hand and calculate total value
    // use "explode" function to separate card suit and value
    // aces count as 11 unless you are over 21 and then they count as 1
    // K, Q, and J count as 10
    // numeric cards count as their value

    foreach ($hand as $card)
    {
        var_dump(explode('-', $card));
    }

    return $total;
}

echo getTotal($hand) . PHP_EOL;

####Sorting Arrays
19 May 14

sort([array]);  //sorts alphabetically
rsort([array]);  //sorts reverse alphabetically


The bitwise OR operator is | (single pipe)

asort([array]);  //keeps associative array keys
ksort([array]); //sorts by array keys


//dzone
//hackerzone
//RSS
//feedme

review conditional statements that look like this

```
    if (array_search($searchstring,$targetarray)!== FALSE) 
    {    
     return true;
    }
    else
    {
     return false;
    }
```
and look at replacing with the following (piece from within a function):


return array_search($searchstring, $targetarray)!==false;

####Add or removing items from beginning or end of an array
array_shift(array); //removes from beginning and returns value removed
array_unshift(array, var); //add to beginning
array_push(array, var); //add to end
array_pop(array); //removes from end and returns value removed

####Cue vs Stack

**Stack**
Last in, First Out
use array_push and array_pop


**Cue**
First in, First Output

use array_push and array_shift()

####Including references to files

$filename = 'file.txt';
$handle =fopen($filename, 'r'); //first arg is the file and the second arg is action; for example the 'r' means 'read'
don't open a file to write unless you have to write back to the file

$filesize($filename);  //this obtains the number of bytes

$somestring = fread($handle,$filesize);  //need the $filesize because the fread command need to know how far to read
at the end of your code it is best practice to close the file
fclose($handle);

before reading a file it is recommended to check 
```
is_readable($filename);
```
to make sure the file exists and is readable 

```feof($handle);``` checks if file pointer has reached the end of the file and returns a boolean

before writing to a file it is recommended to check 
```
is_writable($filename);
```
or
```
is_writeable($filename);
```
to make sure data can be written to the file

###HTML and CSS

<p id="test">content</p>
<img src="">

**SHORTCUT**
use HTML:5 then press tab to get the following
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    
</body>
</html>

Verbs in the HTML cut and paste from (http://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol)
**GET**
Requests a representation of the specified resource. Requests using GET should only retrieve data and should have no other effect. (This is also true of some other HTTP methods.)[1] The W3C has published guidance principles on this distinction, saying, "Web application design should be informed by the above principles, but also by the relevant limitations."[12] See safe methods below.
**HEAD**
Asks for the response identical to the one that would correspond to a GET request, but without the response body. This is useful for retrieving meta-information written in response headers, without having to transport the entire content.
**POST**
Requests that the server accept the entity enclosed in the request as a new subordinate of the web resource identified by the URI. The data POSTed might be, as examples, an annotation for existing resources; a message for a bulletin board, newsgroup, mailing list, or comment thread; a block of data that is the result of submitting a web form to a data-handling process; or an item to add to a database.[13]
**PUT**
Requests that the enclosed entity be stored under the supplied URI. If the URI refers to an already existing resource, it is modified; if the URI does not point to an existing resource, then the server can create the resource with that URI.[14]
**DELETE**
Deletes the specified resource.
**TRACE**
Echoes back the received request so that a client can see what (if any) changes or additions have been made by intermediate servers.
**OPTIONS**
Returns the HTTP methods that the server supports for the specified URL. This can be used to check the functionality of a web server by requesting '*' instead of a specific resource.
**CONNECT**
Converts the request connection to a transparent TCP/IP tunnel, usually to facilitate SSL-encrypted communication (HTTPS) through an unencrypted HTTP proxy.[15][16] See HTTP CONNECT Tunneling.
**PATCH**
Is used to apply partial modifications to a resource.[17]

This will add an element that allows user to jump to top of page (or anywhere else) 
<a href="#top">Go to the top of the page</a>

You need to add the following id as the target location on the page.
<a id="top"></a>


####Forms
put these two lines into a file named form.php

<?php
var_dump($_GET);
var_dump($_POST);
?>

Form Inputs and Submitting
So far, we have covered the basic structure of HTML forms, and a little bit about how they work. Now we will begin to cover form inputs and submission.

Form Inputs
Form inputs can be defined by using the HTML <input> element. The <input> element is a void element, since it doesn't have any inner content.

Type Attribute
There are many types of form inputs in HTML. Since most HTML inputs use the same HTML element, <input>, the browser needs a way to distinguish the input type. This is achieved by specifying a type attribute as part of the <input> element. The types we will be covering in this unit are:

submit
text
password
checkbox
radio
We will also be covering the textarea and select input types, which use unique HTML elements that will be discussed later in this unit.

Name Attribute
HTML inputs should also have a name attribute that describes what the input is. The name attribute for the input will appear as the key in the query string when the form is submitted.

Id Attribute
Additionally, an id attribute with the same value as the name attribute is often specified with the <input>. The id attribute is used for input labeling and also for easy access via JavaScript.

Value Attribute
Some input types, like submit, text, and email, can have an initial value set by using the value attribute.

Placeholder Attribute
Some input types, like text, password, email, and textarea, can have a text overlay that give information about the input that disappears once data is entered for the input. This text overlay is accomplished using the placeholder attribute. The placeholder attribute will not be shown if a value is set for the <input>.

Note: The placeholder attribute is supported in Internet Explorer 10+, Firefox, Opera, Chrome, and Safari.

Input Example
Using all the attributes we just learned, here is a simple text input:

```<input type="text" id="username" name="username" placeholder="Enter your username">```

typical method

    <label for="username">Username</label>
    <input id="username" name="username" type="text" placeholder="username">

alternate method for linking label to input
    <label>Username: <input name="username" type ="text"></label>

---

    run this to setup a new site on your computer
    1.  (in your mac) cd ~/vagrant-lamp/
    2.  copy and paste the following into the command line (replacing the 'todo.dev' reference with the name of your new site)

    ansible-playbook -i ansible/local_hosts ansible/local-site-create.yml -e "domain=todo.dev";
    ansible-playbook ansible/site-create.yml -l vagrant -e "domain=todo.dev"
    **check for the correct command line string in the vagrant-lamp README.md file.**
navigate to folder under sites and mkdir public
sudo subl /etc/hosts
add another reference at the bottom of the file (see the todo.dev example)
save and close
create a Git repository
---


26 May 14

###JavaScript

Arduino - hardware; with microcontroller and inputs/outputs for sensors..can be programmed with JavaScript

using !!true is used when casting to a boolean


function generate_random_word() {
    return strtolower(exec('sed `perl -e "print int rand(99999)"`"q;d" /usr/share/dict/words')) . PHP_EOL;
}

###iterating through arrays in JavaScript (new functionality that is NOT supported in older browsers)

var names = ['Chico', 'Harpo', 'Groucho', 'Zeppo'];
names.forEach(function (element, index, array){
    //element is the name of the item
    //index is the iterator
    //array is the array itself
    console.log ('The name at index ' + index + ' is ' + element);
});

could also implement as a named function like this:

var names = ['Chico', 'Harpo', 'Groucho', 'Zeppo'];
function ShowNames (element, index, array){
    //element is the name of the item
    //index is the iterator
    //array is the array itself
    console.log ('The name at index ' + index + ' is ' + element);
};
names.forEach(ShowNames);


###PHP and HTML


Superglobals
PHP provides some built in variables for us that are visible in all scopes, anywhere in our applications. These variables are referred to as superglobals.

Using Superglobals
We can view the entire list, and learn more from the PHP documentation for superglobals. For this unit, we'll be learning about:

$_SERVER — Server and execution environment information.
$_REQUEST — HTTP Request variables.
$_GET — HTTP GET variables.
$_POST — HTTP POST variables.
$_SESSION — Session variables.
$_COOKIE — HTTP cookies.
$_FILES — HTTP File Upload variable.

$_SESSION
PHP allows us to persist data across page loads using sessions. Sessions are stored on the server, and each session has a unique session id (SID) that we can use to get information out of the $_SESSION superglobal array.

To start using a session, the session must first be initialized/retrieved using the session_start() function.

To set and get data from the session, we use the supergloabal array $_SESSION.

To destroy all of the data associated with the current session, we can use session_destroy(). This method does not remove all the data currently stored in $_SESSION. 

```$_SESSION = array();```

use this php function in your code to redirect back to the page.

```
header('Location: /todo_list.php');
exit;
```

Brian Eno's Oblique Strategies

Peter Hansen's TED Talk "Embrace The Shake"
sacha @simpleswitchlabs.com
simpleswitchlabs.com
photoboop.com


<?php can also be written <? using short tags

instead of <?php echo ... you can use
<?= ....
{no space between the ? and =}

https://xss-game.appspot.com
use htmlspecialchars(string) to protect from users injecting code into input fields

#always check user input before outputing...at least use htmlspecialchars(string)


##JavaScript and the DOM

document.getElementById()

document.getElementsbyClassName()

document.getElementsByTagName()

listItems[i].style['color'] = 'blue';
or
listItems[i].style.color = 'blue';

##common events

click
mousedown
mouseup
change
keydown
keyup
focus
blur
submit

e.preventDefault() ... this tells browser to not do what it normally does
preventDefault is very useful for validation

syntax for creating new object in JavaScript

var car = {};

this is the same as var car = new Object();


var books = <?= json_encode($phpBooks, JSON_PRETTY_PRINT); ?>;

check out the Canvas Object
allows you to draw objects on screen

##Working with Dates using moment.js

first include the following line in your header

<script src="/js/moment.js"></script>

// get the current date/time with moment
var now = moment();

// getting calendar date strings
console.log(now.calendar());

// formatting dates
console.log(now.format("dddd, MMMM Do YYYY, h:mm:ss a"));

// date addition
console.log(moment().add('days', 1).fromNow());
console.log(moment().add('weeks', 1).fromNow());

// date subtraction
console.log(moment().subtract('days', 1).fromNow());
console.log(moment().subtract('weeks', 1).fromNow());

// get a specific date
var codeup = moment("2-4-2014", "MM-DD-YYYY");
console.log(codeup.fromNow());

##JQuery

typical syntax is 
$('element or id or class').operation

example
$('h1').html(); //retrieve HTML from h1 elements
$('#someid').html(); //retrieve HTML from an element with id='someid'
$('.aclass').html(); //retrieve HTML from elements with class ='aclass'

put information into the parentheses to push data to the element

for example:
$('#someid').html('change text to me'); //changes html for element with id='someid' to the text in the parentheses

###Event Handlers in JQuery

some events include:
.click(function())
.dblclick(function())
.hover(enter function(), exit function())
The .hover() event handler combines two other event handlers: mouseenter() and mouseleave().

$('#someid').click(function(){do something}); 
