A function is a named piece of C code. The code is executed each time the function is called (named). Functions are useful for many reasons. I'll give you three.
First, if you have a complicated task that must be performed in several places in a program,-- like, say, printing or getting input, your choice is to write the complicted code in the several places, or write the code once in a named function, then name the function in several places in the program. When we use printf, it looks simple, we plug-in an argument and printf prints it on the screen. The details of printf involve making calls to the operating system. Ultimately once printf has made the right system calls, it is the operating system that does the printing. This is hidden away from us. We just call printf.

Second, functions let you think about programs a different way. You can say to yourself, "I've got this problem to solve, if only I could do XXX, then I could use XXX to solve the problem". So the big problem is broken into two parts. Writing a function to do XXX and then using the function to help solve the original problem.

Third, if you are working on a large program with a team of programmers, the large problem can be broken into several pieces. Each piece can be assigned to a small group of programmers. You would be responsible for solving your piece and could work independently of the other groups.

Function Calls
You have already been introduced to function calls (function uses). Functions are called by using their names and sometimes supplying one or more expressions (separated by commas) plugged inside of their parentheses. These expressions are called arguments. When a function is called its arguments are evaluated, the resulting values are passed to the function, and then the function code is run (using the passed values) and often a value is returned. The statement in which the function occurs often uses the returned value. Here are some examples.
int x=5;
printf("The value of 3 times %d is: %d.\n", x,  3*x);
x = printf("%d\n",12345);
printf("%d\n", printf("%d\n",12345) );
The second statement above uses the function printf to print the line
The value of 3 times 5 is 15.
It does not use the value that printf returns. This is the most common way that printf is used. It is used for the printing work it does, not the value it returns.
NOTE: printf returns the number of characters in its output.

The third statement above is an assignment statement. The value of the expression on the right will be put into the variable on the left. The expression on the right is a call to function printf. The way a function-expresssion is evaluated is to run the function and see what value it returns. When this call to printf is executed printf prints

12345
and then a newline character. That is a total of 6 characters. So that is the value that printf returns and that is the value of the expression on the right. So variable x is assigned the value 6.
The fourth line above has two printf's in it. The outside printf has two arguments in it separated by a comma:

 
"%d\n"
printf("%d\n",12345)
Before the outside printf can be run its arguments must be evaluated. The first argument is a string literal. Its value is just itself. Note: it tells printf that the type of second argument should be int and to print the evaluation of the second argument using decimal digits. Now the second argument is a function, the function printf. We evaluate it by running it. So the inside printf prints
12345
and starts a newline AND returns the value 6. This is the value of the second argument. This value is printed by the outside printf. We see
12345
6
Function Definitions
The purpose of a function definition is to associate a name (the function name) with a piece of code. Below is an example. Three functions are defined: triple, prtTriple, and main.
 1. #include<stdio.h>
 2. int triple(int x) {
 3.     return 3*x;
 4. }

 5. void prtTriple(char *s) {
 6.    int i=0;
 7.    while (i<3) {
 8.       printf("%s\n", s);
 9.       i++;
10.     }
11. }

12. int main() {
13.   int age;
14.   printf("Please enter your age\n");
15.   scanf("%d", &age);
16.   printf("%d is triple your age\n", triple(age) );
17.   printf("%d is triple 2+3\n", triple(2+3) );
18.   prtTriple("Goodbye");
19. }
Lines 2, 3, and 4 are the definition of the function triple. A function definition begins with a type name, in our case int. This specifies the type of value that the function will return. Next comes the function name, triple. Then what follows is a pair of parentheses that contain declarations of the function's parameters separated by commas. A function's parameters are variables that will hold the values of the arguments plugged-into the function when it is called. The value of first argument is put into the first parameter, the value of the second argument is put into the second parameter and so on. Function triple has one parameter, x, so when triple is called it can take one argument (plug-in expression). This much is called the function's header.
The rest of the function, its body, is the compound statement that comes after the header. The body contains the steps (statements) that will be executed when the function is called. We have one new keyword, return. The keyword return stops the function and returns the value of the expression that comes after it.