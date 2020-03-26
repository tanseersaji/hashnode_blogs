## How to write good code?

There are two ways to write any code, the one that works and then there is the right way. It does not matter whether your code works or not if your code does not have proper structure no one can ever understand what you are trying to write. This blog talks about some "good coding practices" that will improve your code's beauty instantly.

There is an old saying:

>  I don't write comments because if it is hard to write, then it must be hard to read. 

I don't know who said this, but I am pretty sure that the programmer was really high. However, carefully chosen comments may make it harder to read the code like 10 lines of comment for every 1 line of code. So there must be a balance between these two factors.

But, I completely disagree with this kind of programming attitude. My friend, who is a successful Android developer, said it right:

> ... sometimes I feel turned on looking at my code, it is so elegant and beautiful, it's orgasmic... 

And I replied to this, "You're code gay bro?", but then when I saw his code, I felt all those things that he described and then he said, "You are code gay, bro". That is the exact moment I realised the importance of writing "good" code and how to write code is similar to writing poems. At that very second, I realised the deeper meaning of  [wordpress.org](https://wordpress.org/) 's slogan. **CODE IS POETRY**

Since then, I have researched exhaustively and found some insights about how one can write good code and I decided to share those insights with you all.

## 1. Write comments
I choose this one because this is the part where most people overdo, they comment every single thing, which is obviously bad. As I said earlier, writing too many comments can make it very hard to read the code. And it is also bad if you have a very little comment.

Ideally, you can write 1 to 3 lines of comments (or docstring) that explains some unique method you have in your code whose name is not sufficient to describe what that method is about.

## 2. Write meaningful identifier names
If you don't know what an "*identifier*" is: Identifiers are user-defined symbols used to uniquely identify a program element in the code. They are also used to refer to types, constants, macros and parameters. An identifier name should indicate the meaning and usage of the element being referred. It can be a namespace, class, method, variable or interface.

All the variable name, class name, method name or any other identifier you have specified in your code should have a meaning and if some other person read that name, he/she should precisely understand what that method does or what that variable is for.

For example, *canScrollHorizontally* is so much better and meaningful that *ScrollableX*.

## 3. Follow the naming conventions
This is kind of extension to our point number two, writing meaningful names is one of the naming conventions that you must follow, if you want to write good code.

**CamelCase** is one of the naming styles with which you can write consistent names: In camelCasing, the first letter of the name is a small letter and every other word in the name start with a capital letter. *canScrollHorizontally* is the best example of camelCased variable name and *ScrollableX* is not a camel-cased variable name. Also, do not start the name with an underscore ( _ ).

But when you are declaring the name of a class, namespace or a package then, you have to start the name with a capital letter and rest of the name will follow camel casing.

Another thing you have to make sure while writing the names is that you should not write lesser known abbreviations, instead write the full form. For example: instead of writing *getWin* you can write *getWindow*. And if there is a case where if you write the full form then the variable name will become too big, then, in that case, write the abbreviation and write a comment above the variable/method declaration describing the use of that element.

Microsoft has released a bunch of  [Naming Conventions](https://docs.microsoft.com/en-us/dotnet/standard/design-guidelines/general-naming-conventions), you can give that a read.

If you are coding in Python, then your code must follow the  [PEP8 style](https://www.python.org/dev/peps/pep-0008/).

## 4. No long methods
If your code has a long method or function, that does multiple things then it is better to divide that method into multiple function/methods each method doing a single task.

## 5. About long strings
If you have a long string or some hash code, like the secret code you get from Facebook, Google, etc. Instead of using them directly, it's better to put that string in a variable first and then use that variable everywhere. This is useful when you have to change the string, you can just make the changes at that one place where you initialise the variable with the string and you there is no need to make changes everywhere which is more error-prone.

## 6. Choose correct Data Types
Suppose you have a variable age and you have declared this variable as double, which is totally unnecessary because you know most people only live for like 80 years or so, therefore you only need to use byte or int data type, that will save a lot of memory.

The point is, choose a variables data type keeping in mind what information will that variable hold. And also remember that memory is a limited resource, use that wisely.

## 7. Indentations and Brackets
If you are coding in python, then you don't have to worry about this point. But if you are using some language that follows C like syntax, like PHP and JAVA, you have to take care of the indentations and brackets, consider the following codes for an example:

```
// code 1: with proper indentations and brackets
$i = 29; 
if ($i % 2 == 0) { 
    echo "{$i} is even";
 } else {
    echo "{$i} is odd";
}

// code 2: without proper indentations and brackets
$i = 29;
if ($i % 2 == 0)
{
echo "{$i} is even";
}
else
{
echo "{$i} is odd";
}
``` 
Both the codes will work fine but, you can clearly see that code 1 looks far more concise and elegant and code 2.

So that is all from my side, by following these subtle styles, your code will look a lot beautiful. Give it a shot and tell me how you feel about your code before and after applying these styles, in the comments below.

Thanks


### Further Reading Suggestion:
1. [6 Commandments of Good Code](https://www.toptal.com/software/six-commandments-of-good-code)