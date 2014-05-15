

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
