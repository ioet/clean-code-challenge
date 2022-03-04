# clean-code-challenge


# Naming :notebook:

Naming things (= variables, properties, functions, methods, classes) correctly and in an understandable way if an extremely important part of writing clean code.

**Be descriptive**, names have one simple purpose: They should describe what's stored in a variable or property or what a function or method does. Or what kind of object will be created when instantiating a class.

## Some ground rules!
| Variables & Constants  | Functions and Methods | Clases |
| ------------- | ------------- | ------------- |
| Data containers  | Commands or calculated values | Use to create "things"  |
| We use Nouns or short prhases with adjetives  | Use verbs or short phrases | Use nouns |
| Eg: userData, CONTANT_EMAIL | Eg: sendData(), print_document() | Ex: User(), ShoppingCart() |

**Exception:** Boolean variables, contants, functions and methods are better named as a Yes/No question
- **isUserValid** = True
- bool **inputIsValid()** {}

In most situations, you should avoid generic names like handle(), process(), data, item etc.
It doesn't matter if you prefer fetch...(), get...(), retrieve...() or any other term but you should be consistent!


# Comments & Formatting :bomb:

You could think that comments help with code readability. In reality, the opposite is often the case though.

Proper code formatting (i.e. keeping lines short, adding blank lines etc.) on the other hand helps a lot with reading and understanding code.

| Bad Comments  | Good comments |
| ------------- | ------------- |
| Dividers & Markers  | Legal Information |
| Redundant Information | "Required" Explanations |
| Commented Out Code | Warnings |
| Misleading Comments | To do Notes |




