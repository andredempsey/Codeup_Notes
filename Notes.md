

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


