

### **Back to RouteGuard** : - [[Implementing token for login]]

---

- We need constants in angular for storing values that will remain constant throughout the session. 
- We have seen an example earlier where we used to store the details of the `username` and `email` that we use to validate the login credentials.

```js
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


- By using the `export` keyword, we make sure that this `const` variable is accessible throughout the application to be imported and used. 