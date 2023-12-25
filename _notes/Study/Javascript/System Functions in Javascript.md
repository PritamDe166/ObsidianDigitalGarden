
## **Back to Index : [[Index]]

---

### **Math.random()**:

- This basically generates a random number between 0 and 1. Lets see the syntax below.
```js
(Math.random() * 100);
```

---

### **Math.floor()**:

- This will round off the value to the nearest lowest value.
```js
Math.floor(Math.random() * 100);
```

---

### **Switch-case**:

- This can be used when you have too many if-else conditions. 
```js
switch (option){
        case 'Rock':
            if(systemChoice === 'Scissors'){
                console.log('Opponent chooses '+systemChoice+ '. You Win !!!!');
            }else if(systemChoice === 'Rock'){
                console.log('Opponent chooses '+systemChoice+ '. Its a Draw !!!!');
            }
            else{
                console.log('Opponent chooses '+systemChoice+ '. You Lose !!');
            }
            break;
        case 'Paper':
            if(systemChoice === 'Rock'){
                console.log('Opponent chooses '+systemChoice+ '. You Win !!!!');
            }else if(systemChoice === 'Paper'){
                console.log('Opponent chooses '+systemChoice+ '. Its a Draw !!!!');
            }else{
                console.log('Opponent chooses '+systemChoice+ '. You Lose !!');
            }
            break;
        case 'Scissors':
            if(systemChoice === 'Paper'){
                console.log('Opponent chooses '+systemChoice+ '. You Win !!!!');
            }else if(systemChoice === 'Scissors'){
                console.log('Opponent chooses '+systemChoice+ '. Its a Draw !!!!');
            }else{
                console.log('Opponent chooses '+systemChoice+ '. You Lose !!');
            }
            break;
   }
```


