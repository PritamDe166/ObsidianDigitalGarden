
### **Back to Index** : - [[Index- Angular Topics]]

---
### _Topics in this page_
- [[#_Intro _]]
- [[#_Constructor _]]
- [[#_ngOnInit _]]
- [[#_ngOnDestroy _]]
- [[#_ngOnChanges _]]
- [[#_ngDoCheck_]]
- [[#_ngAfterContentInit_]]
- [[#_ngAfterContentChecked_]]
- [[#_ngAfterViewInit_]]
-  [[#_Order of the lifecycle hooks_]]



---


### _Intro:_

- These are interfaces and by implementing these interfaces in the component class, we can gain access to the life cycle events. This is a way for the user to access the life cycle events for a page life cycle.
 <br>
- A component in Angular has a life cycle, several different phases it goes through from birth to death. 

		We can hook into those different phases to get some pretty fine-grained control of our application. To do this we add some specific methods to our component class which gets called during each of these life-cycle phases, we call those methods hooks.

---

### _Constructor:_

- This is the first life cycle hook to be called We can do assignments here, along with dependency injection for services, etc.
 <br>
````ts
constructor(){
	//code goes here;
}
````


---

### _ngOnInit:_

- Whenever the component is loaded into the DOM, then the constructor is called and then the ngOnInit is called.


---

### _ngOnDestroy:_

- ngOnDestroy is called whenever the component is unloaded from the DOM. It can be used to destroy unused objects, subscriptions, etc.
 <br>
- **An example of why "ngOnDestroy" is needed would be this:** 
	- let us increment a counter every second in the onInit.

	- When the component is unloaded, still we can see that the counter keeps on incrementing. we can destroy this interval increment in the OnDestroy.


---

### _ngOnChanges:_

- This will get called whenever there is an incoming input (data communication) between the parent and child constructor.
 <br>
- It will be called the first time before the ngOnInit. Each time any changes are passed on between the components, the ngOnChanges is called.
	 <br>
- The OnChanges method accepts a parameter of type `SimpleChanges`. This object contains the current changes and previous changes. This can be used to keep track of the changes that are being done on each input change.

		Note: the ‘ngOnChanges’ that get called in the above scenarios are in the child component where the data is getting transferred. So the child’s ‘ngOnChanges’ will get called at this juncture.
 <br>
- This works for `@input` bound properties only. We can consider this as a function, which captures the data coming in a child component. 
 <br>
- For the data going out of the child component, we have an output and event emitter function. So that covers the part of capturing the incoming changes.


---

### _ngDoCheck_:

- This is invoked after the change detector of the component is invoked. This is called after ngOnInit on the first run and then after ngOnChanges for any change detection.
 <br>
- We should avoid any expensive operations in the ngDoCheck. 
 <br>
- And also we should avoid using ngOnChanges and ngDoCheck in the same component. Because sometimes change detection can trigger another change detection and it becomes an infinite loop.


---

### _ngAfterContentInit_:

- This is invoked after angular perform any content projection in the component’s view. 
 <br>
- If there is a parent component and a child component, then the ngAfterContentInit will be present in the child component.

---


### _ngAfterContentChecked_:

- This is invoked after the projected content is checked by the angular change detection.
 <br>
- If there is a parent component and a child component, then the ngAfterContentChecked will be present in the child component.

---

### _ngAfterViewInit_:

- This is called in response after Angular initializes the component's views and child views.

---

### _ngAfterViewChecked_:

- This is called in response after Angular checks the component's views and child views.

---


### _Order of the lifecycle hooks_:

| `Events`                |
| ---------------       |
| Constructor           | 
| ngOnChanges           |
| ngOnInit              |
| ngDoCheck             |
| ngAfterContentInit    |
| ngAfterContentChecked |
| ngAfterViewChecked    |
| ngOnDestroy           |


### Back to top : [[#_Topics in this page_]]

