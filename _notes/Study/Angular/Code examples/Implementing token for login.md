
### **Back to RouteGuard** : - [[RouteGuard explaination]]


---


### **Creating the login page:**

- So lets create a login page in bootstrap.
- In our login page, we have `fullname` and `email`.
- Our game plan here would be:
	- When an user enter name and email, we will check with a list of login credentials, if the details entered by the user is present or not. If it is present, we create a token and If not, we redirect to the registration page.

---

#### _Here are the steps to achieve that:_

1)  **Create a login page :**

- In this specific example we have created a login page with `fullname` and `email`.
- So we will create a model for this login. We can check the details for adding a model here: [[Creating a data model]].
  In this case we have created a data model like below.

```ts
export class loginUserDetails{
    fullName : string | undefined;
    email : string | undefined;
}
```


<br><br>

---


2) **Create a constant to hold authentication username and passwords (_since we are not using any DB_): **

- We will create a constant that holds all the user login details. Creation of constants can be found here [[Constants in angular]]
- It will be an array of `loginUserDetails`, which is the data model class we have created above.
  For this current example we have created a file `constantFile.ts`, and using the below code:
  
```ts
import { loginUserDetails } from 'src/app/Data-Models/UserClasses';

export const UserLoginDetails :  loginUserDetails[]= [
    {fullName : 'Pritam Dey', email: 'pritam.dey@gmail.com'},
    {fullName : 'Payal Dutta', email: 'payal.dutta@gmail.com'},
    {fullName : 'Ram Singh', email: 'ram.singh@gmail.com'},
    {fullName : 'Ravi Gupta', email: 'ravi.gupta@gmail.com'},
    {fullName : 'Seeta M', email: 'm.seeta@gmail.com'},
    {fullName : 'Kalyan Singh', email: 'kalyan.singh@gmail.com'},
];
```



<br><br>

---

3) **Create a _Service_ where we will be writing the logic for validating the login credentials**:

- Next step will be to create a `service.ts` file in order to write the logics.
- We can take a look at the steps to create a service here : [[Creating a Service in angular]]
- Once you have created the service file, we will be writing the logic to validate the login credentials entered by the user against the saved credentials in our const variable.

```ts
validateUserDetails(loginData : loginUserDetails): boolean{
    
    var returnval : boolean = false;
   
    UserLoginDetails.forEach(item => {
      if(item.fullName?.toUpperCase() === loginData.fullName?.toUpperCase() &&
         item.email?.toUpperCase() === loginData.email?.toUpperCase()
      ){
        returnval = true;
        return true;
      }
      else{
        return false;
      }
    })
    return returnval;
}
```


- So this service method will return `true` and `false` based on whether the credentials entered by the user matches the list of users.
- We will call this service method in our `login component`. 

---

4) **Create a service which has method to create a token**:

- For the sake of our application, we will just use a simple token just for the sake of understanding the [[RouteGuard explaination]].
- In this method, we will be creating a random token, and then saving it in the localStorage. We can take a look about details on the localStorage here : [[Browser Storage Techniques]]

```js
  generateToken() : string{
      return Math.random().toString(36).substring(2);
  }

  saveToken() : void{
      const token = this.generateToken();
      localStorage.setItem(tokenKey, token);
  }
```

- We can then access this method and this localStorage token in other components.

---

4) **Logic in the login page to generate the token**:

- Now that we have a service to generate token, we will need to implement it in our login page.
<br>
```js
 loginFn(formsdata : any){
    this.isLoginValidated = this.loginAuth.validateUserDetails(this.loginData);
    if(this.isLoginValidated){
      this.tokenCreation.saveToken();
      this.router.navigate(['home']);
    }
  }
```


- Our logic would be that: 
	- When login button is clicked, we will first call the service to authenticate if the credentials entered are correct.
	- Next, we will call the `saveToken()` method in the service which is create a token and save it in the localStorage.
	- Then we will navigate to the `home` route, by using `router.navigate()`. Find the details about `navigate()` here: [[Routing Concepts#**router.Navigate([''])**]]

<br><br>

