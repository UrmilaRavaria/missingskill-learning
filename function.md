# Functions
* In JavaScript everything is an object, function are also an object.
* Whatever defined inside a function remains inside that function only cannot be accessed from outside of that function. If we want to access it then we have to return it from that function.

## Defining and Calling  a function
```JavaScript
function function_name(){

} //function declaration.

function_name();//calling a function to execute it.
```
`ES5 : benaviour of function is as variable.`
* container
* hoisted- you can call a function before you define a function. 
* scoped - local & global
* object - function can also be a object 
* override - if you re-define function again it keep the new/latest defination of that function.

**Good pratice :**  while calling a function safe guard function call as below.
```JavaScript
!!function_name && (typeof function_name === 'function') && function_name();
function function_name(){
}
```
```
!!function_name - to make sure that function_name is defined
(typeof function_name === 'function') - to make sure that it is function
function_name() - only then execute the function call.
```
## How things defined inside function work.
* 1st - check if variable is ES6(no hoisting) or ES5(for hoisting) if ES5(var) hoist it at top within the function where it is defined.
* 2nd - check in current lexical scope
* 3rd - check in nearest lexical scope
* 4th - check in local functional scope 
* 6th - check in nearest parent scope.

<br>

## Function with parametes.

* Instead of localize a varable we pass it as parameter.
* Varable passed as parameter are local to function changes to it does not affect global value of that varable.
* if varable 
    * premitive type - pass/copy by value. 
    * non-premitive type - pass/copy by reference. 
* We should make sure that we pass copy of varable in case of non-premitive.

```JavaScript
para1 = 10; 

function function_name(para1){
    console.log(para1); 
} 
function_name(para1); // pass as parameter

//  Is same as

function function_name(){
    var para1 = 10; // localize global varable.
    console.log(para1);
} 
function_name();
```
We should make sure that when we pass non-premitive as paramater we individually copy value of primitive.

## **Two ways for declaring a function**
### **1. function declaration**(single entity) : 
always start with `function` keyword,declaration gets hoisted, define a function with a name.
```JavaScript

declaration();

function declaration(){  
console.log("Still works.")
}
```

### **2. function assignment** (define a function then assign it to variable)/function expression : 
assignment doesn't get hoisted - varable declaration get hoisted(dependent on var, let, const) not defination.

**function expression:** if `function` appear anywhere in middle of statement is a function expression.
<br>

**Benefit :** multiple variable can point to same function.
```JavaScript
//classes(); //TypeError: classes is not a function
//classes && (typeof classes === 'function') && classes(); // not throw error but does not execute the function. Use when calling function before defination.
var classes = function(standard,div,count){
return {
  class: standard,
  division : div,
  no_students : count
   }
};

classes();
var class_10_A = classes(10,'A',45); //points to same function as classes
console.log(class_10_A); //{ class: 10, division: 'A', no_students: 45 }

var class_9_D = classes(9,'D',65);
console.log(class_9_D); //{ class: 9, division: 'D', no_students: 65 }

var class_5_C = classes(5,'C',56);
console.log(class_5_C); //{ class: 5, division: 'C', no_students: 56 }
```
* Functions are `First class citizen` i.e have first class nature(can do anything).
  * can be an object.
  * can be value in array.
  * Can be `assigned to variable`
  * Can also `return another function` , if no variable or value is returned from function it returns `undefined`.
  * Can be `pass as parameter`, if we don't pass argument while calling a parameterized function then by default is `undefined`.

## **Higher order function(concept) :**
function takes function as parameter and/or return function.

## **Pure Function(concept) :**
we don't update value of input parameters within the function. If we want to perform operation on input parameter the copy them into other variable and the use this variable instead.

**Good pratice:** Try to write pure function 

**Example :**
```JavaScript
var price = 250;
function theatre(){ //higher order function as it returns a function(ticket)
    var ticket = function(cash){ //pure function.
        return {movie: 'Avengers',
        duration : 2.5,
        seat_no : 25,
        price : cash
        }
    }
    return ticket; //function return a function so it can be accessed from outside.
}

var person = theatre(); //function assign to variable 
var check_ticket = person(price); 
console.log(check_ticket); // movie: 'Avengers', duration: 2.5, seat_no: 25, price: 250 }
```
## **Function passed as parameter :**
**Example :**
```JavaScript
function greeting(name){
    return `Hi, ${name}`;
}

function body(greet){
    let fn_local;

    if(greet && (typeof greet === 'function')){
      fn_local = greet;   // fn_local is pointing to greeting function.
      var message = fn_local('XYZ'); // geeting function takes a parameter so.
      var final = `${message} greet function is passed as parameter`;
      return final;
    }else{
        fn_local = function(){
        }
    }
}

var email = body(greeting); //function passed as parameter //higher order function
console.log(email); // Hi, XYZ greet function is passed as parameter
```

**Good Pratice :** If function is passed as parameter check function and also create empty function incase if function is not passed as parameter.

## **Function short circuit/ castcading function :** 
Whenever function returns a function we can immideatly invoke the returned function using `()` without assigning to variable.

**Nested function :** function inside another function, which also forms a `closure`.

**Closure :** encuplation,inner function can access variable and parameter of outer function even after outer function  has completed execution,remembers it's environment.

**Example :**
```JavaScript
function class_eight(marks_8){
    function class_ninth(marks_9){
        function class_tenth(marks_10){
            return `${marks_8} in 8th \n ${marks_9} in 9th \n ${marks_10} in 10th Congrulations!!` //closure: this function can access arguments and variable of it's parents function.
        }
        return class_tenth;
    }
    return class_ninth;
}

var pass_eight = class_eight(87.35);
var pass_ninth = pass_eight(89.50);
var pass_tenth = pass_ninth(91.78);

console.log('Pass_tenth :',pass_tenth); /*
                                           Pass_tenth : 87.35 in 8th 
                                           89.5 in 9th
                                           91.78 in 10th Congrulations!!
                                        */

var final = class_eight(87.35)(81.50)(90.79);

console.log('Final :',final);      /*
                                    Final : 87.35 in 8th 
                                    81.5 in 9th
                                    90.79 in 10th Congrulations!!
                                   */
```


## **Immediately invoked function(IIFE)/Self executing function(SEF)**: 
function can act like private method,if we want function to be executed only once we use iife and then it's return value can be assing to variable. first part of iife is a `function expression: (function(){})`, second part invokes iife `()`, use `;` at start of iife to safe guard code.

**Example :**
```JavaScript
function login(name){
;(function(date){  // gets executed only if login function is called 
 let format = `date:${date.getDate()}-${date.getMonth()}-${date.getFullYear()} time:${date.getHours()}:${date.getMinutes()}:${date.getSeconds()}`;
    function log_file(){    //there is now way we can call this function without calling login.
        console.log(`User ${name} logged in at ${format}`);
    }
    log_file()
})(new Date());
}

var log = login('Urmila'); //User Urmila logged in at date:21-4-2021 time:16:51:50
```

## **Inline function :**
Used if we don't want to expose function outside, always function expression and anonymous function.

inline parameter/value : directly pass value.

**Example :**
```JavaScript
let email = (function(greet){
    
    function body(name){
        let final = !!greet && (typeof greet === 'function') && greet(name);  
        return final;
    }

    return body;
})(function(name){               //inline function, anonymous function
    return `Hi, ${name}`; 
});

let person1 = email('Urmila');
console.log(person1); //Hi, Urmila
```

## **ES6 - Arrow function :**
* does not have its own context.
* always function experssion or assignment => does not get hoisted 
<!-- * solved the problem of scope leaking. -->
* `this` keyword refer to nearest parent scope.
* if arrow function has `only one` statement inside it the you can remove the `{ }`
* you can omit parentheses only if you have exactly one parameter passed to arrow function.In all othere cases you have to have parentheses.

**Example :**
```JavaScript
var final1 = para1 => console.log(para1);
final1("Hi, there this much shorter syntax");

// Is same as below

var final = function(para1){
return console.log(para1);
};
final("Hi, there");
```
**Example :**
```JavaScript
var final = {
getPara1 : function(){
return {
    inner : function(para1) {
        this.para1 = para1;
          return () => {
                    console.log(this.para1); // `this` holds the scope of inner function(nearest parent).
                 }
            }
        }
    }
}
final.getPara1().inner("Hi, there")();
```