# JavaScript Coding & Best Practices Style Guide


## Table of Contents

  1. Naming of variables, functions, ...
  2. Conditions for if, while, ...
  3. Check parameters
  4. Comment where a comment is needed

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

### 3 Comment where a comment is needed
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
  //set a tabindex dependent from the value 
  //0 is handled in source order (the order it appears in the DOM)
  //-1 is ignored during tabbing but is focusable.
  tabIndex = (value) ? "-1" : "0";
  
  ```
