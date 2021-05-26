## Timer Function

* `setTimeout()` - delay code by given time.
```JavaScript
const washing_machine = function (){
    setTimeout(function(){
console.log(`Washing Machine turned off after 3 seconds`);
},3000);
}

washing_machine(); // after 3 sec will print //Washing Machine turned off after 3 seconds
```

* `setInterval()` - the function given as parameter is run repeatedly/looping after specified interval. It consumes memory. Also returns a reference clearInterval(<interval_name>) - only required when using setInterval()

```JavaScript
let attempt = 0;
const reconnect = setInterval(function(){
    console.log("Reconnecting to database every 3 sec....");
    if(attempt === 5){
clearInterval(reconnect);
    }
    attempt++;
}, 3000);
```
The function passed as parameter to setInterval will run every 3second and will be cleared when attempt equals 5.

**Note :** in JS code run in non-blocking way and time is handled in msec.
1 second = 1000 milli seconds.

## Parse Method
method to parses/convert string to  number primitive type and returns it.

* `parseInt()` - parses/convert string and return integer or NaN.
```JavaScript
console.log(parseInt('urmila')); //NaN
console.log(parseInt('124xyz')); //124
console.log(parseInt('fy456')); //NaN
console.log(parseInt('678.56')); //678
console.log(parseInt('0x16'));  //22
console.log(parseInt('0e7')); //0
```

* `parseFloat()` - parses/convert string and return floating number or NaN. If first character of string is not a number it return NaN or else keep parsing until a number and returns it.

```JavaScript
console.log(parseFloat("456")); //456
console.log(parseFloat("256.56ads")); //256.56
console.log(parseFloat("gh33")); //NaN
console.log(parseFloat('0e7')); //0
```

## JSON : built-in Object.

JSON : keys should be double quoted, no delimiter for last value, cannot use  ( . ) to access property. 

Object as data- used within program.(JSON conveted into object)

JSON as data - used outside of program.(Object to another application in JSON)

## JSON method
Can  be applied on object as well as array.

* `.stringify({})` : convert object to JSON string, used when we want to send data outside.
JSON.stringify({});

```Javascript
const student = {
    'first Name':"Urmila",                    
    lastName:"Patel", 
    rollNo:50,
    getdetail: function(){ //method
        console.log(`Name :${'first Name'} ${lastName}`);  
    }
}

const studentJSON = JSON.stringify(student);
console.log(studentJSON);  //{"first Name":"Urmila","lastName":"Patel","rollNo":50}
```

* `.parse('{}')` : convert JSON to object string, used when we get data from outside.
JSON.parse("{}");

```JavaScript
const json = '{"first Name":"Urmila", "lastName":"Patel", "rollNo":50}';
const obj = JSON.parse(json);
console.log(obj);             //{ 'first Name': 'Urmila', lastName: 'Patel', rollNo: 50 }
console.log(obj.lastName); //Patel
```

### `.stringify([])` and `.parse('[]')` on array.

```JavaScript

const students = ['Urmila','Sonali','Meghana'];

const studentString = JSON.stringify(students); 
console.log(studentString); //["Urmila","Sonali","Meghana"]

console.log(JSON.parse(studentString)); // [ 'Urmila', 'Sonali', 'Meghana' ]
```

**Note :** JSON are not object they are data.

