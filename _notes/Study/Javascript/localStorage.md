
## **Back to Index : [[Javascript Index]]


---

### **localStorage**:

- localStorage is a way to store data that survives browser refresh.
- Normal variable are only valid for that particular session so it doesn't survive the browser refresh.
- Lets see the example of the `Rock, paper, scissors` game that we saw. We had earlier saved the scores in an object. This will get refreshed even when we reload the browser.
  Lets see the scenario, where we want to stop the scores from refreshing when we refresh the browser. It will refresh only when we click on the "Reset" button.
</br></br>
- Lets see the syntax for localStorage:
```js
localStorage.setItem('Score', JSON.stringify(Score));
```

- It is to be noted that the `localStorage` only accepts "string" values.
- So here we are setting the value using `localStorage.setItem()` and we can fetch the value using `localStorage.getItem()`.
```js
JSON.parse(localStorage.getItem('Score'));
```

</br></br>
- As we have discussed that one of the requirement will be that the score should be reset when we click on `Reset` button. For that we remove the localStorage when we click on that button. 

```js
 localStorage.removeItem('Score');
```

- Removing the `localStorage` is very important since it doesn't get deleted when browser is refreshed or even closed. So If we do not remove the localStorage after a session ends or a user logs out, then it might become a security issue in the real time scenarios.

---
