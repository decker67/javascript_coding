# JavaScript Coding & Best Practices Style Guide


## Table of Contents

  1. Naming of variables, functions, ...
  2. Conditions for if, while, ...

### 1 Naming of variables, functions, ...
  #### What
  Name variables, functions etc. as specific as possible.
  
  #### Why
  This improves the readability of your code for you and other people.

  #### Bad
  ```javascript
  function find(id) {
  }
  ...
  
  #### Good
  ```javascript
  function findCustomer(customerId) {
  }
  ...

### 2 Conditions for if, while, ...
  #### What
  Create boolean variables to name conditions in if, while, ....
  
  #### Why
  This improves the readability of your code for you and other people.

  #### Bad
  ```javascript
  if (index > 0 && index < maxLen && person.age > 18) {
  ...
  
  #### Good
  ```javascript
  var isPersonAdult = person.age > 18;
  var isIndexValid = index > 0 && index < maxLen;
  if (isIndexValid && isPersonAdult) {
  ...
