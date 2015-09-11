# JavaScript Coding & Best Practices Style Guide


## Table of Contents

  1. Naming of variables, functions, ...
  2. Conditions for if, while, ...
  3. Check parameters
  4. Comment where a comment is needed
  5. Provide variables with default values
  6. Replace switch case by a table
  7. Avoid anonymous functions
  8. Crash Early
  
### 1 Naming of variables, functions, ...
#### What
Name variables, functions etc. as specific as possible.
  
#### Why
This improves the readability of your code for you and other people.

#### Bad
  ```javascript
  function find(id) {
  }
  ```
  
#### Good
  ```javascript
  function findCustomer(customerId) {
  }
  ```

### 2 Conditions for if, while, ...
#### What
Create boolean variables to name conditions in if, while, ....
  
#### Why
This improves the readability of your code for you and other people.

#### Bad
  ```javascript
  if (index > 0 && index < maxLen && person.age > 18) {
  ```
  
#### Good
  ```javascript
  var isPersonAdult = person.age > 18;
  var isIndexValid = index > 0 && index < maxLen;
  if (isIndexValid && isPersonAdult) {
  ```
### 3 Check parameters
#### What
Because JavaScript allows you to call a function with any parameter, it seems to be a good practice to check these.
  
#### Why
Ignoring or simply returning hides errors. 

#### Bad
  ```javascript
  function addCustomer(customer) {
    if(!customer) {
      return;
    }
  ```
  
#### Good
  ```javascript
  function addCustomer(customer) {
    console.assert(customer, 'customer not given');
    console.assert(customer instance of Customer, 'no costumer object given');
  ```

### 4 Comment where a comment is needed
#### What
Don't bore with comments that are obious, instead comment the not so obvious things.

#### Why
Boring demotivates and secrets decreses consciousness power. Always ask yourself: Is this really obvious or could it be misunderstood?

#### Bad
  ```javascript
  //sets customerId to '4'
  var id = '4';
  ...
  scope.tabIndex = (value) ? "-1" : "0";
  
  ```
  
#### Good
  ```javascript
  var customerId = '4';
  ...
  //ignore control during tabbing if disabled (-1), or handle tabbing in source order (0) otherwise
  scope.tabIndex = (disabled) ? "-1" : "0";
  
  ```
  
### 5 Provide variables with default values.
#### What
Sometimes I find code that has to check if a variable is defined and if not it is initialised with i.e. an empty array.

#### Why
You have to write additonal code to check the variable each time you want to use it.

#### Bad
  ```javascript
  var selectedCustomerIds;
  ...
  if (!selectedCustomerIds) {
    selectedCustomerIds = [];
  }
  selectedCustomerIds.forEach(...); 
  ```
  
#### Good
  ```javascript
  var selectedCustomerIds = [];
  ...
  selectedCustomerIds.forEach(...); 
  ```

### 6 Replace switch case by a table
#### What
If you are simply replacing one constant value through another constant value, it is easier to use a object for that.

#### Why
Makes your code simpler and faster.

#### Bad
  ```javascript
  var lockFlagText;

  switch (lockFlag) {
      case 'l':
          lockFlagText = 'Lost';
          break;

      case 'd':
          lockFlagText = 'Defect';
          break;

      case 'f':
          lockFlagText = 'Fired';
          break;

      case ' ':
          lockFlagText = 'Not locked';
          break;
  }
  ```
  
#### Good
  ```javascript
  var LOCK_FLAG_TEXTS = {'l': 'Lost', 'd': 'Defect', f: 'Fired', ' ': 'Not locked'};
  ...
  var lockFlagText = LOCK_FLAG_TEXTS[lockFlag];
  ```

### 7 Avoid anonymous functions
#### What
It is a common practice to use anonymous function declarations for defining a callback or something else. Try to avoid this and instead name each function explicitly.

#### Why
During debugging it is annoying to read anonymous function, because that does not help to understand what is going on.

#### Bad
  ```javascript
  var controller.setEventHandler( function () {
  }
  ```
  
#### Good
  ```javascript
  var controller.setEventHandler( function handleCustomerIdChangedEvent() {
  }
  ```
  
### 7 Crash Early
#### What
It's always a bad idea to silently catch exceptions or not executing a function when a given parameter is missing. You should have good arguments when doing so.

#### Why
Simply because you are hiding errors in using the function or executing code. This does not help to get your program free of errors and even worse hides the source of the problem poping up somewhere else.

#### Bad
  ```javascript
  function saveCustomer(customerEntity)  {
    if(!customerEntity) {
       return;
    }
    
    try {
      resource.update(customerEntity);
    }
    catch (e) {
      // statements to handle any exceptions
      logMyErrors(e); // pass exception object to error handler
    }
  }
  ```
  
#### Good
  ```javascript
  function saveCustomer(customerEntity)  {
    console.assert(!customerEntity, 'customerEntity not given.');
    ...
    try {
      resource.update(customerEntity);
    }
    catch (exception) {
      console.log(exception);
      throw exception;
    }
  }
  ```

