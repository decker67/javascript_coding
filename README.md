# JavaScript Coding & Best Practices Style Guide


## Table of Contents

  1. Naming of variables, functions, ...
  2. Conditions for if, while, ...
  3. Check parameters

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
### Check parameters
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

