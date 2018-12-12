# ECMA Script 6

## Variable Identifiers

- ```let``` and ```const```
  - Both are block-scoped, variable identifiers
  - ```let``` is for variables with values that will change over time.
    - Best practice:  Use it inside of blocks denoted by ```{}```.
    - ```let``` vs ```var```: Leave var in legacy code to denote that the variable needs to be carefully refactored.
  - ```const``` is for variables that cannot be reassigned.
    - e.g. ```const = 3.14 // Value of Pi cannot change.```

---

## Template Literals

- Template Literals
  - Backtick character ``` ` ``` can be used to denote that a string lasts multiple lines.
  
- Interpolation
  - Enclosing a string with backticks ``` ` ``` will allow us to log variables directly into a string.
  - Syntax: console.log(`string ${varName1} string`)
  - e.g.
    ```javascript
    var name = "Pumpkin";
    console.log("My cat is named " + name + ".");
    
    // This is equivalent to:
    
    console.log(`My at is named ${name}.`);
    ```
- New lines do not need to be explicitly declared.
  - e.g.
    ```javascript
    var text = (
      "cat\n" +
      "dog\n" +
      "nickelodeon"
    );

    // This is equivalent to:

    var text = (
      `cat
      dog
      nickelodeon`
    );
    ```
    
- Template literals can accept expressions
  - e.g.
    ```javascript
    let today = new Date();
    let text = `The time and date is ${today.toLocaleString()}`;
    ```
---

## Destructuring

- Destructuring allows us to extract values from arrays and objects (even nested) and store them in variables with a more convenient syntax.
  - Arrays
    - e.g.
      ```javascript
      // ES5
      
      var arr = [1, 2, 3, 4];
      var a = arr[0];
      var b = arr[1];
      var c = arr[2];
      var d = arr[3];
      
      // ES6
      
      let [a, b, c, d] = [1, 2, 3, 4];
      console.log(a); // 1
      console.log(b); // 2
      
      // This is equivalent to a, b, c, d = 1, 2, 3, 4 in Python
      ```
  - Objects
    - e.g.
      ```javascript
      // ES5
      
      var luke = {occupation: "jedi", father: "anakin"};
      var occupation = luke.occupation; // "jedi"
      var father = luke.father; // "anakin"
      
      // ES6
      
      let luke = {occupation: "jedi", father: "anakin"};
      let {occ, dad} = luke;
      
      console.log(occ); // "jedi"
      console.log(dad); // "anakin"

---
      
## Functions

- Arrow Function
  - An arrow function expression has shorter syntax than a traditional function expression and does not have
    - ```this```
    - ```arguments```
    - ```super```
    - ```new.target```
  - Utility
    - Arrow functions are used for non-method functions and cannot be used as constructors.
    - There is no binding of arguments
  - Syntax
    ```javascript
    (param1, param2, ..., paramN) => {statements}
    ```
  - e.g.
    ```javascript
    var materials = [
      'Hydrogen',
      'Helium',
      'Lithium',
      'Beryllium'
    ];

    console.log(materials.map(material => material.length));
    // expected output: Array [8, 6, 7, 9]
    ```

- JavaScript ```this``` vs Python ```self```
  - Python ```self```: An instance of the current object in the class method.
  - JavaScript ```this```: Current execution context of a function.
  
- JavaScript inherently supports prototype-based object-oriented programming
  - ES6 has updated the OOP syntax to more closely follow other class-based OOP
  - e.g.
    ```javascript
    // ES5
    
    function getType() { // doesn't work in ES6
      setTimeout(function () {
        console.log('Type is: ' + this.type);
      }, 500);
    }
    
    // ES6
    
    function selfGetType() {
      var self = this;
      setTimeout(() => {
        console.log('Type is: ' + self.type);
      }, 500);
    }
    ```
    - ```this``` becomes replaced with ```self```
    
- Default Parameters
  - ES5
    ```javascript
    function addTwoNumbers(x, y) {
      x = x || 0;
      y = y || 0;
      return x + y;
    }
    ```
  
  - ES6
    ```javascript
    function addTwoNumbers(x=0, y=0) {
      return x + y;
    }
    addTwoNumbers(2, 4); // 6
    addTwoNumbers(2); // 2
    addTwoNumbers(); // 0
    ```
    
- Rest Parameters
  - If a function has an indefinite amount of arguments, we can use the ```...args```
  - ES5
    ```javascript
    function logArguments() {
      for (var i=0; i < arguments.length; i++) {
          console.log(arguments[i]);
      }
    }
    ```
  - ES6
    
    ```javascript
    function logArguments(...args) {
      for (let arg of args) {
          console.log(arg);
      }
    }
    ```
---
    
## Classes

- Prior to ES6, "classes" were implemented by creating a constructor function and adding properties by extending the prototype:
  - ES5
    ```javascript
    
    ```