# Ways to Create Object
* Object literal (mostly used)
* `new Object`  Object constructor
* Function constructor (Function converted to Object prototype)
* Object.create()  (not really used)


## Object literal

#### list of key : value pairs inside { }
```JavaScript
var student = {firstName:"Urmila", lastName:"Patel", rollNo:50 };
```
## Object Constructor
```JavaScript
var student = new Object();
student.firstName  = "Urmila";
student.lastName = "Patel"; 
student.rollNo = 50;
```
## Constructor function (not really favored)

Write a normal function use `this` keyword to read parameter as this will be converted to object. Create object using `new` keyword and call the function.
Create method using `.prototype` on the function and give the name of method and define it.
```JavaScript
function Student(firstName, lastName, rollNo) {   //object constructure function
  this.firstName = firstName;
  this.lastName = lastName;
  this.rollNo = rollNo;  
}  

Student.prototype.getName = function (){
    return this.firstName;
} //adding method using `.prototype`

var student1 = new Student("Urmila","Patel",50); // student1 is object(instance of student) created using `new` keyword and calling constructure function.
```
## Object.create() 

```JavaScript
let student = {
  firstname: 'Urmila',
  roll_no : 67
}

let student1 = Object.create(student);

student1.lastname = 'Rai'; 
student1.roll_no = 34;

console.log(student1);             //overwrite inherated property roll_no 
console.log(student1.firstname);
console.log(student);              // lastname does not get added to student object
```
**Output**
```
{ lastname: 'Rai', roll_no: 34 }     
Urmila                               
{ firstname: 'Urmila', roll_no: 67 } 
```
## Creating Inheritance in Javascript
```JavaScript
function Person(firstName,lastName) { 
   this.firstName = firstName;
   this.lastName = lastName;
}  

function Student(rollNo) { 
  this.rollNo = rollNo;  
}  

Student.prototype.__proto__ = new Person("Urmila","Patel"); //student has inherit property of person

var student1 =  new Student(50); 
var student2 =  new Student(50); 
console.log(student1); // Student { rollNo: 50 }
console.log(student1.firstName); //Urmila
```

## Behaviour of `this` keyword in different context.

* current object(nearest parent scope) in methods(a function attach to object key is a method).
* global object when used alone
* in functions `this` refers to global object.

In ES5 if method is directly attached to object key then  `this` refer to current object if not `this` refer to global object.

In ES6 in arrow function `this` keyword holds the scope of it's nearest parent.

```JavaScript
var student = {
    'first Name':"Urmila",                    
    lastName:"Patel", 
    rollNo:50,
    getdetail: function(){ //method
        return this;  // current object
    }, 
    getdetail1: function(){   //is a method
      return function(){      // is a function
        return student;  // static reference [use static reference to avoid confusion.]
      };  // current object
    },
    getdetail2: function(){   
      return function(){      
        return this;
      };  // global object
    },
    getdetail3: function() { // this => student object
      return () => {   
        return this; // current object 
      };  
    }
}

var detail = student.getdetail();
console.log(detail);

var detail1 = student.getdetail1();
console.log(detail1());

var detail2 = student.getdetail2();
console.log(detail2());

var detail3 = student.getdetail3();
console.log(detail3());
```

## Accessing properties and methods of Objects

* Key:Value pairs - properties of object. 
* Keys are always strings.
* Methods are action that can be performed on the object created as function definitions.
* use bracket notation when key name contain space or hyphen.

```JavaScript
var student = {
    'first Name':"Urmila",                    
    lastName:"Patel", 
    rollNo:50,
    getRollNo : function() {    //a function attach to object key is a method.
              return this.rollNo;  //current object(student)
            },
    getRollNo1 : function() {    //method
              return student.rollNo;  //static reference, cyclic reference(object referencing itself)
            },
}

console.log(student['first Name']); //Urmila   [bracket notation]
console.log(student.lastName); // Patel
console.log(student.getRollNo()); // 50
console.log(student.getRollNo1()); // 50
```

## Object static Methods

* ### Object.keys() 
returns array with all the keys of object.
* ### Object.values()
returns array with all the values of object.
* ### Object.assign() 
create `copy` all primitive values but non-primitive are still pass by reference.

**Note :**  .keys() and values() returns array.

```JavaScript
const student = {
  'first Name':"Urmila",                    
  "lastName" :"Patel", 
   rollNo:50,
    getRollNo : function() {
            return this.rollNo;
          },
   subjects : ['Science', 'English']
}

let student1 = Object.assign({}, student); //dereference the object.
student1.rollNo = 45;
student1.subjects.push('French');
console.log('Keys :' ,Object.keys(student));
console.log('Values : ',Object.values(student));
console.log('\n',student.rollNo,student1.rollNo); // does not change both object
console.log(student.subjects,student1.subjects); //  non-primitive values are changed in both object
```


**Output :**
```
Keys : [ 'first Name', 'lastName', 'rollNo', 'getRollNo', 'subjects' ]
Values :  [
  'Urmila',
  'Patel',
  50,
  [Function: getRollNo],
  [ 'Science', 'English', 'French' ]
]

 50 45
[ 'Science', 'English', 'French' ] [ 'Science', 'English', 'French' ]
```


## **ES6 : spread operator `...`**

**Note :** use `...`(spread operator) every time you want to create copy of  non-primitive values in complex data structure.If not then will not create copy but will reference to same non-primitive value.

```JavaScript
const student = {
  'first Name':"Urmila",                    
  "lastName" :"Patel", 
   rollNo:50,
    getRollNo : function() {
            return this.rollNo;
          },
   subjects : ['Science', 'English']
}

let student1 = { ...student, subjects: [...student.subjects]}; //spread the student object // spread the subjects array into key subjects

student1.rollNo = 45;
student1.subjects.push('French');
console.log(student, student1)
```

```
{
  'first Name': 'Urmila',
  lastName: 'Patel',
  rollNo: 50,
  getRollNo: [Function: getRollNo],
  subjects: [ 'Science', 'English' ]
} {
  'first Name': 'Urmila',
  lastName: 'Patel',
  rollNo: 45,
  getRollNo: [Function: getRollNo],
  subjects: [ 'Science', 'English', 'French' ]
}
```
 
## **ES6 : Array Destructure and Object Destructure**

* destructure object : 
     * use exact same key names as in object that you want to destructure.
     * to rename key use `:` i.e <old_key_name>:<new_key_name>
     * (ES6) to apply default value if give key is not present in object you want to destructure i.e <key_name>=<default_value>,if key is present then this has no effect.
* destructure array :
     * supply name for every index value that you want.

**Note :** `Only one Rest Element can be present and it should always be the last element.[should not be in between otherwise it will throw error]`
```JavaScript

const student = {
  firstName:"Urmila",                    
  lastName:"Patel", 
   rollNo:50,
    getRollNo : function() {
            return this.rollNo;
          },
   subjects : ['Science', 'English', 'Physics', 'Chemistry']
}

let { firstName, lastName='Ravaria', rollNo:RollNo, ...rest} = student;  
let [a,b, ...remaning] = student.subjects;
console.log(firstName,lastName,RollNo,rest);
console.log('\n',a,b,remaning);
```
**Output**
```
Urmila Patel 50 {
  getRollNo: [Function: getRollNo],
  subjects: [ 'Science', 'English', 'Physics', 'Chemistry' ]
}

 Science English [ 'Physics', 'Chemistry' ]
```

## Spread and Destructure in function
* use empty object or empty array to avoid error in case if parameter(object,array) is not passed at time of function call
* spread and destructure works same in function also.

```JavaScript
const student = {
  firstName:"Urmila",                    
  lastName:"Patel", 
   rollNo:50,
    getRollNo : function() {
            return this.rollNo;
          },
   subjects : ['Science', 'English', 'Physics', 'Chemistry']
}
function spread({ firstName, ...obj } = {}){  // use {} or [] to prevent error if no parameter is passed
        firstName = 'Pooja';
        console.log(firstName,'\n',student.firstName, '\n',obj);
}

spread(student); 
```

**Output**
```
Pooja 
 Urmila
 {
  lastName: 'Patel',
  rollNo: 50,
  getRollNo: [Function: getRollNo],
  subjects: [ 'Science', 'English', 'Physics', 'Chemistry' ]
}
```