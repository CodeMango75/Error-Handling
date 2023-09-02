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
