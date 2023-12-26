
## **Back to Index : [[Javascript Index]]

---

### **Basics about Javascript Objects:

- In Javascript we have another type of datatype called objects.
- Lets see the below example:
```js
const Employee1 = {
    name: 'Pritam',
    age : 32
}
```

- This is how we can declare an object. As we see we have created an "Employee" object with 2 properties "name" and "age".

---

#### Accessing an Object:

- Now lets see how we can access this object.

```js
	console.log(Employee1);

    console.log(Employee1.name);
    console.log(Employee1.age);
```

- Here we have accessed individual properties, as well the entire object as a whole. The Console looks something like this.
```console
> Object { name: "Pritam", age: 32 }
Pritam
32
```

- Another way to access an object is through the `[]` notation. Lets see an example.
```js
    console.log(Employee1['name']);
    console.log(Employee1['age']);
```

- This notation is helpful when we have a property which has a special character in its name. Like `department-name`. In that case if we use the "dot" notation, then it will give an error. 
- But most commonly used syntax is the "dot" notation.

---

#### Add Properties to any object Dynamically:

- We can also add any property Dynamically to any object like this:
```js
Employee1.dept = 'IT';
```

- So even if the initial "Employee1" Object doesn't have this "Dept" property, it doesn't give us any error because JS is not a strongly typed language.

***Example***:

- We have a small example where we have used object to hold the score for our Rock, paper , scissors game.
- So basically we create an object which holds the scores.
```js
const Score = {
    Wins : 0,
    Losses : 0,
    Ties : 0
}
```

- At each win or loss or tie we just keep incrementing the values:
```js
case 'Rock':
            if(systemChoice === 'Scissors'){
                console.log('Opponent chooses '+systemChoice+ '. You Win !!!!');
                Score.Wins ++;
            }
            else if(systemChoice === 'Rock'){
                console.log('Opponent chooses '+systemChoice+ '. Its a Draw !!!!');
                Score.Ties ++;
            }
```

- We also have a function to reset the scores:
```js
function ResetScore(){
    Score.Wins = 0; Score.Losses = 0; Score.Ties = 0;
    console.log('Score Resetted.');
}
```

---

#### Nested Objects:

- Objects can have properties of any datatype, including other objects. Lets see the below example:
```js
const Employee1 = {
    name: 'Pritam',
    age : 32,
    department : {
        deptId : 101,
        deptName : 'Mathematics'
    }
}
```


- Here, we see that the ***department*** is a property which is another object, containing the properties ***deptId*** and ***deptName***.
- In order to access the values, we do the same, i.e. 
```js
	console.log(Employee1);

    console.log(Employee1.name);
    console.log(Employee1.age);
    console.log(Employee1.department);

    console.log(Employee1.department.deptId);
```


---

#### Methods (functions inside JS objects):

- `Methods` are functions which are inside any object. Like we have seen above, a Javascript object is capable of storing many types of values , including all basic datatypes, other objects.
- It is also capable of having functions in the properties. These are called as `methods`, which is nothing but functions that are the held inside objects. For eg:

```js
const Employee1 = {
    name: 'Pritam',
    age : 32,
    department : {
        deptId : 101,
        deptName : 'Mathematics'
    },
    printMsg : function printMsg(){
        console.log('Method Inside Object');
    }
}
```

- In the above example, _printMsg_ contains the value as a function. In order to excess the function, we will be using the same kind of 'dot' syntax.
```js
Employee1.printMsg();
```

- We have seen similar objects that are built-in or system defined. We have already used a similar 'built-in' function which is `console.log()`. Here log() is the method enclosed inside the object `console`.

- Another concept that we need to to see are the JSON objects and how it is different than the Javascript objects.

---

### **JSON objects (Javascript Object Notation)**:

- JSON is a notation and way to store the data in objects. JSON objects are widely used to send data across networks due to it light-weightlessness and because its is widely accepted across all languages.
- It looks similar to what we have seen in the JS objects.
- The `only difference` is that JSON objects doesn't  support `Methods` inside it. Example of a JSON Object:
```js
const Employee2 = {
    "name" : "Pritam",
    "age"  : 30,
    "Department" : "IT"
}
```

<br><br>
- We have a JS object 'Employee1' and now lets see how we can convert that in a JSON object:
```js
JSON.stringify(Employee1)
```

- This will convert the JS object into the JSON format but it will be in string format. Now we can convert this into a JSON object like this:
```js
	let jsonString = JSON.stringify(Employee1)
    console.log(JSON.parse(jsonString));
```

- If you notice in the console, the method which is inside the JS object "Employee1", is not present in the converted JSON object. This is because, as we discussed, JSON object doesn't support methods.

---
