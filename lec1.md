# Fundamentals 

app.component.html is the content we have, how does our server serve up html component? 


index.html has <app-root> </app-root>

all components are related to their names, how is angular triggered and kicked off? 

```html

<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>MyApp</title>
  <base href="/">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="icon" type="image/x-icon" href="favicon.ico">
<link rel="stylesheet" href="styles.css"></head>
<body>
  <app-root></app-root>
<script src="runtime.js" type="module"></script><script src="polyfills.js" type="module"></script><script src="styles.js" defer></script><script src="vendor.js" type="module"></script><script src="main.js" type="module"></script></body>
</html>


```

this gets injected by CLI command automatically 
it will create those javascript bundles and automatically add the right imports in the index.html file 


```TypeScript
import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';

import { AppModule } from './app/app.module';
import { environment } from './environments/environment';

if (environment.production) {
  enableProdMode();
}

platformBrowserDynamic().bootstrapModule(AppModule)
  .catch(err => console.error(err));

```

main.ts gets started, knows bootstrap[AppComponent] -> get bootstrappted -> app.module.ts -> index.html <app-root>
modules are building blocks 

angular code is able to use script src = "runtime.js" ....., angular overwrites this at runtime, 



## Components 



components are the key feature in angular 

app.component.ts
```TS

import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  name = 'Eddie';
}


```

app-root component which holds our app and nest our app 
header, menu, sidebar would be a fitting component
splitting up all the app into separate components , each component will have its own component and business logic 
it allows you to split your complex app and your complex webpage into reusable parts, you may use a component more than once that allows youto easily replicate the business logic 


it makes finely controlled peices in you app without having to crunch everything into one single script file



bootstrap: AppComponent tells the whole app with that component being the root component so all other components we created will not be added to the index.html file 
their component will be added to app.component.html file 

all your app related content will go to this app folder 


you create a folder called server having the folder name equal you component and each component typically should have its own folder 

let's create a server.component.js 

components are like classes so angular is able to instantiate it to create objects based on the blueprint we set up 

we need to tell angular it is a component 

the @angular/core gives us access to some of the core functionalities of angular 
we set up some important info inside @Component({}) to store as metadata

```TS

import { Component } from "@angular/core"

@Component({
selector: 'app-server',
templateURL : './server.component.html'
})



export class ServerComponent{

}
```



let's create a server.component.html

```html

<p> server component is right here </p>


```






to use this, we need to dive into the app.module.ts 
angular uses componentt to build web pages and uses modules to bascically bundle different pieces 
app module is a bundle of functionalites of our app and it basically give angular the information which features does our app have and use 

we transfor those components by adding the decorator @NgModule 
we add to add the new component so angular knows that this component exists because it is important 
by default angular will not scan all your files here 
we need to register these by the declarations array 

```TS
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';

import { AppComponent } from './app.component';
import { FormsModule } from '@angular/forms';
 
// we need to add ServerComponent here , you do not need .ts here the extension is addded automatically 
import { ServerComponent}  from './server/server.component';

@NgModule({
  declarations: [
    AppComponent,
    ServerComponent, // this is our server app 
  ],
  imports: [
    BrowserModule,
	FormsModule,
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }


```

we registered the component and let's add our component to app.component.html

```html



<input type = "text" [(ngModel)]= "title">


<p> {{ title }} </p>


<app-server> </app-server>
```

## using CLI command to create a new component  ng generate component <name>

```shell
ng generate component <name>
ng g c <name>
```


we can use the same component as often s we want bysimply using its selector 
CLI also update app.module.ts


## component templates 

we can change templatUrl to template 
you can have template either linekd to an external template or just the template to define it in this file but each component needs to have a template , this is the one property you have to have all times 

```TS
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-something',
  template: '<app-another> </app-another><app-another> </app-another>',
  styleUrls: ['./something.component.css']
})
export class SomethingComponent implements OnInit {

  constructor() { }

  ngOnInit(): void {
  }

}



```


we can use `` to write javascript strings to convert it to html 

```TS
import { Component, OnInit } from '@angular/core';



@Component({
  selector: 'app-something',
  template: `<app-another> </app-another><app-another> </app-another>`,
  styleUrls: ['./something.component.css']
})
export class SomethingComponent implements OnInit {

  constructor() { }

  ngOnInit(): void {
  }

}


```


You can use this approach to inline your code 




### Styling 

we can go to app.component.css for normal css code 



you can also define styles: []
this also takesa an array but now it takes an array of strings where you define the style in this string 



```TS

import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-something',
  templateUrl: `./something.component.html`,
  styles: [`
  h1{
  color: red;
  }
  `],
})
export class SomethingComponent implements OnInit {

  constructor() { }

  ngOnInit(): void {
  }

}

```

You cannot apply templateUrl and styles at the same time 




### Component Selector 



the selector has to be unique so you do not override the exisitng element or component made available to another third party package 




you can use square backets to use the attribute selector so in css, you can select elements by attribute by enclosing that attribute in square brackets 



```TS

import { Component, OnInit } from '@angular/core';

@Component({
  selector: '[app-something]',
  templateUrl: `./something.component.html`,
  styles: [`
  h1{
  color: red;
  }
  `],
})
export class SomethingComponent implements OnInit {

  constructor() { }

  ngOnInit(): void {
  }

}

```
now our app does not recognized app-something anymore 
now we need to add the 
```html
<div app-server> </div>
```




```html



<input type = "text" [(ngModel)]= "title">


<p> {{ title }} </p>


<app-server> </app-server>

<app-another> </app-another>

<div app-something> </div>
```

we can also do 

```TS 
 // selector: '.app-something',
import { Component, OnInit } from '@angular/core';

@Component({
  selector: '.app-something',
  templateUrl: `./something.component.html`,
  styles: [`
  h1{
  color: red;
  }
  `],
})
export class SomethingComponent implements OnInit {

  constructor() { }

  ngOnInit(): void {
  }

}


```

```html



<input type = "text" [(ngModel)]= "title">


<p> {{ title }} </p>


<app-server> </app-server>

<app-another> </app-another>

<div class = "app-something"> </div>

```


all pesudo selectors such as hover and so on do not work, and you typically use the element styles here 






## Data Binding (communication)


data binding is the communication between your data component using typescript code(business logic) to template HTML 

we want to output data to html template 

using string interpolation ({{data}})
property binding ([property] = "data")

react to user events using event binding 
((event) = "expresion")



## String interpolation 

string interpolation ahs to resolve to a string in the end, it ha to get a string 



```TS
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-hello',
  templateUrl: './hello.component.html',
  styleUrls: ['./hello.component.css']
})
export class HelloComponent {

 id: number = 100;
 stringValue :string = 'offline';

 helloMethod(){
  return this.id;
 }

}



```
```html

<p> {{id}} </p>

<p> {{stringValue}} </p>

<p> {{ helloMethod()}} </p>


```


## property binding 
there are a lot of times where you can use property binding or string interprolation 
```
[attribute] = "property_name"
```
for property binding, that we ant to dynamically bind some property and disable the html attributes 
normal html only sets a specific property on the underlying DOM element 
that element is unrelated to angular a lot of property cannot even be set through attributes on the html elements 
with square brakcet,s we are dynamically binding it to this native disabled property 


```html
<p> {{id}} </p>

<p> {{stringValue}} </p>

<p> {{ helloMethod()}} </p>


<button class = "btn btn-primary" [disabled] = "enabledButton"> click me </button>

```

```TS

import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-hello',
  templateUrl: './hello.component.html',
  styleUrls: ['./hello.component.css']
})
export class HelloComponent implements OnInit {

 id: number = 100;
 stringValue :string = 'offline';

 enabledButton = false;
 constructor(){
 setTimeout(() => {this.enabledButton = true;},2000);
 }

 ngOnInit(){

 }



 helloMethod(){
  return this.id;
 }

}

```



## property binding vs string interpolation 



```html
<p> {{id}} </p>

<p> {{stringValue}} </p>

<p> {{ helloMethod()}} </p>

<p> {{enabledButton}} </p>


<button class = "btn btn-primary" [disabled] = "enabledButton"> click me </button>

```


if you want to output something into your template, use string interpolation 
if you want to change some property, be that of a html element or directive component use property binding 


do not mix property binding with string interpolation 


```TS
// do not do this 
[attribute]={{propertyName}}

// do this 
[attribute]="propertyName";


```

string interpolation only works in a normal template not within another expression of that template 




## Event binding 


```TS

(eventName)="methodName()";
//(onlick)="methodnAME";

```


```TS


import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-hello',
  templateUrl: './hello.component.html',
  styleUrls: ['./hello.component.css']
})
export class HelloComponent implements OnInit {

 

nothing: string = "nothing started";
 constructor(){}

 ngOnInit(){

 }


 something(){
  this.nothing = "something showed up";
 }



 
}



```




```html
 <p> {{nothing}}</p>


 <button class = "btn btn-default" (click)="something()"> click me and something show up</button>

```

bind to all properties or events using console.log(). the element that you are interested in to see which properties and events it offers 


## Two way binding -- passing and using data with event binding 

```html 
<element (event) = "methodname($event)">


```
dollar sign event is super important , dollar sign event will only be data emitted with that event 

input and click ship some events when you fired , now we can capture this data with dollar sign event passed as an argument to the method we are calling or used anywhere between these quotation marks inthe code we are executing 
that can be type any for now event : any in the TS method 


```html

 <input type = "text" class = "form-control" (input)="updateInput($event)">

 <button class = "btn btn-default"  > click me and something show up</button>
```


```TS
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-hello',
  templateUrl: './hello.component.html',
  styleUrls: ['./hello.component.css']
})
export class HelloComponent implements OnInit {

 

 

 constructor(){

 }

 ngOnInit(){

 }

 
 updateInput(event : any){
  console.log(event);

 }

 
}



```



you can specifically inform type script the type of html HTMLInputElement event.target.value;


```TS


import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-hello',
  templateUrl: './hello.component.html',
  styleUrls: ['./hello.component.css']
})
export class HelloComponent implements OnInit {

 
 variableString : string = "";

 

 constructor(){

 }

 ngOnInit(){

 }

 
 updateInput(event : any){
  this.variableString = (<HTMLInputElement> event.target).value;
  console.log(this.variableString);

 }

 
}

```


```html

 <input type = "text" class = "form-control" (input)="updateInput($event)">


<p> {{variableString}}</p>

 <button class = "btn btn-default"  > click me and something show up</button>
```


#### important note: for two way binding you need to enable ngModel directive . this is done by adding FormModule to the imports[] array in the AppModule 


```TS

import { FormsModule } from '@angular/forms';

```



## two way databinding ([ngModel] = "variabelName")      {{variableName}}


```html

 <input type = "text" class = "form-control" 
 [(ngModel)] = "variableString" >


<p>  {{variableString}}</p>

 <button class = "btn btn-default"  > click me and something show up</button>
```


```TS
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-hello',
  templateUrl: './hello.component.html',
  styleUrls: ['./hello.component.css']
})
export class HelloComponent implements OnInit {

 
 variableString: string = "";

 constructor(){

 }

 ngOnInit(){

 }

 
 

 
}


```



comparison 


```html



<!-- two way data binding-->
 <input type = "text" class = "form-control" 
 [(ngModel)] = "variableString" >


<!-- one way data binding -->

 <input type = "text" class = "form-control" 
 (input) = "myEvent($event)" >



<p>  {{variableString}}</p>

 <button class = "btn btn-default"  > click me and something show up</button>
```


```TS
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-hello',
  templateUrl: './hello.component.html',
  styleUrls: ['./hello.component.css']
})
export class HelloComponent implements OnInit {

 
 variableString: string = "";

 constructor(){

 }

 ngOnInit(){

 }


myEvent(event: Event){
  this.variableString =  (<HTMLInputElement>event.target).value;

}
 
 

 
}


```


### combinding forms of data binding 

```html



<!-- two way data binding-->
 <input type = "text" class = "form-control" 
 [(ngModel)] = "variableString" >


<!-- one way data binding -->

 <input type = "text" class = "form-control" 
 (input) = "myEvent($event)" >

  <button class = "btn btn-default" (click) 
  = "clickMethod($event)"  > click me after you input something</button>



<p>  {{variableString}}</p>


```


```TS
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-hello',
  templateUrl: './hello.component.html',
  styleUrls: ['./hello.component.css']
})
export class HelloComponent implements OnInit {

 
 variableString: string = "";

 constructor(){

 }

 ngOnInit(){

 }


myEvent(event: Event){
  this.variableString =  (<HTMLInputElement>event.target).value;

}

clickMethod(event:Event){
  this.variableString = `now I have been clicked and show the phrase you typed as ${this.variableString} `;
}
 
 

 
}


```



## directives 

directives are instrutions in the DOM, components are kind of such instructions in the DOM 

there are also directives without a template, 
we typically add directives with an attribute selector but technically the selector of a directive can be configrued just like the selector of a component, so you could also use css classes or the element style 



```TS
@Directive({
  selector: '[directiveName]'
})
export class YourDirectiveName{

}

```



### nglf to put data conditionally 
*ngIf is a structural directive which means it changes the structure , it means it either adds or not addd just some extra info for angular, without it it cannot work correctly 



```javascript 


<input type = "text" [(ngModel)] = "variableString">
<p *ngIf="1===2"> {{variableString}}</p>

import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-hello',
  templateUrl: './hello.component.html',
  styleUrls: ['./hello.component.css']
})
export class HelloComponent implements OnInit {

 
 variableString: string = "";


 constructor(){

 }

 ngOnInit(){

 }

 trueMethod(){
  return true;
 }


methodName(event:Event){
  this.variableString = `hello, the string is ${this.variableString}`;
}


 

 
}

```


```TS

<input type = "text" [(ngModel)] = "variableString">
<button class = "btn btn-warning" (click) = "methodName($event)"> click me </button>

<p *ngIf="trueMethod()"> {{variableString}}</p>
```


## ngIf else enhancing statement 

ng-template is the component shipped with angular which you can use to mark places in the DOM 


```html
<tag *ngIf="methodName/variableName; else marker"> </tag>

<ng-template #marker>

</ng-template>

```



```html


<input type = "text" [(ngModel)] = "variableString">


<p *ngIf="falseMethod(); else marker"> {{variableString}} and it is true</p>
<ng-template #marker> {{variableString}} but it is false </ng-template>

```




## ngStyle  to style elements dynamically 


unlike structural directives, attribute directives do not add or remove elements, they only change the element they were placed on 


```html
<tagname [ngStyle]="style-name"> </tagname>


<tagname [ngStyle]="{style-name:method()/variable}"> </tagname>

```



```TS
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-hello',
  templateUrl: './hello.component.html',
  styleUrls: ['./hello.component.css']
})
export class HelloComponent implements OnInit {

 
 variableString: boolean = false;


 constructor(){
  this.variableString = Math.random() > 0.5 ? true : false;

 }

 
 getColor(){
  return "red";
 }

 ngOnInit(){

 }



 

 

 
}


```


```html
<p [ngStyle]="{backgroundColor:getColor()}"> hello this is me </p>

```



## ngClasse with CSS classes 

it only adds css classes if certain conditions are true 

```html
<tagname [ngClass] = "{classname : condition}"> </tagname>

```



```html




<p [ngClass]="{hello:1===1}"> hello this is me </p>


```


```TS
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-hello',
  templateUrl: './hello.component.html',
  styles : [ `
  .hello {
    color:blue;
    background-color:green;
  }
  `],
})
export class HelloComponent implements OnInit {

 
 variableString: boolean = false;


 constructor(){
  this.variableString = Math.random() > 0.5 ? true : false;

 }

 
 getColor(){
  return "red";
 }

 ngOnInit(){

 }




 
}



```



## *ngFor to output lists 




``html

<tagname *ngFor = "let item of list"> {{item}}</tagname>
```


```TS

let list = [elements...]


```



```html




<p *ngFor = "let variable of arrayVariable"> {{variable}} </p>

```

```TS
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-hello',
  templateUrl: './hello.component.html',
  styles : [ `
  .hello {
    color:blue;
    background-color:green;
  }
  `],
})
export class HelloComponent implements OnInit {

  arrayVariable = [1,2,3,4,5,6,7,8,9,10];


 constructor(){
 
 }

 

 ngOnInit(){

 }



 

 

 
}


```





### *ngFor indexing 

that is a tiny addition 




```html

<tagname *ngFor ="let element of list; let i = index"> </tagname>
```




```html




<p *ngFor = "let variable of arrayVariable; let i = index"> {{i}} </p>

```




### ERROR

src/app/app.component.html:9:1 - error NG8001: 'app-server' is not a known element:
1. If 'app-server' is an Angular component, then verify that it is part of this module.
2. If 'app-server' is a Web Component then add 'CUSTOM_ELEMENTS_SCHEMA' to the '@NgModule.schemas' of this component to suppress this message.

9 <app-server> </app-server>
  ~~~~~~~~~~~~

  src/app/app.component.ts:5:16
    5   templateUrl: './app.component.html',
                     ~~~~~~~~~~~~~~~~~~~~~~



```TS

import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';

import { AppComponent } from './app.component';
import { FormsModule } from '@angular/forms';
 
import { ServerComponent } from './server/server.component';

@NgModule({
  declarations: [
    AppComponent,
	ServerComponent,
  ],
  imports: [
    BrowserModule,
	FormsModule,
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }

```



 @Component({
  ~~~~~~~~~~~~
5 selector: 'app-server',
  ~~~~~~~~~~~~~~~~~~~~~~~
6 templateURL : './server.component.html'
  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
7 })
  ~~


Error: src/app/server/server.component.ts:6:1 - error TS2345: Argument of type '{ selector: string; templateURL: string; }' is not assignable to parameter of type 'Component'.
  Object literal may only specify known properties, but 'templateURL' does not exist in type 'Component'. Did you mean to write 'templateUrl'?

6 templateURL : './server.component.html'
  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Error: src/app/server/server.component.ts:13:1 - error TS1005: '}' expected.

13


```TypeScript


import { Component } from "@angular/core"

@Component({
selector: 'app-server',
templateUrl : './server.component.html',
})



export class ServerComponent{

}
```









<p [ngStyle]="backgroundColor:getColor()"> hello this is me </p>
<e> [webpack-dev-middleware] Error: Quotes are not supported for evaluation!
<e>         Statement: getColor() located at C:\Users\Eddie\Desktop\angularjs\p1\my-app\src\app\hello\hello.component.html@3:14
<e>     at _AstToIrVisitor.visitQuote (file:///C:/Users/Eddie/Desktop/angularjs/p1/my-app/node_modules/@angular/compiler/fesm2015/compiler.mjs:7279:15)
<e>     at Quote.visit (file:///C:/Users/Eddie/Desktop/angularjs/p1/my-app/node_modules/@angular/compiler/fesm2015/compiler.mjs:6095:24)
<e>     at convertPropertyBinding (file:///C:/Users/Eddie/Desktop/angularjs/p1/my-app/node_modules/@angular/compiler/fesm2015/compiler.mjs:6938:50)
<e>     at TemplateDefinitionBuilder.convertPropertyBinding (file:///C:/Users/Eddie/Desktop/angularjs/p1/my-app/node_modules/@angular/compiler/fesm2015/compiler.mjs:17836:42)
<e>     at Object.value (file:///C:/Users/Eddie/Desktop/angularjs/p1/my-app/node_modules/@angular/compiler/fesm2015/compiler.mjs:17488:51)
<e>     at file:///C:/Users/Eddie/Desktop/angularjs/p1/my-app/node_modules/@angular/compiler/fesm2015/compiler.mjs:17787:40
<e>     at Array.map (<anonymous>)
<e>     at file:///C:/Users/Eddie/Desktop/angularjs/p1/my-app/node_modules/@angular/compiler/fesm2015/compiler.mjs:17786:36
<e>     at file:///C:/Users/Eddie/Desktop/angularjs/p1/my-app/node_modules/@angular/compiler/fesm2015/compiler.mjs:17045:66
<e>     at Array.map (<anonymous>)










<p [ngStyle]="{backgroundColor:getColor()}"> hello this is me </p>






lay out the structure of this app, 

root 
header 
list         recipe 
edit            list 
ingredeint      item 
         detail 

you can split this more and merge more

model component feature 


```shell
ng new recipe 

npm install --save bootstrap

```


in the .angular.json file, add gloanl stylesheets to our own project 
C:\Users\Eddie\Desktop\angularjs>cd recipe

C:\Users\Eddie\Desktop\angularjs\recipe>dir
 Volume in drive C has no label.
 Volume Serial Number is 0697-3EFD

 Directory of C:\Users\Eddie\Desktop\angularjs\recipe

2022-01-20  09:29 PM    <DIR>          .
2022-01-20  09:28 PM    <DIR>          ..
2022-01-20  09:28 PM               600 .browserslistrc
2022-01-20  09:28 PM               274 .editorconfig
2022-01-20  09:28 PM               548 .gitignore
2022-01-20  09:28 PM    <DIR>          .vscode
2022-01-20  09:28 PM             3,039 angular.json
2022-01-20  09:28 PM             1,423 karma.conf.js
2022-01-20  09:29 PM    <DIR>          node_modules
2022-01-20  09:29 PM           742,267 package-lock.json
2022-01-20  09:28 PM             1,070 package.json
2022-01-20  09:28 PM             1,052 README.md
2022-01-20  09:28 PM    <DIR>          src
2022-01-20  09:28 PM               287 tsconfig.app.json
2022-01-20  09:28 PM               863 tsconfig.json
2022-01-20  09:28 PM               333 tsconfig.spec.json
              11 File(s)        751,756 bytes
               5 Dir(s)  54,268,370,944 bytes free

C:\Users\Eddie\Desktop\angularjs\recipe>npm install --save bootstrap@3

added 1 package, and audited 892 packages in 3s

92 packages are looking for funding
  run `npm fund` for details

6 vulnerabilities (3 low, 3 moderate)

To address all issues (including breaking changes), run:
  npm audit fix --force

Run `npm audit` for details.




in angular.json 




```json

            "styles": [
              "../node_modules/bootstrap/dist/bootstrap.min.css",
              "src/styles.css",
              ""
            ],

```


```shell
ng serve 

```
C:\Users\Eddie\Desktop\angularjs\recipe>ng serve
An unhandled exception occurred: ENOENT: no such file or directory, lstat 'C:\Users\Eddie\Desktop\angularjs\node_modules'
See "C:\Users\Eddie\AppData\Local\Temp\ng-dCr670\angular-errors.log" for further details.
- Generating browser application bundles (phase: setup)...




```json

    "styles": [
              "./node_modules/bootstrap/dist/css/bootstrap.min.css",
              "src/styles.css",
              ""
            ],
```


Error: Module not found: Error: Can't resolve 'C:\Users\Eddie\Desktop\angularjs\recipe' in 'C:\Users\Eddie\Desktop\angularjs\recipe'

```shell
ng build

```


##### all steps did not work so we need to delete and recreate one using ng new project_name

##### if we do not see the bootstrap change, please update package by npm install --save bootstrap









### add new component 


let's manually create a folder called header 



app.component.html


```html

<div class = "container">
<div class="row">
<div class = "col-md-12"> 
 


<app-header> </app-header>
</div>

</div>

</div>
```



app.component.ts
```TS
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';

import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';

import { FormsModule } from '@angular/forms'

import { HeaderComponent } from './header/header.component';

@NgModule({
  declarations: [
    AppComponent,
    HeaderComponent,

  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    FormsModule,
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }


```


header.component.html
```html



<h1> this is the header</h1>
```




header.component.ts


```TS

import { Component } from '@angular/core';


@Component({
  selector: 'app-header',
  templateUrl: './header.component.html',
  styleUrls: ['./header.component.css']
})
export class HeaderComponent {
  name = 'lec1p1';
}

```






## ng g c project --skipFalse true 




C:\Users\Eddie\Desktop\angularjs\lec1p1>cd app
The system cannot find the path specified.

C:\Users\Eddie\Desktop\angularjs\lec1p1>dir
 Volume in drive C has no label.
 Volume Serial Number is 0697-3EFD

 Directory of C:\Users\Eddie\Desktop\angularjs\lec1p1

2022-01-21  09:22 PM    <DIR>          .
2022-01-21  09:19 PM    <DIR>          ..
2022-01-21  09:22 PM    <DIR>          .angular
2022-01-21  09:19 PM               600 .browserslistrc
2022-01-21  09:19 PM               274 .editorconfig
2022-01-21  09:19 PM               548 .gitignore
2022-01-21  09:19 PM    <DIR>          .vscode
2022-01-21  09:29 PM             3,104 angular.json
2022-01-21  09:19 PM             1,423 karma.conf.js
2022-01-21  09:30 PM    <DIR>          node_modules
2022-01-21  09:30 PM           742,859 package-lock.json
2022-01-21  09:23 PM             1,097 package.json
2022-01-21  09:19 PM             1,052 README.md
2022-01-21  09:19 PM    <DIR>          src
2022-01-21  09:19 PM               287 tsconfig.app.json
2022-01-21  09:19 PM               863 tsconfig.json
2022-01-21  09:19 PM               333 tsconfig.spec.json
              11 File(s)        752,440 bytes
               6 Dir(s)  53,837,463,552 bytes free

C:\Users\Eddie\Desktop\angularjs\lec1p1>cd src

C:\Users\Eddie\Desktop\angularjs\lec1p1\src>dir
 Volume in drive C has no label.
 Volume Serial Number is 0697-3EFD

 Directory of C:\Users\Eddie\Desktop\angularjs\lec1p1\src

2022-01-21  09:19 PM    <DIR>          .
2022-01-21  09:22 PM    <DIR>          ..
2022-01-21  09:45 PM    <DIR>          app
2022-01-21  09:19 PM    <DIR>          assets
2022-01-21  09:19 PM    <DIR>          environments
2022-01-21  09:19 PM               948 favicon.ico
2022-01-21  09:19 PM               292 index.html
2022-01-21  09:19 PM               372 main.ts
2022-01-21  09:19 PM             2,338 polyfills.ts
2022-01-21  09:19 PM                80 styles.css
2022-01-21  09:19 PM               745 test.ts
               6 File(s)          4,775 bytes
               5 Dir(s)  53,837,463,552 bytes free

C:\Users\Eddie\Desktop\angularjs\lec1p1\src>cd app

C:\Users\Eddie\Desktop\angularjs\lec1p1\src\app>dir
 Volume in drive C has no label.
 Volume Serial Number is 0697-3EFD

 Directory of C:\Users\Eddie\Desktop\angularjs\lec1p1\src\app

2022-01-21  09:45 PM    <DIR>          .
2022-01-21  09:19 PM    <DIR>          ..
2022-01-21  09:19 PM               245 app-routing.module.ts
2022-01-21  09:19 PM                 0 app.component.css
2022-01-21  09:42 PM               124 app.component.html
2022-01-21  09:19 PM             1,073 app.component.spec.ts
2022-01-21  09:19 PM               210 app.component.ts
2022-01-21  09:57 PM               625 app.module.ts
2022-01-21  09:42 PM    <DIR>          header
2022-01-21  09:45 PM    <DIR>          recipe
               6 File(s)          2,277 bytes
               4 Dir(s)  53,837,398,016 bytes free

C:\Users\Eddie\Desktop\angularjs\lec1p1\src\app>ng g c recipe/recipe-list
CREATE src/app/recipe/recipe-list/recipe-list.component.html (26 bytes)
CREATE src/app/recipe/recipe-list/recipe-list.component.spec.ts (655 bytes)
CREATE src/app/recipe/recipe-list/recipe-list.component.ts (294 bytes)
CREATE src/app/recipe/recipe-list/recipe-list.component.css (0 bytes)
UPDATE src/app/app.module.ts (732 bytes)

C:\Users\Eddie\Desktop\angularjs\lec1p1\src\app>

C:\Users\Eddie\Desktop\angularjs\lec1p1>cd app
The system cannot find the path specified.

C:\Users\Eddie\Desktop\angularjs\lec1p1>dir
 Volume in drive C has no label.
 Volume Serial Number is 0697-3EFD

 Directory of C:\Users\Eddie\Desktop\angularjs\lec1p1

2022-01-21  09:22 PM    <DIR>          .
2022-01-21  09:19 PM    <DIR>          ..
2022-01-21  09:22 PM    <DIR>          .angular
2022-01-21  09:19 PM               600 .browserslistrc
2022-01-21  09:19 PM               274 .editorconfig
2022-01-21  09:19 PM               548 .gitignore
2022-01-21  09:19 PM    <DIR>          .vscode
2022-01-21  09:29 PM             3,104 angular.json
2022-01-21  09:19 PM             1,423 karma.conf.js
2022-01-21  09:30 PM    <DIR>          node_modules
2022-01-21  09:30 PM           742,859 package-lock.json
2022-01-21  09:23 PM             1,097 package.json
2022-01-21  09:19 PM             1,052 README.md
2022-01-21  09:19 PM    <DIR>          src
2022-01-21  09:19 PM               287 tsconfig.app.json
2022-01-21  09:19 PM               863 tsconfig.json
2022-01-21  09:19 PM               333 tsconfig.spec.json
              11 File(s)        752,440 bytes
               6 Dir(s)  53,837,463,552 bytes free

C:\Users\Eddie\Desktop\angularjs\lec1p1>cd src

C:\Users\Eddie\Desktop\angularjs\lec1p1\src>dir
 Volume in drive C has no label.
 Volume Serial Number is 0697-3EFD

 Directory of C:\Users\Eddie\Desktop\angularjs\lec1p1\src

2022-01-21  09:19 PM    <DIR>          .
2022-01-21  09:22 PM    <DIR>          ..
2022-01-21  09:45 PM    <DIR>          app
2022-01-21  09:19 PM    <DIR>          assets
2022-01-21  09:19 PM    <DIR>          environments
2022-01-21  09:19 PM               948 favicon.ico
2022-01-21  09:19 PM               292 index.html
2022-01-21  09:19 PM               372 main.ts
2022-01-21  09:19 PM             2,338 polyfills.ts
2022-01-21  09:19 PM                80 styles.css
2022-01-21  09:19 PM               745 test.ts
               6 File(s)          4,775 bytes
               5 Dir(s)  53,837,463,552 bytes free

C:\Users\Eddie\Desktop\angularjs\lec1p1\src>cd app

C:\Users\Eddie\Desktop\angularjs\lec1p1\src\app>dir
 Volume in drive C has no label.
 Volume Serial Number is 0697-3EFD

 Directory of C:\Users\Eddie\Desktop\angularjs\lec1p1\src\app

2022-01-21  09:45 PM    <DIR>          .
2022-01-21  09:19 PM    <DIR>          ..
2022-01-21  09:19 PM               245 app-routing.module.ts
2022-01-21  09:19 PM                 0 app.component.css
2022-01-21  09:42 PM               124 app.component.html
2022-01-21  09:19 PM             1,073 app.component.spec.ts
2022-01-21  09:19 PM               210 app.component.ts
2022-01-21  09:57 PM               625 app.module.ts
2022-01-21  09:42 PM    <DIR>          header
2022-01-21  09:45 PM    <DIR>          recipe
               6 File(s)          2,277 bytes
               4 Dir(s)  53,837,398,016 bytes free

C:\Users\Eddie\Desktop\angularjs\lec1p1\src\app>ng g c recipe/recipe-list
CREATE src/app/recipe/recipe-list/recipe-list.component.html (26 bytes)
CREATE src/app/recipe/recipe-list/recipe-list.component.spec.ts (655 bytes)
CREATE src/app/recipe/recipe-list/recipe-list.component.ts (294 bytes)
CREATE src/app/recipe/recipe-list/recipe-list.component.css (0 bytes)
UPDATE src/app/app.module.ts (732 bytes)

C:\Users\Eddie\Desktop\angularjs\lec1p1\src\app>

                                                                                                                                                                                 C:\Users\Eddie\Desktop\angularjs\lec1p1\src\app>ng g c recipe/recipe-detail/reicpe-item                                                                                          CREATE src/app/recipe/recipe-detail/reicpe-item/reicpe-item.component.html (26 bytes)                                                                                            CREATE src/app/recipe/recipe-detail/reicpe-item/reicpe-item.component.spec.ts (655 bytes)                                                                                        CREATE src/app/recipe/recipe-detail/reicpe-item/reicpe-item.component.ts (294 bytes)                                                                                             CREATE src/app/recipe/recipe-detail/reicpe-item/reicpe-item.component.css (0 bytes)                                                                                              UPDATE src/app/app.module.ts (968 bytes)                     



C:\Users\Eddie\Desktop\angularjs\lec1p1\src\app>ng g c shopping-list
CREATE src/app/shopping-list/shopping-list.component.html (28 bytes)
CREATE src/app/shopping-list/shopping-list.component.spec.ts (669 bytes)
CREATE src/app/shopping-list/shopping-list.component.ts (302 bytes)
CREATE src/app/shopping-list/shopping-list.component.css (0 bytes)
UPDATE src/app/app.module.ts (1076 bytes)


C:\Users\Eddie\Desktop\angularjs\lec1p1\src\app>ng g c recipe/recipe-list/recipe-item
CREATE src/app/recipe/recipe-list/recipe-item/recipe-item.component.html (26 bytes)
CREATE src/app/recipe/recipe-list/recipe-item/recipe-item.component.spec.ts (655 bytes)
CREATE src/app/recipe/recipe-list/recipe-item/recipe-item.component.ts (294 bytes)
CREATE src/app/recipe/recipe-list/recipe-item/recipe-item.component.css (0 bytes)
UPDATE src/app/app.module.ts (1195 bytes)

C:\Users\Eddie\Desktop\angularjs\lec1p1\src\app>

C:\Users\Eddie\Desktop\angularjs\lec1p1\src\app>ng g c shopping-list/shopping-edit
CREATE src/app/shopping-list/shopping-edit/shopping-edit.component.html (28 bytes)
CREATE src/app/shopping-list/shopping-edit/shopping-edit.component.spec.ts (669 bytes)
CREATE src/app/shopping-list/shopping-edit/shopping-edit.component.ts (302 bytes)
CREATE src/app/shopping-list/shopping-edit/shopping-edit.component.css (0 bytes)
UPDATE src/app/app.module.ts (1317 bytes)



in app.component.html 



```html

<div class = "container">
<div class="row">
<div class = "col-md-12"> 
 


<app-header> </app-header>

<app-recipe> </app-recipe>

<app-shopping-list></app-shopping-list>


</div>

</div>

</div>
```


in the recipes.component.html

```html

<div class = "row">
<div class = "col-md-5">
<app-recipe-list> </app-recipe-list>
<app-recipe-detail> </app-recipe-detail>

</div>

<div class = "col-md-7">
	</div>

</div>
```



in recipe-list.component.html

```html

<app-recipe-item></app-recipe-item>
```

in shopping-list html 


```html

<div class = "row">
<div class = "col-xs-10">

	<app-shopping-edit></app-shopping-edit>
	<hr>

	<p> this is my shopping list with edit on top </p>

</div>


</div>

```


let's add a navbar in the header:



```html


<app-header> </app-header>

<div class = "container">
<div class="row">
<div class = "col-md-12"> 
 




<app-recipe> </app-recipe>

<app-shopping-list></app-shopping-list>


</div>

</div>

</div>
```






## model 

what is a model? a model is simply a typescript file 

it should be descriptive such as xxx.model.ts



create recipe-model.ts

we need to export this class


```TS
export class ClassName{

}

```



```TS
export class Recipe{

	public name:string;
	public description: string;
	public imagePath : string;

	constructor(name:string, desc:string, imagePath:string){
		this.name = name;
		this.description = desc;
		this.imagePath = imagePath;
	}
}
```


In recipe-list.component.ts 


```TS
import { Component, OnInit } from '@angular/core';


import { Recipe } from '../recipe-model';

@Component({
  selector: 'app-recipe-list',
  templateUrl: './recipe-list.component.html',
  styleUrls: ['./recipe-list.component.css']
})
export class RecipeListComponent implements OnInit {

  recipes : Recipe [] = [
 new Recipe('a test ', 'this is a image', 'https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.pexels.com%2Fsearch%2Ffood%2F&psig=AOvVaw1yJ6S4TKtepEPQ-mb1EEkI&ust=1642909514010000&source=images&cd=vfe&ved=0CAsQjRxqFwoTCIjN2YG5xPUCFQAAAAAdAAAAABAJ'),
 
new Recipe('b test', 'this is b image', 'https://www.google.com/url?sa=i&url=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FFood&psig=AOvVaw1yJ6S4TKtepEPQ-mb1EEkI&ust=1642909514010000&source=images&cd=vfe&ved=0CAsQjRxqFwoTCIjN2YG5xPUCFQAAAAAdAAAAABAO'),
  ];


  constructor() { }

  ngOnInit(): void {
  }

}


```

