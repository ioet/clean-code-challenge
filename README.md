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

## Vertical and Horizontal formating
![Captura de Pantalla 2022-03-04 a la(s) 10 13 08](https://user-images.githubusercontent.com/11364767/156788869-930be01f-8cc2-412f-ac99-23068626f32d.png)

# Functions (& Methods)

Functions and methods (I don't differentiate here) are the meat of any code we write. All our code is part of some function or method after all. And we use functions to call other functions, build re-usable functionalities and more.

Functions are made up of three main parts:
- Their name
- Their parameters (if any) 
- Their body

## How Many Parameters Are Okay?
![Captura de Pantalla 2022-03-04 a la(s) 10 45 28](https://user-images.githubusercontent.com/11364767/156794656-73b81113-8261-467b-9b36-aa8a4c157415.png)

## Keep Functions Small
Besides the number of paramters, the function body should also be kept small. In order to be small, functions should just do one thing. Exactly one thing.

Example (large login function, no abtraction):
```
function login(email, password) {
  if (!email.includes('@') || password.length < 7) {
    throw new Error('Invalid input!');
  }
  const existingUser = database.find('users', 'email', '==', email);
  if (!existingUser) {
    throw new Error('Could not find a user for the provided email.');
  }
  if (existingUser.password === password) {
    // create a session
  } else {
    throw new Error('Invalid credentials!');
} }
```

Example (small function, but is doing one thing?):
```
function login(email, password) {
  validateUserInput(email, password);
  verifyCredentials(email, password);
  createSession();
}
```

A function is considered to do just one thing if all operations in the function body are on
the same level of abstraction and one level below the function name.




