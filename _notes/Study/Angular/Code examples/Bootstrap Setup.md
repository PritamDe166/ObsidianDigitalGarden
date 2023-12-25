

### **Back to Index** : - [[Growing the Application one by one]]

---


### **Installing bootstrap**

- To install bootstrap, we go to cmd and install bootstrap.

```cmd
npm install bootstrap
```

- This gets installed in the `node_modules` folder. 

---

- There are multiple ways to make sure that we use bootstrap throughout the application.

> [!tip] Adding in the `angular.json`

- We can add the references of the bootstrap css and the `js` here.
- We will be including the css file reference in the `styles` array and the `js` reference in the `scripts` array.

```js
"styles": [
	"node_modules/bootstrap/dist/css/bootstrap.min.css",
	"src/styles.css"
],
"scripts": [
	"./node_modules/bootstrap/dist/js/bootstrap.js"
]
```


---

> [!tip] Adding in the `styles.css`


- The `styles.css` is a global css file. So we can add the bootstrap css in this file to make sure that it is referenced throughout the entire application.

```css
@import url('../node_modules/bootstrap/dist/css/bootstrap.css');
```


---
