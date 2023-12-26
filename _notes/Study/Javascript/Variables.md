
## **Back to Index : [[Javascript Index]]

---

### **Declarations of variables:**

>[!tip] Javascript is a weakly typed language.

- Variables can be defined using the keyword `let`. For eg.
````js
let variable1 = 3;
````

- Variables can also be created using the keyword `const`. This will create a constant variable whose value cannot be changed once it is assigned. So if we are storing a value that we know will not change throughout the application, then we can use `const`.

```js
const variable2 = 6;
```

- Another way of creating a variable in using `var`. This creates a variable similar to `let` which allows the value to be modified. But `var` has some issues which makes it more favourable to instead use `let`, to declare a variable in JS. 

---

### **Some Rules related to variables**:

- We cant use special keywords as the name of the variable. like `var`, `let` etc. These are reserved keywords.
<br><br>
- A variable name cant start with a number. It can have numbers in the middle and end.
<br><br>
- We cant use most special characters like `@,#,!, spaces` etc. The only special characters we can use are `$` and `_`.
<br><br>
- Another important character in the semicolon. Its needed to separate two set of instructions. For eg.
```js
let variable1 = 3 console.log(variable1)
```

These are 2 different set of instructions. But until we separate them with a semicolon, JS will not recognise it. So we need to provide the semicolon between them as:

```js
let variable1 = 3; console.log(variable1)
```

Another feature of javascript in the auto-insertion of he last semicolon. So javascript basically inserts the semicolon at the end of the line automatically during runtime. So the above command will execute properly even if we haven't explicitly mentioned the semicolon.
However its the `best practise` to use semicolon in our syntax.


- Naming convention for any variable in JS is `camelCase`.
<br><br>
- Also remember the since JS is a weakly typed language, we may often need to use then `typeof` function in our logic to understand what kind of value a certain variable holds.
```js
console.log(typeof(totalQuantity));
```

---

### **Simple buttons and calculation example:**

- Note that we are using Bootstrap as our CSS class here:

***Html Page***:

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Javascript Practise</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="../JS_Practise1/styles/bootstrap.css">
  <script src="../JS_Practise1/scripts/myOwn.js"></script>
  <script src="../JS_Practise1/scripts/bootstrap.js"></script>
</head>
<body>
  <div class="container">
    <h1>This is Cart App</h1><br>
    <div class="row">
      <div class="col-2">
        <input class="btn btn-outline-warning" type="button" id="showQ" name="showQ" value="Show Quantity" onclick="ShowQuantity()">
      </div>
      <div class="col-2">
        <input class="btn btn-outline-primary" type="button" id="AddItem" name="AddItem" value="Add Item" onclick="AddItem()">
      </div>
      <div class="col-2">
        <input class="btn btn-outline-dark" type="button" id="Addtwo" name="Addtwo" value="+2" onclick="AddTwo()">
      </div>
      <div class="col-2">
        <input class="btn btn-outline-secondary" type="button" id="reset" name="reset" value="Reset Cart" onclick="ResetCart()">
      </div>
    </div>    
  </div>  
</body>
</html>
```


***JavaScript***:

```JS

let totalQuantity = 0;

function ShowQuantity(){
    console.log(`Total Quantity : ${totalQuantity}`);
}

function AddItem(){
    totalQuantity ++;
    ShowQuantity();
}

function ResetCart(){
    totalQuantity = 0;
    ShowQuantity();
}

function AddTwo(){
    totalQuantity += 2;
    ShowQuantity();
}
```