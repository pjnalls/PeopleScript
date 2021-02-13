<h1 align="center"><b>PeopleScript</b></h1>
<br>
<br>
<p align="center">
  <img src="ps.png" width="120px"/>
</p>
<br>
<h3 align="center">Documentation for understanding JavaScript meticulously.</h3>
<br>
<br>
<hr>

## `var` Statements for Variable Declarations

```javascript
//
//  var-statements.js
//

'use strict';

/* This is a globally-scoped variable declaration. */ 
var beverage = "unsweetened tea";

console.log(beverage); // => unsweetened tea

if (beverage === "unsweetened tea")
{
  /* 
    This is another globally-scoped variable declaration,
    but it will not override the first declaration of 
    the variable "beverage".
  */ 
  var beverage; // !== undefined
  
  console.log(beverage); // => unsweetened tea

  /* 
    This is also another globally-scoped variable 
    declaration, but it overrides the first declaration of
    the variable "beverage" due to the "=" assignment 
    operator.
  */
  var beverage = "water";

  console.log(beverage); // => water
}

function chooseDifferentBeverage() {
  /* 
    This is a function-scoped variable declaration. Therefore,
    this "beverage" variable may only be used within this block
    of the current function.
   */ 
  var beverage = "coffee";
  console.log(beverage);
}

function chooseSameBeverage() {
  /*
    The globally-scoped variable "beverage" will be referenced
    since there isn't a function-scoped variable of "beverage"
    defined in this block.
  */
  console.log(beverage);
}

function chooseNoBeverageThenCoffee() {
  /*
    
    The output for the code of this function-block might lead to some
    confusion because of the apparent "hoisting" process which occurs. 
    Therefore here is what I think happens during the Just-in-time (JIT)
    compilation process.

    1. A function-scoped variable "beverage" is declared but remains undefined.
    2. That "beverage" is hoisted to the top of this function block.
    3. Since the assignment operation doesn't occur before or during 
      the hoisting process, the console prints "undefined".
    4. "beverage" is then assigned a value of "coffee".
    5. Finally, the console prints "coffee".
  
  */
  console.log(beverage);
  var beverage = "coffee";
  console.log(beverage);
}

chooseDifferentBeverage(); // => coffee
chooseSameBeverage(); // => water
chooseNoBeverageThenCoffee(); // => undefined
                              //    coffee

console.log(beverage); // => water


```