# **Arrays** 
* are a special type of objects. 
* Thus arrays use numeric key to access its "elements" we don't need to provide/define it,javascript does that for us.
* Same array can have variables of different types.

## **Ways to create Arrays**

### Array literal
```JavaScript
var students = ['Urmila','Sonali','Meghana', 50 , true];
```

### Array Constructor
```JavaScript
var students = new Array('Urmila','Sonali','Meghana');
```

## **Accessing array elements**

array index starts with 0
```JavaScript
var arr = [1,
  'name',
  function(a){  console.log(`Hi ,from ${a} element`)}, 
  null,
  { name : 'XYZ' , address : { line1: 'plot 1A', city : 'Mumbai'}}, //search Mumbai
  ['Hi','Everyone',[1,2,3]] // search 2
  ]; 

console.log(arr[1]); //name      
console.log(arr["1"]); //name  // arr["1"] is also valid because array is special kind of object.

console.log(arr[4]["address"].city) // Mumbai
console.log(arr[5][2][1]) // 2 

var greet = arr[2]
greet('third');  //Hi ,from third element 


arr[2]('third'); //Hi ,from third element   (pass parameter,direct call, same output as previous)

```


## **Length of array**

## length of array is `last index` + 1

```JavaScript
var students = ['Urmila','Sonali','Meghana', 50 , true]

console.log(students.length) //5

students[8] = 'Anuja';
console.log(students) //[ 'Urmila', 'Sonali', 'Meghana', 50, true, <3 empty items>, 'Anuja' ]
console.log(students.length) // 9 [last index + 1]

students[students.length] = [1,2,3]; // add element at end of array.
console.log(students) /* [
                           'Urmila',
                           'Sonali',
                           'Meghana',
                            50,
                            true,
                            <3 empty items>,
                            'Anuja',
                            [ 1, 2, 3 ]
                          ]*/
```



### Note : Arrays are a special kind of objects, with numbered indexes. In javascript length will only look for `numbered index` in case of arrays.
```JavaScript
var arr = [1,2,45,67];
console.log(arr.length); // 4
arr['hi'] = 678;  // valid because array is special kind og object. [but 'hi' is not a index.]
console.log(arr); // [ 1, 2, 45, 67, hi: 678 ]
console.log(arr.length); //4
arr[hi]; // error: hi is not defined. because hi is a string key.
```

**Good Pratice:**
* Use literal method to create array.
use [ ] instead of `new` Array().
* Use `push()` method for adding elements, adding elements using indexes can create `holes` in an array.

##  **Array methods**

```JavaScript 
var students = ['Urmila','Sonali','Meghana', 50 , true, "" , null];
var array2 = [1,2,function(){return 'Hi'}, {key1: 'greet', key2: 78}];

var new_array = students.concat(array2); // concat two array and returns new array.

console.log(new_array); 
/* 
[
  'Urmila',
  'Sonali',
  'Meghana',
  50,
  true,
  '',
  null,
  1,
  2,
  [Function (anonymous)],
  { key1: 'greet', key2: 78 }
]
*/

//Add an item at end of an Array.
let newStudents = students.push('payal'); // // pass item that you want to push.
console.log('newStudents :', newStudents);  //8

//Remove item from end of an Array and returns it.
let last = students.pop();
console.log('last :' , last); // last :payal

//Add an item to beginning of an Array
let newStudent1 = students.unshift('xyz'); // pass item that you want to add.
console.log('newStudent1:', newStudent1); //8

//Remove an item from beginning of an Array and returns it
let first = students.shift();
console.log('first :', first); //first : xyz

//Find the index of an item
let pos = students.indexOf('Sonali'); // pass item that you want to find
console.log('pos :', pos); //pos : 1

//Find if  an item is present in the Array returns true or false//ES6
let present = students.includes('Urmila');
console.log('present :', present); //present : true


//Conver array to string and specify the delimiter to join elements.
let str1 = students.join(" ") // uses space as delimiter
console.log('str1 : ',str1); //str1 :  Urmila Sonali Meghana 50 true

//To check if it is an array. 
let isArray = Array.isArray(students);
console.log(isArray);  //true
```
## **.forEach()**
### Loop over every element in an array and does not return undefined.
Takes function as parameter also called as callback function.And will execute this function on each item of array. 

```JavaScript
//Loop over an Array
students.forEach(function(item, index) {
  console.log(item, index)
});

/*
Urmila 0
Sonali 1
Meghana 2
50 3
true 4
 5
null 6
*/
```


## **.filter()**
### Iterates through all the items and based on condition returns the same length or less. Returns array of true cases.
Takes a callback function as parameter.Which can be inline function or normal function.
```JavaScript
const arr1 = [2, 8, 9, 20, 15];
const areEven = arr1.filter(function(item){  // inline function to filter method
  return item % 2 == 0;
})

console.log(areEven);
```
**Output :**
```
[ 2, 8, 20 ]
```

## **.map()** (transforming array)
### Iterates through all the items and returns the new array with same length. 
change value i.e perform the operation on array item  and return it. `.map()` takes function and index as parameter and perform operation in that function on each element. function can also be passed as inline function in `.map()` method.

```JavaScript
var user = [{
  name : 'urmila',
  date : 18,
  month : 1,
  year : 1999
},
{
  name:'meghana',
  date: 23,
  month: 7,
  year: 1995
}];


var generate = function(item){
     return `${item.name}_${item.date}_${item.year}`;
}
const user_name = user.map(generate); //can also have inline function
console.log(user_name);
```
**Output**
```
 [ 'urmila_18_1999', 'meghana_23_1995' ]
```


