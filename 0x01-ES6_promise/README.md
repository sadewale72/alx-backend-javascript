0x01. ES6 Promises
==================

JavaScriptES6

-   By Johann Kerbrat, Engineering Manager at Uber Works

![image](https://user-images.githubusercontent.com/106776383/232731806-5bd941fe-debc-4168-9633-dc030cad52dc.png)


Resources
---------

**Read or watch**:

-   [Promise](https://alx-intranet.hbtn.io/rltoken/j_0FTFbkTg42JMcAbNPOVQ "Promise")
-   [JavaScript Promise: An introduction](https://alx-intranet.hbtn.io/rltoken/2Q2LzNFokcUwpA2u3FKG6Q "JavaScript Promise: An introduction")
-   [Await](https://alx-intranet.hbtn.io/rltoken/UXb3S2PMBe-SLJ55isMcow "Await")
-   [Async](https://alx-intranet.hbtn.io/rltoken/_K0C7pgEjwaIzU9RpwCb8g "Async")
-   [Throw / Try](https://alx-intranet.hbtn.io/rltoken/UTjDgvKk5l892Xslh0vqcQ "Throw / Try")

Learning Objectives
-------------------

At the end of this project, you are expected to be able to [explain to anyone](https://alx-intranet.hbtn.io/rltoken/Z4xW7_BFaRcrHxfDySjKuQ "explain to anyone"), **without the help of Google**:

-   Promises (how, why, and what)
-   How to use the `then`, `resolve`, `catch` methods
-   How to use every method of the Promise object
-   Throw / Try
-   The await operator
-   How to use an `async` function

Requirements
------------

-   All your files will be executed on Ubuntu 18.04 LTS using NodeJS 12.11.x
-   Allowed editors: `vi`, `vim`, `emacs`, `Visual Studio Code`
-   All your files should end with a new line
-   A `README.md` file, at the root of the folder of the project, is mandatory
-   Your code should use the `js` extension
-   Your code will be tested using `Jest` and the command `npm run test`
-   Your code will be verified against lint using ESLint
-   All of your functions must be exported

Setup
-----

### Install NodeJS 12.11.x

(in your home directory):

```
curl -sL https://deb.nodesource.com/setup_12.x -o nodesource_setup.sh
sudo bash nodesource_setup.sh
sudo apt install nodejs -y

```

```
$ nodejs -v
v12.11.1
$ npm -v
6.11.3

```

### Install Jest, Babel, and ESLint

in your project directory:

-   Install Jest using: `npm install --save-dev jest`
-   Install Babel using: `npm install --save-dev babel-jest @babel/core @babel/preset-env @babel/cli`
-   Install ESLint using: `npm install --save-dev eslint`

Files
-----

### `package.json`

Click to show/hide file contents

### `babel.config.js`

Click to show/hide file contents

### `utils.js`

Use when you get to tasks requiring `uploadPhoto` and `createUser`.

Click to show/hide file contents

### `.eslintrc.js`

Click to show/hide file contents

### and...

Don't forget to run `$ npm install` when you have the `package.json`

Response Data Format
--------------------

`uploadPhoto` returns a response with the format

```
{
  status: 200,
  body: 'photo-profile-1',
}

```

`createUser` returns a response with the format

```
{
  firstName: 'Guillaume',
  lastName: 'Salva',
}

```

Tasks
-----

+ [x] 0. **Keep every promise you make and only make promises you can keep**<br/>[0-promise.js](0-promise.js) contains a script that exports a function with the prototype `function getResponseFromAPI()`, which returns a Promise.

---
+ [x] 1. **Don't make a promise...if you know you can't keep it**<br/>[1-promise.js](1-promise.js) contains a script that exports a function with the prototype `getFullResponseFromAPI(success)`, which returns a Promise. The parameter (`success`) is a `boolean`.
  + When the argument is:
    + `true`
      + Resolve the promise by passing an object with 2 attributes:
        + `status`: `200`
        + `body`: `'Success'`
    + `false`
      + Reject the promise with an error object with the message `The fake API is not working currently`.

---
+ [x] 2. **Catch me if you can!**<br/>[2-then.js](2-then.js) contains a script that exports a function with the prototype `function handleResponseFromAPI(promise)`, which appends three handlers to the `promise` argument.
  + When the Promise resolves, return an object with the following attributes:
    + `status`: `200`,
    + `body`: `'success'`
  + When the Promise rejects, return an empty `Error` object.
  + For every resolution, log `Got a response from the API` to the console.

---
+ [x] 3. **Handle multiple successful promises**<br/>[3-all.js](3-all.js) contains a script that meets the following requirements.
  + Import `uploadPhoto` and `createUser` from [utils.js](utils.js).
  + Use the prototype below to collectively resolve all promises and log `body firstName lastName` to the console. The functions in [utils.js](utils.js) return Promises.
  
    ```js
    function handleProfileSignup()
    ```
  + In the event of an error, log `Signup system offline` to the console.

---
+ [x] 4. **Simple promise**<br/>[4-user-promise.js](4-user-promise.js) contains a script that exports a function with the prototype `function signUpUser(firstName, lastName)`, which returns a resolved promise with the object shown below.

  ```js
  {
    firstName: value,
    lastName: value,
  }
  ```

---
+ [x] 5. **Reject the promises**<br/>[5-photo-reject.js](5-photo-reject.js) contains a script that exports a function with the prototype `function uploadPhoto(filename)`, which returns a Promise rejecting with an Error and the string `$fileName cannot be processed`, where `fileName` is a string.

---
+ [x] 6. **Handle multiple promises**<br/>[6-final-user.js](6-final-user.js) contains a script that meets the following requirements.
  + Import `signUpUser` from [4-user-promise.js](4-user-promise.js) and `uploadPhoto` from [5-photo-reject.js](5-photo-reject.js).
  + Export a function named `handleProfileSignup` that accepts three arguments `firstName` (string), `lastName` (string), and `fileName` (string) and calls the two other functions (`signUpUser` and `uploadPhoto`).
  + When the promises are all settled it should return an array with the following structure:
  
    ```js
    [
      {
        status: status_of_the_promise,
        value: value || reason // value or error returned by the Promise
      },
      ...
    ]
    ```

---
+ [x] 7. **Load balancer**<br/>[7-load_balancer.js](7-load_balancer.js) contains a script that exports a function with the prototype `function loadBalancer(chinaDownload, USDownload)`, which returns the value returned by the promise that resolved the first, where `chinaDownload` and `USDownload` are Promises.

---
+ [x] 8. **Throw error / try catch**<br/>[8-try.js](8-try.js) contains a script that meets the following requirements.
  + Exports a function with the prototype `function divideFunction(numerator, denominator)`, where `numerator` and `denominator` are numbers.
  + When the `denominator` argument is equal to 0, the function should throw a new error with the message `cannot divide by 0`.
  + Otherwise it should return the `numerator` divided by the `denominator`.

---
+ [x] 9. **Throw an error**<br/>[9-try.js](9-try.js) contains a script that meets the following requirements.
  + Export a function named `guardrail` that accepts a function argument called `mathFunction`.
  + The `guardrail` function should create and return an array named `queue`.
  + When the `mathFunction` function is executed, the value returned by the function should be appended to the `queue`. If this function throws an error, the error message should be appended to the `queue`.
  + In every case, the message `Guardrail was processed` should be added to the queue.

---
+ [x] 10. **Await / Async**<br/>[100-await.js](100-await.js) contains a script that meets the following requirements.
  + Import `uploadPhoto` and `createUser` from [utils.js](utils.js).
  + Export an async function named `asyncUploadUser` that will call the two functions imported above and return an object with the following format:
  
    ```js
    {
      photo: response_from_uploadPhoto_function,
      user: response_from_createUser_function,
    }
    ```
  + Import `uploadPhoto` and `createUser` from [utils.js](utils.js).
  + If one of the async function fails, return an empty object as shown below:
  
    ```js
    {
      photo: null,
      user: null,
    }
    ```
