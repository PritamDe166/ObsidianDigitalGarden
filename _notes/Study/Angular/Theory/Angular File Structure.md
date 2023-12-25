
### **Back to Index** : - [[Index- Angular Topics]]


---

### Topics in this page:
- [[#_App Folder_]]
- [[#_Package.json_]]
- [[#_Angular.json_]]
- [[#_App.module.ts_]]

---


The angular folder structure may look intimidating but let's try to break it down.
![[Angular_folder_Structure.png]]


---

### _App Folder_:

The folder has the core application files. The entire application is inside this. Most of the other things are mostly related to things like listing, and compiling and not directly to the writing of your angular application.
 <br>
Now let's start with the most important files.

---

### _Package.json_:

This is manifest that contains information related to the application and the dependencies, packages, and versions of these things.
 <br>
It contains "npm" shortcuts and scripts that can be used. E.g. ng serve which is used to compile the application.

```ts
{
  "name": "angular-concepts1",
  "version": "0.0.0",
  "scripts": {
    "ng": "ng",
    "start": "ng serve",
    "build": "ng build",
    "watch": "ng build --watch --configuration development",
    "test": "ng test"
  },
  "private": true,
  "dependencies": {
    "@angular/animations": "^16.1.0",
    "@angular/common": "^16.1.0",
    "@angular/compiler": "^16.1.0",
    "@angular/core": "^16.1.0",
    "@angular/forms": "^16.1.0",
    "@angular/platform-browser": "^16.1.0",
    "@angular/platform-browser-dynamic": "^16.1.0",
    "@angular/router": "^16.1.0",
    "@ng-bootstrap/ng-bootstrap": "^15.1.1",
    "@popperjs/core": "^2.11.6",
    "bootstrap": "^5.3.1",
    "rxjs": "~7.8.0",
    "tslib": "^2.3.0",
    "zone.js": "~0.13.0"
  },
```


---

### _tsconfig.json_:

Since angular uses typescript, this file acts as a configuration file for the typescript. So that anything that we write in typescript gets converted to javascript and that config is mentioned in this file.


### _Angular.json_:

- This is the configuration file for angular CLI. Here we can add scripts, styles, etc. This contains information about the index, root, styles, scripts, etc. for the CLI to be able to act as a runtime environment for angular.
 <br>
- So if we want any bootstrap, JSON, etc, we can install it through the npm and add the path of the bootstrap in this file. 
  The same goes for the “js” file and we can mention that in the scripts section of this file and that will dynamically get referred into the DOM.
 <br>
```ts
"Angular_Concepts1": {
      "projectType": "application",
      "schematics": {},
      "root": "",
      "sourceRoot": "src",
      "prefix": "app",
      "architect": {
        "build": {
          "builder": "@angular-devkit/build-angular:browser",
          "options": {
            "outputPath": "dist/angular-concepts1",
            "index": "src/index.html",
            "main": "src/main.ts",
            "polyfills": [
              "zone.js"
            ],
            "tsConfig": "tsconfig.app.json",
            "assets": [
              "src/favicon.ico",
              "src/assets"
            ],
            "styles": [
              "node_modules/bootstrap/dist/css/bootstrap.min.css",
              "src/styles.css"
            ],
            "scripts": [
              "./node_modules/bootstrap/dist/js/bootstrap.js"
            ]
          },
```


---

### _node- modules_:

All of our node dependencies and packages are inside this folder. 

---

### _E2e_:

End-to-end testing and not required from a dev perspective.

---

### _Index.html_:

- This is the main HTML file of the application which gets rendered when the application is loaded.
 <br>
- By default, we have the “app component” as the default component and for that, we have the selector “app-root”. This will be referenced in the index.html and this will link to all the components and Html files that we will be writing for our functionalities.
 <br>
- As we can see the selector “app-root”. This is nothing but the selector for the app component. 
 <br>
- This will make sure that the contents inside the app component will be rendered inside the body tag of this index.html.
 <br>
```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>AngularConcepts1</title>
  <base href="/">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="icon" type="image/x-icon" href="favicon.ico">
</head>
<body>
  <app-root></app-root>
</body>
</html>
```


---

### _App.module.ts_:

As we have seen, the "main.ts" loads something called “app.module” and this is declared in this file.
 <br>
All the references to every module, service, and component are mentioned in this file which helps the angular CLI to load those components during runtime.
 <br>
```ts
import { InputExampleChildComponent } from './InputOutputExample/input-example-child/input-example-child.component';
@NgModule({
  declarations: [
    AppComponent,
    NavbarComponent,
    LoginComponent,
    HomeComponent,
    ParentRouterOutletComponent,
    TemplateDrivenComponent,
    ReactiveFormsComponent,
    InputExampleParentComponent,
    InputExampleChildComponent
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    NgbModule,
    FormsModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

 <br>

- So for any new component, we need to mention the name in the “declarations”
		- Component -----> declarations
		- Modules      ------> imports
		- Services     -------> providers
 <br>
- We also see that there is a “bootstrap” array. This is not to be confused with the CSS style bootstrap. This bootstrap means “loading”. This tells the cli to load the app component by default. We won't be changing it.
 <br>
So this is the melting point of the app.

Now let's see some component-specific files.


---

### _App.component.ts_:

- This is the component file for the default component “app”. Like each component, this will contain the “@Component” directive where the selector, template, and style URLs are mentioned.
 <br>
- Component files are also where we write our classes and variables and functional logic.
 <br>
```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'Angular_Concepts1';
}
```


---

### _App.component.html_:

- This is the template HTML for the default component “app”. The contents of this will be loaded into the index.html while rendering in the position where we had mentioned the selector for the app component.
 <br>
In this file, we will mention the selectors of other components whose content we want to be rendered.
 <br>
```html
<app-navbar></app-navbar>
<div class="container">
    <app-parent-router-outlet></app-parent-router-outlet>
</div>
```


---

### Back to Top : [[#Topics in this page]]
