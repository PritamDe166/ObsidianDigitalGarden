
## **Back to Index : [[Javascript Index]]

---

Lets see how to strings in javascript work:

### **Plus (`+`) operator:**

- When we try to add 2 strings , it `concatenates` those strings in to a new one.

```console
>> 'some ' + 'Text'
-> "some Text" 
```


- Remember that javascript follows `BODMAS` order for calculations.
<br><br>
- When we try to add a string and a number, it will convert the number into a string and concatenate. For eg.
```console
>> 'some' + 2
-> "some2"
```


- Lets see a scenario where we want to calculate something and then also concatenate with a `$` sign in the front. So for that we will use the bracket `( )` , `divide`, `*` . This will make sure all the operations are done before the plus operator with the `$` sign. Lets see the example below:

```console
>> '$' + 234.45 + 459.45
-> "$234.45459.45"

>> '$' + (234.45 + 459.45)
-> "$693.9"
```


---

### **Ways to create strings:**

- We can declare string in many ways:<br>
  1. Using `''` (Single quotes) <br>
  2. Using `""` (Double Quotes) <br>
  3. Using `"``"` (back Tick)<br>
  <br>
	- By default we can using single quotes for string, with the exception of one scenario. For example if we write the string `I'm learning JS`. So in this situation we will need to use double quotes because there is a single quote character.<br>
	  <br><br>
	- This scenario can also be resolved using something called `escape character`(\').  This denotes that the single quote after this will be considered as a string character rather than a single quote. for eg.
```console
>> alert('I\'m learning Js');
-> 'I\'m learning Js'
```

***String Interpolation***:

- This is another way of creating string which is very handy when we want to involve calculations and numbers in a string.
<br><br>
- In this concept, instead of using single or double quotes, we will use `tick`.
<br><br>
- Wherever we want to do any arithmetic operations, we put them inside `${}`. This will tell the console to calculate and append the result with the string. Lets see the below example. <br><br>
```console
>> `Total for ${2+2} products : Rs. ${(234.56 + 300.23 + 456.43 + 568.00)}`
-> "Total for 4 products : Rs. 1559.22"
```
- This is a very useful way of combining strings with numbers.


---

### **typeof operator:**

- The `typeof` operator is used to find the data type of any value or variable. 
<br><br>
- We can see the below example of how this operator works in console.

```console
>> typeof 2  
-> "number"  

>> typeof 'hello'  
-> "string"  

>> typeof true  
-> "boolean"
```


