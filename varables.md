# JavaScript Tech debt:
* `+` : used for both addition and concatenation. It concates values if any one operand is string eg:  167 + "null" => "167null", [2,3,4] + "Hello" => "2,3,4Hello"

* `==` : only check value of number not datatype eg: '1' == true => true, "24" == 24 => true. 
So `===`(equality check) was introduced which  checks the datatype first and then checks value eg '1' === true => false , "24" === 24 => false. `1. it checks datatype => match => 2. check values.`

* typeof(null) => object : ideally it should return null by it returns object.

**Note :** use `+` or concatnation only with primitive type to be safe. Because when used with non-primitive type it may give unexpected result.


# Variable
JavaScript dynamically typed languages. Everything is object in javascript.Variables are container that stores data.

Declaring variable name rules i.e identifiers
* it should always start with letter (a to z OR A to Z), underscore( _ ), dollar ( $ )
* can have numbers, letters, or symbol like '_' and '$'
* reserved words, cannot be used as variable name.
* they are case sensitive

**Examples :**

```JavaScript
var test1 = 'ok'
var user_name = 'Urmila'
var 1test = 'Error' // error 
```

**Good pratice :**
* name variables in lowercase, if have multiple words use `camelCase` naming 
* use underscore ( _ ) for private variable 
* name `const` variable that are hard coded or who's value won't change using capital letters

```JavaScript
var greet = 'Hi';
var userName = 'Urmila'; //camelCase each word except first starts with a capital letter
var _getUser ;
var HOURS = 24;
```

## Scope 

### Scope of variable is the protion in program where it is defined.
* **Functional Scope** : each program or application  can be called as functional scope(global functional scope). And each function within program  have their own functinal scope(local functional scope) which exist untill the function exists. `var` keyword has functional scope
    * **global  variable** :global variables are variables defined outside of functions,can be used by any functions and anywhere.
    * **local  variable** : local variables defined within functions,can only be used within that function in which they are defined its scope exist only within that function not outside of that function.
* **Lexical Scope/Block Scope** : starts and end with curly braces `{ }`also called block is lexical scope/block scope. Any variable that exist only inside curly braces `{ }` has lexical scope.`let` and `const` have lexical scope.

**Note :** Within function,local variable overrides a global variable with the same name.

**Good pratice:** Use local variable whenever possible.

## Datatype 
Any datatype variable can be created using two ways

* using literal notation
* using Built-in Constructor/Object prototype.
    * They are object representation of primitive and non-prmitive type.
    * variable using this can be created using `new` keyword followed by name of Built-in Constructor like
    ```JavaScript
    var str = new String("This is String Object");
    ```
    this creates variable of string object and `typeof()`
    this variable is `object`.

**Note :** creating variable using Object prototype is not favored because in some cases opeartion variable create unexpected output.

**Note :**
any variable primitive or  non-primitive when we add `( . )` after variable name it converts it into it's respective prototype object and then you can use all the property defined for that prototype object.

###  Primitive type :  
are pass/copy by value, they conatin only single type of value i.e if variable is of string primitive type then it can hold only one value which should be string.

* ### string
  * anything enclosed in quotes is string.
  * **string :(ES6)-backticks allow to embed variable into string by wrapping variable inside `${<variable_name>}`**
```JavaScript
var message = "Hi";
var str1 = 'This is a     String   ';
var str2 = 'This is   String2'
var str3 = 562776890
var useBackTicks = `${message}, ${str1}`; //Hi, This is a String
console.log(typeof(useBackTicks)); //string


var str = new String("This is string created using String Object");
console.log(str, typeof(str)); // [String: 'This is string created using String Object'] object

//convert to lowercase(normalize)
console.log(str1.toLowerCase()); // this is a     string   

//convert to uppercase(normailze)
console.log(str1.toUpperCase()); // THIS IS A     STRING

//convert to string
console.log(str3.toString(), typeof(str3.toString())); // 562776890 string

//split string with specified delimiter [returns array] [opposite of join in array] 
console.log(str2.split('i')); // [ 'Th', 's ', 's   Str', 'ng2' ]

//replace the 1st parameter with 2nd parameter [only 1st occurence is replaced]
console.log(str2.replace('i','$')); // Th$s is   String2

//gives substring from specifed indexes.
console.log(str2.substr(5,9)); // is   Stri

//trims spaces from two ends of string [not from between] [works only on string]
console.log(str1.trim()); // This is a     String
```
```JavaScript
 var str1 = "This is string created using string literal"   
 
 console.log(String(str1).toLowerCase()); //this is string created using string literal 

 //Is same as below.

 console.log(str1.toLowerCase()); //this is string created using string literal  // internally it does [new String(str1)]
```

**Good pratice :** use `.toString()` as below before using any String method on variable to avoid error.
```JavaScript
console.log(str3.toString().split(8)); //[ '562776', '90' ]  [function chaning]
```

* ### number
```JavaScript
var age = 18;
console.log(age); //18
console.log(typeof(age)); //number

var num = new Number("12");  //Using Number Object/Number constructor

 console.log(num, typeof(num)); //[Number: 12] object
```
* ### boolean : two posssible values `true` or `false`
```JavaScript
var isChecked = true;
console.log(age); // true
console.log(typeof(isChecked)); //boolean

var bool = new Boolean("12");  //Using Boolean Object/Boolean constructor
 console.log(bool, typeof(bool)); //[Boolean: true] object
```
* ### undefined - meaning “value is not assigned”
if variable is declared but not assigned a value or defined that is of `undefined` type.
```JavaScript
var age; 
console.log(age);  // undefined
console.log(typeof(age)); // undefined
```
**Note :** We can assign undefined to variable but is not recommend doing, `undefined` is use internally by javascript engine. Use `null` to assign an “empty” or “unknown” value.

* ### null - represents “nothing”, “empty”  
```JavaScript
var age = null;
console.log(age); //null
console.log(typeof(age)) //object [Tech dea]
```
## Type cast : Easy way
* Number("100") => (+"100") //to number
* Boolean("hello") => (!!"hello") //to boolean

## Primitive type variable  are copy by value and pass by value.

meaning if we copy or pass primitive variable they copy or pass the actual value/data that they hold or is inside them.

```JavaScript
var student1 = 'urmila'
var student2 = student1;
console.log('student1 : ',student1); //student1 :  urmila
console.log('student2 : ',student2);//student2 :  urmila

student1 = 'pooja'; // update value
console.log('student1 : ',student1);//student1 :  pooja 
console.log('student2 : ',student2);//student2 :  urmila   //does not get updated

function student(name){
    console.log('student1 : ',name);//student1 :  pooja   //actual value is passed.
}

student(student1);
```



## Non Premitive type 
can be a collection of primitive and non-primitive, and are pass/copy by reference. i.e
if a variable is of non-primitive type can hold many values which can be of different datatype.

* ### objects - {key1:value1,key2:value2 }
```JavaScript
var userName = {firstName: 'Urmila', lastNam: 'Patel'};
console.log(userName); // { firstName: 'Urmila', lastNam: 'Patel' }
```

* ### arrays - [value1, value2]
```JavaScript
var students = ['Urmila','Sonali','Meghana'];
console.log(students); // [ 'Urmila', 'Sonali', 'Meghana' ]
```
## Non-primitive type variable  are copy by reference and pass by reference.

meaning if we copy or pass non-primitive variable they pass or copy reference not the actual data that you may think is inside them. Because non-primitive variable does not store actual data itself but  store pointer to a address where actual data is stored.

**Example :**

object are non-primitive so when we copy one object into another as below it does not copy actual data but copy of reference address,because non-primitive variable store reference to actual data not the data itself. So both variable point to same memory location which has actual data.

```JavaScript
var student1 = student; //student will also point to same memory location as student does;
```
student1 is not copy of student. student1 and student both are same object change in student1 will change student.

```JavaScript
var student = {firstName:"Urmila", lastName:"Patel", rollNo:50 };
var student1 = student;
student1.gender = 'Female'; // adding key in student1.
console.log(student1);
console.log(student);
```
 
**Output :**
```
{
  firstName: 'Urmila',
  lastName: 'Patel',
  rollNo: 50,
  gender: 'Female'
}
{
  firstName: 'Urmila',
  lastName: 'Patel',
  rollNo: 50,
  gender: 'Female'       // student also gets updated.
}
```
adding new key in student1 also addes new key in student.

## Logical Operator:

### `&&` : 
evaluates untill it's (truthy value)true and stops when (falsy value)false is encountered, `results into false even if any one value is evaluated to falsy or false.`
### `||`: 
evaluates untill it's (falsy value)false and stops when (truthy value)true is encountered, `results into true even if any one value is evaluated to truthy or true.`
### `!` : 
can be used as boolean converter,it negates the value. i.e is exp1 is true !(exp1) => false and if we negate it again i.e !!(exp1) => true.

### Truth Table:

#### NOT 
| exp1 | NOT |
|------|-----|
| true | false|
| false| true|

#### AND & OR            
| exp1 | exp2 | AND | OR |
|------|------|------|----|
| true | true | true | true|
| true | false| false| true|
|false | true | false| true|
|false | false| false| false|



 **Falsy Value :**
 Boolean: false, String : "", Number : 0, NaN, undefined, null.

 **Truthy Values :**
 Object : { } , Array : [ ] - even an empty object and empty array are truthy because even if they are empty they are allocated space inmemory.

 Boolean : true, String : all non-empty string are truthy, Number : all numbers except (0 and NaN) are truthy even negative number is truthy.


**Note**: Whenever we perform logical operations or conditional check javascript convert variable in boolean value and then evaluate accourding to truth table.
conditions are evaluated to either `true or false`

## Arithmatic operator:
#### `*,-,/,%,++,--,+`

* undefined `+` any primitive datatype(except string) results into NaN(not a number)
* string `+` any primitive datatype results into string i.e other datatype is type casted into string and then it concates the values.
* number `+,*,etc` any primitive datatype(except string and undefined) results into number i.e other datatype is type casted into number and then it performs opeartion on that  values.
boolean: true - 1, false - 0, null - 0

## Assignment operator:
#### `=,+=,-=,*=,/=,%=`

## Comparison operator
#### `===,==,!=,>,<,<=,>=`

## Ternary operator
#### `<condition>?<expression_if_true>:<expression_if_false>`
It can be use in replacement to `if else` statement, right assocative.

```JavaScript
let a = "dog"

if(a === "cat"){  // else if statement
     a = "meow";

 }else if(a === "pig"){
     a = "oing";
 }else{
     a = "bark";
 }

console.log(a); //bark

a = (a === "cat") ?  a = "meow": (a === "pig") ? a = "oing" : a = "bark"; // Ternary operator used to shoter the code. //same output

console.log(a); //bark 
```
## Creating Variables

### `var` :
* var (ES5) : can be redeclared and re-initalized, has functional scope, gets hoisted-declaration get's hoisted not assignment, get's hoisted only at functional scope.

```JavaScript
var outside = 'This is global var oustide of function';
var globalVar = 'Before calling the function';

function scopeOfVar(){
    var outside = 'This outside in the scopeOfVar()'; //reuse variable,localize variable.
    console.log(outside); //3//This outside in the scopeOfVar()
    globalVar = 'After calling the function override the global globalVar';
    console.log(inside);//4//undefined
    var inside = 'This is local var availabe only within scopeOfVar()';
    console.log(inside); //5 //This is local var availabe only within scopeOfVar()
}

console.log(globalVar); //1//Before calling the function
console.log(outside); //2 //This is global var oustide of function
scopeOfVar();
console.log(globalVar);//6//After calling the function override the global globalVar
console.log(inside); //7// ReferenceError: inside is not defined
```

### `let` :
* let (ES6) : cannot be redeclared and re-initalized, reassignmient is posssible, does not get hoisted, has lexical/block scope.

**Example :**
How Lexical scoping work. 

```Javascript
var a = true;
let b = null;
const c = 'lexical scope';

function lexicalScoping(){
if(a && b){
    let b = 'b declared in Current lexical scope';    // this b does not exist outside this if block .
    console.log('b override parent lexical scope :', b); // b overrid the b declared in global functional scope.
}else{
    b = 'lexical scope';
    console.log(' b in else blocK :', b); // this b value to b defined in global functional scope
    b = ' outside lexical scope of else'  // re-assign global varaiable.
}
console.log('b inside functional scope and:', b); // this b value to global variable value.
}

lexicalScoping();
lexicalScoping();
```
**Output**
```
b in else blocK : lexical scope
b inside functional scope and:  outside lexical scope of else        
b override parent lexical scope : b declared in Current lexical scope
b inside functional scope and:  outside lexical scope of else           
```

```JavaScript
let outside = 'This is global var oustide of function';
let globalVar = 'Before calling the function';

function scopeOfVar(){
    let outside = 'This outside in the scopeOfVar()';
    console.log(outside); //3//This outside in the scopeOfVar()
    globalVar = 'After calling the function override the global globalVar';
// Uncomment the next line to see error will not be able to see output 4 and 5 will stop here.

    // console.log(inside); //ReferenceError: Cannot access 'inside' before initialization

    let inside = 'This is local var availabe only within scopeOfVar()';
    console.log(inside); //4//This is local var availabe only within scopeOfVar()
}

console.log(globalVar); //1//Before calling the function
console.log(outside); //2// This is global var oustide of function
scopeOfVar();
console.log(globalVar);//5//After calling the function override the global globalVar
console.log(inside); //ReferenceError: inside is not defined
```

### `const`
* const (ES6) : cannot be redeclared ,re-initalized or reassignmient, does not get hoisted, has lexical/block scope.[const variables shuold always be initalized].

```JavaScript
const outside = 'This is global var oustide of function';
const globalVar = 'Before calling the function';

function scopeOfVar(){
    const outside = 'This outside in the scopeOfVar()';
    console.log(outside);  //1//Before calling the function
    globalVar = 'After calling the function override the global globalVar'; //TypeError: Assignment to constant variable.
     console.log(inside); 
    const inside = 'This is local var availabe only within scopeOfVar()';
    console.log(inside);
}

console.log(globalVar); //2//This is global var oustide of function
console.log(outside); //3//This outside in the scopeOfVar()
scopeOfVar();
console.log(globalVar);
console.log(inside); 
```

```JavaScript
const outside = 'This is global var oustide of function';
const globalVar = 'Before calling the function';

function scopeOfVar(){
    const outside = 'This outside in the scopeOfVar()';
    console.log(outside); 
    //globalVar = 'After calling the function override the global globalVar';

    // Uncomment next line to see this error.
    // console.log(inside); //ReferenceError: Cannot access 'inside' before initialization

    const inside = 'This is local var availabe only within scopeOfVar()';
    console.log(inside);
}

console.log(globalVar); 
console.log(outside); 
scopeOfVar();
console.log(globalVar);
const var; //1//will not excute the script// SyntaxError: Unexpected token 'var' // always initalize a const variable 
console.log(inside); 
```