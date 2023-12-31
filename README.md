# Error Handling 
* Error handling, in simple terms, is the process of dealing with unexpected or exceptional situations that can occur during the execution of a program. 
* It involves identifying when something goes wrong in your code and taking appropriate actions to prevent program crashes or undesirable outcomes. 

Error handling is a crucial skill for any programmer because it allows you to gracefully handle unexpected situations that may arise during the execution of your code. There are several mechanisms in python that facilitates Error Handling:
1. Try
2. Except
3. Else
4. Finally

In programming, errors can come in various forms, such as invalid inputs, file not found, division by zero, and many others. Error handling allows you to address these issues so that your programs can handle adversity and continue functioning as intended.

## Types of Errors

In python, we can encounter the following types of errors:

**Development Time Error** are the errors encountered during developing a program. It is easy to locate and identify. These types of errors occur when we write codes for example non variable declaration, type error, zero division error etc. 

**Logical Error** is hard for interpreter to identify. As of now, there is no tool to detect a logical error. The only best option available is to *test* the program. This type of error is given to seniors or *Quality Assurance Team* to perform the Testing. 
Testing is done through Dry Runs (Step by step) 
```
def add_two_numbers(a,b):
    print(7,7, type(a),type(b)) # thats how dry testing is done like see if the values are passed to a and b and if the data types are same.  
    return a - b
print(add_two_numbers(7,7)) # Create case 7 + 7 = 14, False
```

**Production/Runtime Error** can cause <span style="color: red;">great loss</span>. This error occurs during the running of an application. In businesses, this can cause a huge loss to an entity. The Application should be capabale of running 24/7. This error can also be caused by a user who puts an invalid function or pressure to The server. 


### Try and Except

* Try or `try` is used to prevent an error occured from the user side. 
* Try is used from a user perspective. 
* This is where you enclose code that you expect might raise an exception or error.
* Try lets us test the block of code
* Except block lets us handle the error

***Syntax***

```
try: # We can pass classes 
   **logic** # Maybe error occur here.
except (errorclass1, errorclass2):
   **action** # What can be performed to prevent the error
else:
    # run if error not occur         
finally:
    # line will always run
```
Example 1:
```
print("Talaal")
print("Amna")
try:  
    print(a)
except NameError: # NameError is the class we defined that will encounter due to non declaration of object 
    print("Variable Not Defined")    
print(75)
print("Yaaay!")
```
```
num1 = 7
num2 = 0

try:
    print(num1 / num2)
except (NameError, ZeroDivisionError):
    print("Invalid Division")   
```

**Example 1**
```
num1 = 7
num2 = 0
b = 20

try:
    print(20)
    print(num1 / num2) # Error Occured
    print("Hello") # No print
    print("World") # No Print 
except (NameError, ZeroDivisionError):
    print("Invalid Division")  # After error, will directly come here   

print("Pakistan") # This will be printed
print("Zindabad") # This will be printed too
     
```
If python encounters error in any line of Try Block, it will directly go to except block and then the cursor will move ahead not backwards. To solve this issue, we can individually perform exception handling

```
num1 = 24
num2 = 0
b = 25

print("Talaal")
print("Yousoof")
try:
    print(num1/num2)
except ZeroDivisionError:
    print("Zero Cannot Be Divided")
try:
    print(d)
except NameError:
    print("Variable d is not defined")

print("Pakistan")
print("Zindabad")
```


# Exception Handling 

* Exception handling is a programming concept and a set of techniques used to manage and respond to exceptional or unexpected events
* Exception handling is not specific to Python but is a common practice in many programming languages.
* It allows you to gracefully handle errors and unexpected situations, preventing program crashes and ensuring that your code continues to run smoothly.

Key Components of Exception Handling are:
1. **Throwing or Raising Exceptions** Exceptions can be raised by `raise` keyword. 
2. To handle exceptions, we can use combination of `try`, `excetp`, `else` and `finally`.
3. **Handling Logics** Inside the `except` block, we can define logics to respond to exceptions
4. You can include an `else` block, which runs when no exceptions occur in the try block
5. The `finally` block is optional but runs regardless of whether an exception occurs or not. It's often used for cleanup tasks, like closing files or releasing resources. 

### Examples

**Example 1**

```
num1 = 100
num2 = 10
b = 10
list1 = [1,2,3,4,5,6,7,8,9]

print("Talaal")
print("Yousoof")
try:
    print(b)
    print(num2*num1)
    print(list1[20])
    print("Hey Bro")
except Exception as e:
    print(f'Something is Wrong! {e}')    
print("Pakistan")
print("Zindabad")
```

**Example 2**

* We can also create our own errors. 
```
class StudentCard():
    def __init__(self, roll, name, age):
        if age < 18 or age > 70:
            raise Exception("Not Allowed")
        self.roll = roll
        self.name = name
        self.age = age
s1 = StudentCard(1, "Talaal", 27) 
print(s1.name)
print(s1.roll)
print(s1.age)      

try:
    s1 = StudentCard(1, "Mehwish", 17)
except Exception as e:
    print(e)
```

**Example 3**
```
try:
    num1 = int(input("Enter a number: "))
    num2 = int(input("Enter another number: "))
    result = num1 / num2
    print("Result:", result)
except ZeroDivisionError:
    print("You cannot divide by zero.")
except ValueError:
    print("Invalid input. Please enter a valid number.")
except Exception as e:
    print(f"An unexpected error occurred: {e}")
else:
    print("No exceptions were raised.")
finally:
    print("This will always be executed.")
```

### Except Exception as e

we might want sometimes to use the expression **except Exception as e** which is breakdown as under:
* `except` keyword: It signals the beginning of an exception-handling block.
* `Exception` is a base class for all exceptions in Python. By specifying `Exception`, you're indicating that you want to catch any exception that inherits from the `Exception` class.
* `as e`: This part allows you to assign the caught exception object to a variable named
* `e`. You can use this variable `e` to access information about the exception, such as its type or the error message it contains.

The use of `except Exception as e` is a common and widely accepted convention for handling exceptions in Python, but it's not a strict requirement. You can use different variable names instead of `e` if you prefer. 

## Hot Takes

* When we give a class name of error to `except` block, this approach is known to **catch a specific exception by their class names**. For example if we print(p), a NameError will arise because p is not defined. 
* It's recommended to give class names to except blocks when you know the specific types of exceptions that your code might encounter and when you have a clear plan for handling those exceptions differently.
* This approach improves code clarity and maintainability, making it easier to understand how your program responds to different types of errors.

# File Handling

## File Management System
* File management system refers to handling of multiple files such as text files, audio files, video files etc.
* Append mode keeps old data as it it is and helps to create a new dat as well 
* `open` function is used to open a file. 
* If you're working in a terminal and you want to know which directory you're currently in, you can simply type `pwd` *Print Working Directory* and press Enter. The terminal will then display the full path to your current working directory, like **/home/username/Documents** or **C:\Users\username\Documents**, depending on your operating system.
* **pwd** provides a full path to directory and particularly useful when you need to reference or work with files and directories using relative paths, as it helps you understand your current position within the directory structure.

There are two types of paths in File Management System: 

###  **Absolute Path**: 
* An absolute path starts from the very beginning, at the root of your computer's file system, and gives the full, exact location of a file or folder.* Example: `C:\Users\YourName\Documents\file.txt` (for Windows) or `/home/yourname/Documents/file.txt` (for Linux).
* In most of the cases, it is a practice to give absolute path as a major path to open a file.
* Absolute path acts like a **GPS** giving complete full address; county, city, town, street, house 

### **Relative Path**
* Imagine a relative path as giving directions from your current location, like saying "go two blocks down and turn left."
* A relative path is described based on your current location within the file system. It's relative to where your program is running.
* Example: `../../folder/file.txt` means "go up two levels in the directory structure, then find the 'folder' and 'file.txt' inside it."
The Identifiers in Relative Paths:
* `./` Current Location 
* `./xyz/aa/xyz.txt`
`../` the double dots before forward slash means we have moved one step behind. 
* `../../` means we have moved one folder behind the current.
* It does not require 100% path. 

### Difference Between Absolute and Relative Path
* Absolute paths start from the root and provide the complete location. They are fixed and unchanging.
* Relative paths are described based on the current location and adapt as you move around the file system.
* The main difference is in how they specify file locations, with absolute paths being more explicit and relative paths being more adaptable.

### File Modes in Python 
* **UTF-8** is a mode which has almost 14 million characters and are mapped in ASCII Codes. Best example is having multiple charachters of different languages together. 
* UTF-8 is a standard mode
There are several modes in python:
* `r` means to read file. Reads every data of file. It is a default mode.
* `r+` means read and write
* `w` means write only. 
* `w+` means Write and Read
* `a` means append mode. Adds after last element. Append creates a file if no file is created previously. Prior data is not changed
* `a+` means read and add in the same system. Prior data is not changed
* `x` creates a new file if not existing. If ile already exists, it will generate an error. 
```
f = open("README")
print(f.readline()) # Reads the first line
print(f.readlines()) # Returns comma separated lines in the form of elements
print(f.read()) # Reads every Data
print(f) # Returns the file location and type
```
* `close()` function is always recommended to include when reading a file. 

### With Block
* 

**with** *open("README")* as file:
   a = file.readlines()
   print(a)

* This has given us the benefits of connectivity. Frees up the connectivity. 

## Apply File Mode

**with** *open("README", mode='r')* as file:
   a = file.readlines()
   print(a)
