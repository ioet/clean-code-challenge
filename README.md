# CLEAN CODE

# Naming :notebook:

Naming things (= variables, properties, functions, methods, classes) correctly and in an understandable way if an extremely important part of writing clean code.

**Be descriptive**, names have one simple purpose: They should describe what's stored in a variable or property or what a function or method does. Or what kind of object will be created when instantiating a class.

## Some ground rules :facepunch:!
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

**Examples**:
- [Bad names](https://github.com/ioet/clean-code-challenge/blob/main/naming_Examples/01-bad-name-examples.py)
- [Good names](https://github.com/ioet/clean-code-challenge/blob/main/naming_Examples/02-better-name-examples.py)
- [Clean names](https://github.com/ioet/clean-code-challenge/blob/main/naming_Examples/03-clean-name-examples.py)

# Comments & Formatting :bomb:

You could think that comments help with code readability. In reality, the opposite is often the case though.

Proper code formatting (i.e. keeping lines short, adding blank lines etc.) on the other hand helps a lot with reading and understanding code.

| [Bad comments](https://github.com/ioet/clean-code-challenge/blob/main/good_bad_comments/bad-comments.ts)  | [Good comments](https://github.com/ioet/clean-code-challenge/blob/main/good_bad_comments/good-comments.ts) |
| ------------- | ------------- |
| Dividers & Markers  | Legal Information |
| Redundant Information | "Required" Explanations |
| Commented Out Code | Warnings |
| Misleading Comments | To do Notes |

## Vertical and Horizontal formating
![Captura de Pantalla 2022-03-04 a la(s) 10 13 08](https://user-images.githubusercontent.com/11364767/156788869-930be01f-8cc2-412f-ac99-23068626f32d.png)

[Vertical Formating example](https://github.com/ioet/clean-code-challenge/blob/main/good_bad_comments/vertical-formatting.js)

# Functions (& Methods)

Functions and methods (I don't differentiate here) are the meat of any code we write. All our code is part of some function or method after all. And we use functions to call other functions, build re-usable functionalities and more.

Functions are made up of three main parts:
- Their name
- Their parameters (if any) 
- Their body

## How Many Parameters Are Okay:question:
![Captura de Pantalla 2022-03-04 a la(s) 10 45 28](https://user-images.githubusercontent.com/11364767/156794656-73b81113-8261-467b-9b36-aa8a4c157415.png)

[Functions example](https://github.com/ioet/clean-code-challenge/tree/main/functions_examples)


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

# Control Structures
No matter which kind of application you're building - you will most likely also use control structures in your code: if statements, for loops, maybe also while loops or switch-case statements.

But control structures can also lead to bad or suboptimal code and hence play an important role when it comes to writing clean code.

### Prefer positive checks
This is a simple one. It can make sense to use positive wording in your if checks instead of negative wording.
```
if (isEmpty(blogContent)) {
  // throw error
}
if (!hasContent(blogContent)) {
  // throw error
}
```

### Avoid Deep Nesting
This is very important! You should absolutely avoid deeply nested control structures since such code is highly unreadable, hard to maintain and also often error-prone.
[dirty code](https://github.com/ioet/clean-code-challenge/blob/main/control_structure_examples/01-dirty-control-structures.js)

```
function messageUser(user, message) {
  if (user) {
    if (message) {
      if (user.acceptsMessages) {
        const success = user.sendMessage(message);
        if (success) {
          console.log('Message sent!');
        }
   } }
 } }
```


#### Use Guards & Fail Fast
Guards are a great concept! Often, you can extract a nested if check and move it right to the start of a function to fail fast if some condition is (not) met and only continue with the rest of the code otherwise.

```
function messageUser(user, message) {
  if (!user || !message || !user.acceptsMessages) {
      return;
  }
  user.sendMessage(message);
  if (success) {
    console.log('Message sent!');
  }
}
```

[Guards in action](https://github.com/ioet/clean-code-challenge/blob/main/control_structure_examples/02-guard.js)


#### Extract Control Structures & Logic Into New Functions
We already learned that splitting functions and keeping functions small is important. Applying this knowledge is always great, it also helps with removing deeply nested control structures.

[Extracting functions](https://github.com/ioet/clean-code-challenge/blob/main/control_structure_examples/03-extract-functions.js)

[Improving logic?](https://github.com/ioet/clean-code-challenge/blob/main/control_structure_examples/04-invert-logic.js)


#### Embrace Errors
Errors are another nice way of getting rid of redundant if checks. They allow us to utilize mechanisms built into the programming language to handle problems in the place where they should be handled (and cause them in the place where they should be caused...).

[Using error](https://github.com/ioet/clean-code-challenge/blob/main/control_structure_examples/05-use-errors.js)

#### Polymorphism & Factory Functions
Sometimes, you end up with duplicated if statements and duplicated checks just because the code inside of these statements differs slightly.

[Factory function](https://github.com/ioet/clean-code-challenge/blob/main/control_structure_examples/07-factory-functions.js)

