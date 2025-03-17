A method to attempt an execution but skip if fail is detected. Fail can be then labelled with an error
```python
try:
    x = 10 / 0  # This will cause a ZeroDivisionError
except ZeroDivisionError as e:
    print(f"Error: {e}")

```
The function mentioned after the 'except' keyword are inbuilt into python. These will feed the detailed error into variable 'e' which can then be displayed:


| **Exception Name** | **When It Occurs**                                                      |
| ------------------ | ----------------------------------------------------------------------- |
| FileNotFoundError  | When trying to open a non-existent file                                 |
| ZeroDivisionError  | When dividing by zero (`10 / 0`)                                        |
| ValueError         | When passing an invalid value to a function (`int("abc")`)              |
| TypeError          | When using an operation on an incompatible type (`"2" + 2`)             |
| IndexError         | When accessing a list index that doesn't exist (`my_list[100]`)         |
| KeyError           | When accessing a non-existent dictionary key (`my_dict["missing_key"]`) |

User defined errors can also be introduced. These process the failure to determine what time of fault has been detected
```python
class CustomError(Exception):
    """Custom exception for a specific case"""
    pass

def check_number(num):
    if num < 0:
        raise CustomError("Number cannot be negative!")  # Raising a user-defined error
    return num
# USE CASE
try:
    check_number(-5)
except CustomError as e:
    print(f"Caught Custom Exception: {e}")

```
Example above explains, that for specific conditions of input to check_number() we will assigned a CustomError response. This response is then parsed to variable 'e'.


When opening files for processing, the below syntax will close the defined file if an error occurs:
```python
try:
    with open("example.txt", "r") as file:
        content = file.read()
        print(content)
except FileNotFoundError as e:
    print(f"Error: {e}")

```

### raise
You can manually trigger errors in the execution of our class
```python
def divide(a, b):
    if b == 0:
        raise ZeroDivisionError("Cannot divide by zero!")  # Raising an exception
    return a / b

print(divide(10, 2))  # Works fine
print(divide(5, 0))   # Raises ZeroDivisionError
```

In an event where you want to stop execution under error, you can run some logging or some post processing before actually ending the execution. This can be done by sending in an empty 'raise'
```python
def fetch_data():
    try:
        # Simulating an error
        result = 10 / 0  
    except ZeroDivisionError as e:
        print(f"Logging error: {e}")  # Logging the error
        # Do anything you want before the execution is stopped
        raise  # Re-raises the same exception

fetch_data()  # Logs and then raises ZeroDivisionError again
```

### finally
// TODO
Read more about the finally function
```python
def process_data():
    try:
        print("Processing data...")
        raise ValueError("Something went wrong!")  # Original exception
    finally:
        print("Cleaning up resources...")
        # If you raise another exception here, it overrides the first one.
        raise RuntimeError("Cleanup failed!")

process_data()  
# Only RuntimeError is shown, original ValueError is lost.
```