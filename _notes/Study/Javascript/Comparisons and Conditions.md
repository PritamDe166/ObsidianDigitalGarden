## **Back to Index : [[Index]]

---

### **Conditional operators in JS**:

- The conditional operators used in JS are 
	- `>` greater than.
	- `<` less than.
	- `>=` greater than equal to.
	- `<=` less than equal to.
	- `===` equal to.
	- `!==` not equal to.

---

### **Example for all operators**:

***Greater Than***:
```js
function LessThan(){
    console.log(num1 < num2);
}
```

</br></br>

***Less Than***:
```js
function MoreThan(){
    console.log(num1 > num2);
}
```


</br></br>

***Greater than equal to***:
```js
function GTEqTo(){
    console.log(num1 >= 5);
}
```

</br></br>

***Less than equal to***:
```js
function ltETo(){
    console.log(num2 <= 8);
}
```

</br></br>

***Equal to (`===`)***:
- In Javascript, we normally use `===` as the conditional operator. This will do a strongly-typed comparison. This means it will compare the `type` as well as `value`.
- So in the below example, when we compare the variables with values `4.5` and `"4.5"`, we see that they might have the same value but different data types. Hence, their comparison will not be equal.

```js
function EqualTo(){
    console.log(val1 === val2);
}
```

</br></br>

***Equal To (`==`)***:
- This is also work, but this does a weakly typed comparison. In the same example with values `4.5` and `"4.5"`, it will consider them equal.
```js
function EqualTo2(){
    console.log(val1 == val2);
}
```

</br></br>

***Not Equal To***:
```js
function ntEqual(){
    console.log(num1 !== num2);
}
```

---

### **Ternary Operator**:

- Ternary operator is a syntax, which is a substitute for `if-else` statement. Lets see the syntax.
```js
var result = (num1 > num2) ? true : false;
```

- This statement replaces the `if-else` statement that might have been written something like this:
```js
	if(num1 > num2){
        return true;
    }
    else{
        return false;
    }
```


---

### **Truthy and Falsy**:

- Lets see the below example.
```js
	if(num1 > 0){
        console.log('this is truthy');
    }
```

- What we can see here is that, we are checking that if the variable "var1" is greater than 0, then we log something in the console.
- This can be also written in the below manner:
```js
	if(num1){
        console.log('this is truthy');
    }
```


- The `truthy` and `falsy` values are used in the conditional statements.
- The falsy values are :
	- `false`
	- `0`
	- `NaN` : Not a number
	- `undefined` : When no value is assigned to the variable.
	- `null`

- So when we are checking for any condition these truthy and falsy values can be used to simplify our conditional statements.

---

### **Guard Operator**:

- As we know than an AND operator (`&&`), will be complete if all the conditionals are true. So basically in case the very first statement encountered, is false, it will stop the check at that point and will not proceed with any further checks.
- So lets say we want to store a value to a variable if something is true. A shortcut for that can be explained below.
- Lets see the below example:
```js
	let message ;

	if(5){
		message = 'Hello';
	}
```

- With the Guard operator, lets see the same logic:
```js
	let message = 5 && 'hello1';
	console.log(message);
```

- What this does is, if the first statement is true , which in this case it is, then it will go to the next statement and will assign the latter value to the variable "message".


---

### **Default Operator**:

- Just like `Guard operator`, we have another operator to take care of the if statement, for "false". 
- Using the `Default operator`, we have a shortcut way of writing the below if-else statement.
```js
	let message;

    if(num1 > num2){
        console.log('i m here');
    }
    else{
        console.log('Default operator');
    }
```

- For this, we can use the default system as:
```js
	let message = (num1 > num2) || 'Default Operator';

    console.log(message);
```


---
</br>

>[!tip] These `ternary operator`, `truthy , falsy` , `Guard Operator` and `Default Operator` can all be considered as shortcuts to the `if-else` condition. 


---

### **Example of these operators used in latter examples**:

***Default Operator***:

- In our [[localStorage]] example, we had used this below if condition to check if the localStorage is `null`, then assign the reseted value.
```js
function ViewScore(){
    let scoreFromLocalStorage = JSON.parse(localStorage.getItem('Score'));

    if(scoreFromLocalStorage === null){
        scoreFromLocalStorage = JSON.parse(JSON.stringify(Score));
    }
	...
	...
}
```

</br></br>
- Instead of this, using the `default operator` syntax, we can rewrite it as follows:

```js
let scoreFromLocalStorage = JSON.parse(localStorage.getItem('Score')) || JSON.parse(JSON.stringify(Score));
```


---

### **Objects are reference types**:

- Value of the objects are stored in the memory and the objects are actually reference to the memory location where they are saved.
- So when we copy one object to another, we the reference is copied and that means we have 2 references pointing to the same object in memory.
- When the value changes, it will be reflecting in the both the references. For eg.

```js
	let object1 = {
        message : 'Hello'
    };

    console.log(object1.message);

    let object2 = object1;
    object1.message = "message changed";

    console.log(object1.message);
    console.log(object2.message);
```

- We see that when we print the message properties in both the objects, then it shows the changed message.

