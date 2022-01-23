## TODO https://angular.io/guide/inputs-outputs


# Keynote 
1. import {FormsMudle} from '@angular/forms';
2. imports : [FormsModule]
3. [(ngModule)] = "variableNames"
4. (event/click) = "methodName()"
5. {{variable}}
6. <tagname *ngFor = "let item of list"> </tagname>


# Debugging 


find error message in the conole 
in source developer tools you ca set a breakpoint 





# Component & Databinding 

split up makese sense because it would allow us if we build a bigger app 


let's make an add list 
C:\Users\Eddie\Desktop\angularjs>ng new listExample
? Would you like to add Angular routing? No
? Which stylesheet format would you like to use? CSS
CREATE listExample/angular.json (3070 bytes)
CREATE listExample/package.json (1076 bytes)
CREATE listExample/README.md (1057 bytes)
CREATE listExample/tsconfig.json (863 bytes)
CREATE listExample/.editorconfig (274 bytes)
CREATE listExample/.gitignore (548 bytes)
CREATE listExample/.browserslistrc (600 bytes)
CREATE listExample/karma.conf.js (1429 bytes)
CREATE listExample/tsconfig.app.json (287 bytes)
CREATE listExample/tsconfig.spec.json (333 bytes)
CREATE listExample/.vscode/extensions.json (130 bytes)
CREATE listExample/.vscode/launch.json (474 bytes)
CREATE listExample/.vscode/tasks.json (938 bytes)
CREATE listExample/src/favicon.ico (948 bytes)
CREATE listExample/src/index.html (297 bytes)
CREATE listExample/src/main.ts (372 bytes)
CREATE listExample/src/polyfills.ts (2338 bytes)
CREATE listExample/src/styles.css (80 bytes)
CREATE listExample/src/test.ts (745 bytes)
CREATE listExample/src/assets/.gitkeep (0 bytes)
CREATE listExample/src/environments/environment.prod.ts (51 bytes)
CREATE listExample/src/environments/environment.ts (658 bytes)
CREATE listExample/src/app/app.module.ts (314 bytes)
CREATE listExample/src/app/app.component.html (23332 bytes)
CREATE listExample/src/app/app.component.spec.ts (971 bytes)
CREATE listExample/src/app/app.component.ts (215 bytes)
CREATE listExample/src/app/app.component.css (0 bytes)
√ Packages installed successfully.
warning: LF will be replaced by CRLF in .browserslistrc.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in .editorconfig.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in .gitignore.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in .vscode/extensions.json.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in .vscode/launch.json.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in .vscode/tasks.json.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in README.md.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in angular.json.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in karma.conf.js.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in package-lock.json.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in package.json.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in src/app/app.component.html.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in src/app/app.component.spec.ts.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in src/app/app.component.ts.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in src/app/app.module.ts.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in src/environments/environment.prod.ts.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in src/environments/environment.ts.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in src/index.html.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in src/main.ts.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in src/polyfills.ts.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in src/styles.css.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in src/test.ts.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in tsconfig.app.json.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in tsconfig.json.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in tsconfig.spec.json.
The file will have its original line endings in your working directory
    Successfully initialized git.

C:\Users\Eddie\Desktop\angularjs>


C:\Users\Eddie\Desktop\angularjs>cd listExample

C:\Users\Eddie\Desktop\angularjs\listExample>npm intall --save bootstrap
Unknown command: "intall"

Did you mean this?
    npm install # Install a package

To see a list of supported npm commands, run:
  npm help

C:\Users\Eddie\Desktop\angularjs\listExample>npm install --save bootstrap

added 2 packages, and audited 893 packages in 5s

94 packages are looking for funding
  run `npm fund` for details

6 vulnerabilities (3 low, 3 moderate)

To address all issues (including breaking changes), run:
  npm audit fix --force

Run `npm audit` for details.



C:\Users\Eddie\Desktop\angularjs\listExample>npm install --save bootstrap

C:\Users\Eddie\Desktop\angularjs\listExample>

C:\Users\Eddie\Desktop\angularjs\listExample>npm install --save bootstrap

removed 1 package, and audited 893 packages in 6s

94 packages are looking for funding
  run `npm fund` for details

6 vulnerabilities (3 low, 3 moderate)

To address all issues (including breaking changes), run:
  npm audit fix --force

Run `npm audit` for details.

C:\Users\Eddie\Desktop\angularjs\listExample>ng serve
√ Browser application bundle generation complete.

Initial Chunk Files   | Names         |  Raw Size
vendor.js             | vendor        |   1.73 MB |
styles.css, styles.js | styles        | 373.25 kB |
polyfills.js          | polyfills     | 339.24 kB |
runtime.js            | runtime       |   6.86 kB |
main.js               | main          |   5.97 kB |

                      | Initial Total |   2.44 MB

Build at: 2022-01-22T21:00:42.197Z - Hash: d993fba4a2d3651e - Time: 8516ms

** Angular Live Development Server is listening on localhost:4200, open your browser on http://localhost:4200/ **


√ Compiled successfully.

C:\Users\Eddie\Desktop\angularjs\listExample>
C:\Users\Eddie\Desktop\angularjs\listExample>dir
 Volume in drive C has no label.
 Volume Serial Number is 0697-3EFD

 Directory of C:\Users\Eddie\Desktop\angularjs\listExample

2022-01-22  03:56 PM    <DIR>          .
2022-01-22  03:51 PM    <DIR>          ..
2022-01-22  03:56 PM    <DIR>          .angular
2022-01-22  03:51 PM               600 .browserslistrc
2022-01-22  03:51 PM               274 .editorconfig
2022-01-22  03:51 PM               548 .gitignore
2022-01-22  03:51 PM    <DIR>          .vscode
2022-01-22  03:57 PM             3,137 angular.json
2022-01-22  03:51 PM             1,429 karma.conf.js
2022-01-22  04:00 PM    <DIR>          node_modules
2022-01-22  04:00 PM           743,712 package-lock.json
2022-01-22  03:53 PM             1,103 package.json
2022-01-22  03:51 PM             1,057 README.md
2022-01-22  03:51 PM    <DIR>          src
2022-01-22  03:51 PM               287 tsconfig.app.json
2022-01-22  03:51 PM               863 tsconfig.json
2022-01-22  03:51 PM               333 tsconfig.spec.json
              11 File(s)        753,343 bytes
               6 Dir(s)  52,535,296,000 bytes free

C:\Users\Eddie\Desktop\angularjs\listExample>ng g c listOne
CREATE src/app/list-one/list-one.component.html (23 bytes)
CREATE src/app/list-one/list-one.component.spec.ts (634 bytes)
CREATE src/app/list-one/list-one.component.ts (282 bytes)
CREATE src/app/list-one/list-one.component.css (0 bytes)
UPDATE src/app/app.module.ts (402 bytes)

C:\Users\Eddie\Desktop\angularjs\listExample>
C:\Users\Eddie\Desktop\angularjs\listExample>ng g c listTwo
CREATE src/app/list-two/list-two.component.html (23 bytes)
CREATE src/app/list-two/list-two.component.spec.ts (634 bytes)
CREATE src/app/list-two/list-two.component.ts (282 bytes)
CREATE src/app/list-two/list-two.component.css (0 bytes)
UPDATE src/app/app.module.ts (490 bytes)

C:\Users\Eddie\Desktop\angularjs\listExample>


in app.component.ts 

```html


<div class = "row">
  <div class = "container">
<h1> this is the list app </h1>


<app-list-one> </app-list-one>
<app-list-two> </app-list-two>

</div>

</div>
```






core.mjs:6461 ERROR Error: If ngModel is used within a form tag, either the name attribute must be set or the form
    control must be defined as 'standalone' in ngModelOptions.


```TS

import { Component, OnInit } from '@angular/core';

import { ModelOne } from './list-one-model';

@Component({
  selector: 'app-list-one',
  templateUrl: './list-one.component.html',
  styleUrls: ['./list-one.component.css']
})
export class ListOneComponent implements OnInit {
 resultList: ModelOne [] = [];
 value : string = "";

  constructor() {

   

   }


   addElement(){
    this.resultList.push(new ModelOne(this.resultList.length + 1, this.value));

   }


 

  ngOnInit(): void {
  }

}

```


```html


 <div class="form-group">
    
    <input type="text" class="form-control" [(ngModel)] = "value" name = "value">
  </div>
```




the list app is here: 
list-one.component.htm; 
```html

<div class = "row">

	<div class = "container-fluid">
<form>
  
  <div class="form-group">
    
    <input type="text" class="form-control" [(ngModel)] = "value" name = "value">
  </div>
 
 
  <button type="submit" class="btn btn-primary" (click) = "addElement()">Submit</button>
   <button type="submit" class="btn btn-danger" (click) = "deleteElement()">Delete</button>
</form>

<div *ngFor = "let element of resultList" >
	<p>
{{ element.id}} | {{element.value}}
</p>

 </div>




</div>
</div>




```



list-one.component.ts 


```TS
import { Component, OnInit } from '@angular/core';

import { ModelOne } from './list-one-model';

@Component({
  selector: 'app-list-one',
  templateUrl: './list-one.component.html',
  styleUrls: ['./list-one.component.css']
})
export class ListOneComponent implements OnInit {
 resultList: ModelOne [] = [];
 value : string = "";

  constructor() {

   

   }


   addElement(){
    console.log(this.resultList);
    this.resultList.push(new ModelOne(this.resultList.length + 1, this.value));

   }

   deleteElement(){
    if(this.resultList.length != 0){
      this.resultList.pop();
    }

   }


 

  ngOnInit(): void {
  }

}

```


list-one-moddel.ts 


```TS




export class ModelOne{

     id : number;
	value: string;

	constructor(id: number, value: string){
		this.id = id;
		this.value = value;
	}




}
```

app.module.ts
```TS

import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';

import { AppComponent } from './app.component';
import { ListOneComponent } from './list-one/list-one.component';
import { ListTwoComponent } from './list-two/list-two.component';
import { FormsModule } from '@angular/forms';

@NgModule({
  declarations: [
    AppComponent,
    ListOneComponent,
    ListTwoComponent,


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


app.component.ts
```TS


<div class = "row">
  <div class = "container">
<h1> this is the list app </h1>


<app-list-one> </app-list-one>
<app-list-two> </app-list-two>

</div>

</div>


```



## property & event binding 
property and event binding we used as (enable) = "variableTrueOrFalse"
we passed the info that it should be disabled that this is set to true to this html element 


1. we can use html elements to native properties & events 


2. we can also use directives with custom properties & events ngClass / ngStyle 

3. we can also use components to bind with custom properties & events 



## binding to custom properties  @Input from parent to child 

use 

```TS

// in the sub component.ts  we cannot access from outside 
variable : {attribute1 : typeOne, attribute2 : typeTwo, attribute3 : typeThree};


// in the app.component 

element = [ {attribute1: value1,attribute2: value2,attribute3: value3}]

```

we cannot do this, in app component.html, because it is not known of the sub element, by default, all components are visibles inside these component not outside, you do not want to make your properties bindable from outside 

```html 

<app-sub-element *ngFor = "let element of elements " [variable] = "element"> </app-sub-elmement>



```



you need to add a decorator called @Input , any parent component is now able to access it down to that custom component through selctor 
```TS

import {Input} from '@angular/core';

@Input ()variable : {attribute1 : typeOne, attribute2 : typeTwo, attribute3 : typeThree};

```

In app.component.ts

```TS

import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'listExample';

  elementsExample = [{attributeOne: "this is attributeOne", attributeTwo : 1},{attributeOne: "this is attributeTwo", attributeTwo : 2}]


}


```

in subcomponent.ts 


```TS

import { Component, OnInit, Input } from '@angular/core';



@Component({
  selector: 'app-list-two',
  templateUrl: './list-two.component.html',
  styleUrls: ['./list-two.component.css']
})
export class ListTwoComponent implements OnInit {
  @Input () element! : { attributeOne: string, attributeTwo: number};

  constructor() { }

  ngOnInit(): void {
  }

}

```

subcomponent.html
```html

<p>list-two works!</p>


{{element.attributeOne}} | {{element.attributeTwo}}

```


## assiging an alias to custom properties 
somtimes you do not want to use an outside component inside this component 
you might say element is exactly the property name , now the original name will no longer work outside the component 


```TS

import {Input} from '@angular/core';

@Input ('AliasName') variable : {attribute1 : typeOne, attribute2 : typeTwo, attribute3 : typeThree};

```




```TS
import { Component, OnInit, Input } from '@angular/core';



@Component({
  selector: 'app-list-two',
  templateUrl: './list-two.component.html',
  styleUrls: ['./list-two.component.css']
})
export class ListTwoComponent implements OnInit {
  @Input ('randomShit') element! : { attributeOne: string, attributeTwo: number};

  constructor() { }

  ngOnInit(): void {
  }

}


```

```html


<div class = "row">
  <div class = "container">
<h1> this is the list app </h1>


<app-list-one> </app-list-one>
<app-list-two *ngFor = "let e of  elementsExample" [randomShit] = "e">

 </app-list-two>

</div>

</div>
```

we have done parent component to child component what about backwards???


## binding to custom events  @Output from child to parent 

how to inform parent component? 


app.component.html

```html


<div class = "row">
  <div class = "container">
<h1> this is the list app </h1>


<app-list-one> </app-list-one>
<app-list-two (childEventOne) = "parentEventOne($event)"
(childEventTwo) = "parentEventTwo($event)">

 </app-list-two>

</div>

</div>
```

app.component.ts
```TS
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'listExample';

  elementsExample = [{attributeOne: "this is attributeOne", attributeTwo : 1},{attributeOne: "this is attributeTwo", attributeTwo : 2}]



  parentEventOne(jsObject: {name: string, value: number}){

console.log("this is parent event  1");
  }

  parentEventTwo(jsObject: {name: string, value: number}){
console.log("this is parent event  2");

  }


}


```

subcomponent.ts


```TS

import { Component, OnInit, EventEmitter, Output } from '@angular/core';



@Component({
  selector: 'app-list-two',
  templateUrl: './list-two.component.html',
  styleUrls: ['./list-two.component.css']
})
export class ListTwoComponent implements OnInit {
  

@Output () childEventOne = new EventEmitter<{name: string, value:number}>();
@Output () childEventTwo = new EventEmitter<{name: string, value:number}>();


  constructor() { }

  ngOnInit(): void {
  }


  parentEventOne(){
    this.childEventOne.emit({name: "hello", value : 1});
  }

  parentEventTwo(){
    this.childEventTwo.emit({name: "world", value : 2});
  }

}

```

```html


<div class = "row">
  <div class = "container">
<h1> this is the list app </h1>


<app-list-one> </app-list-one>
<app-list-two (childEventOne) = "parentEventOne($event)"
(childEventTwo) = "parentEventTwo($event)">

 </app-list-two>

</div>

</div>

```


### asssiniging an alias to custom event


in the subcomponent.ts 

```TS


import { Component, OnInit, EventEmitter, Output } from '@angular/core';



@Component({
  selector: 'app-list-two',
  templateUrl: './list-two.component.html',
  styleUrls: ['./list-two.component.css']
})
export class ListTwoComponent implements OnInit {
  

@Output ("randomShitOne") childEventOne = new EventEmitter<{name: string, value:number}>();
@Output ("randomShitTwo") childEventTwo = new EventEmitter<{name: string, value:number}>();


  constructor() { }

  ngOnInit(): void {
  }


  parentEventOne(){
    this.childEventOne.emit({name: "hello", value : 1});
  }

  parentEventTwo(){
    this.childEventTwo.emit({name: "world", value : 2});
  }

}

```


in app.component.html


```html



<div class = "row">
  <div class = "container">
<h1> this is the list app </h1>


<app-list-one> </app-list-one>
<app-list-two (randomShitOne) = "parentEventOne($event)"
(randomShitTwo) = "parentEventTwo($event)">

 </app-list-two>

</div>

</div>
```


when you want to have components sitting to each other, it will get complicated to emit an evnt in one component change something and these chains can be really complex 




## view encapsulation   encapsulation: ViewEncapsulation.None, OR   encapsulation: ViewEncapsulation.ShadowDom
css rule overriding is defined by angular , all the specific attributes are applied by angular , basically parent's styling cannot be applied to children directly 

it kinda emulates the shadow dom , the shadow dom is a technology not supported by all browsers 
but you can define it in angular child.component.ts 

```TS

import { Component, OnInit, EventEmitter, Output, ViewEncapsulation } from '@angular/core';



@Component({
  selector: 'app-list-two',
  templateUrl: './list-two.component.html',
  styleUrls: ['./list-two.component.css'],
  encapsulation: ViewEncapsulation.None,
})
```


## local reference 
a local reference is to get access to some elements in your template and then use it either directly in the template 
if it is just a simple app and we do not want two way bindings, we can use local reference to achive this 

it will hold the whole html element with all its properties 


you can use this only only in your html templates not the TS code !!!!

```HTML
   <input type="text" class="form-control" [(ngModel)] = "value" name = "value" #giveItAName>
  <button   class="btn btn-info" (click) = "localElement(giveItAName)">local</button>

```


```TS


   localElement(something:any){
    console.log(something.value);
   }

```



### Getting access to the template & DOM with @ViewChild ('', {static:true})
import { Component, OnInit, ViewChild } from '@angular/core';

this @ViewChild('', {static:true}) is the selector we want to select the element not lke a css selector 

```HTML
   <input type="text" class="form-control" [(ngModel)] = "value" name = "value" #giveItAName>
  <button   class="btn btn-info" (click) = "localElement(giveItAName)">local</button>

```


```TS
import { Component, OnInit, ViewChild } from '@angular/core';

 @ViewChild("giveItAName",{static:true}) somethingHere! : HTMLInputElement;
   localElement(){
    console.log(this.somethingHere);
   }


```


#### You can se this as ElementRef 
```TS

import { Component, OnInit, ViewChild, ElementRef } from '@angular/core';

import { ModelOne } from './list-one-model';

@Component({
  selector: 'app-list-one',
  templateUrl: './list-one.component.html',
  styleUrls: ['./list-one.component.css']
})
export class ListOneComponent implements OnInit {
 resultList: ModelOne [] = [];
 value : string = "";
 @ViewChild("giveItAName",{static:true}) somethingHere! : ElementRef;

  constructor() {

   

   }
```


##### Now without two ways binding but local reference past two methods or local reference @ChildView('variable') here , one important thing is you should not use ElementRef.nativeElement.value = "value";  generally you should use directives or string interpolations and property binding and not directly mess with any element 



### project content into components with ng-content 


everything you place between openining and closing tag of your own coomponent is lost by default 

this serves as a hook that you can place in your component to mark the place for angular , you can reuse it to build reusable widgets such as tabs 

You use the <ng-content></ng-content> tag as a placeholder for that dynamic content, then when the template is parsed Angular will replace that placeholder tag with your content.


```html

<ng-content> </ng-content>
```





```ts

import { Component, OnInit, Input } from '@angular/core';

@Component({
  selector: 'app-list-one',
  template : `
 <button class = "btn btn-default" (click) = "add()"> 

 <ng-content></ng-content>
</button>
  `,
  styleUrls: ['./list-one.component.css']
})
export class ListOneComponent implements OnInit {

  @Input() buttonText! : string;

  constructor() { }

  ngOnInit(): void {
  }


  add(){



  }

}

```



```html


<div class = "row">
  <div class = "container">
<h1> this is the list app </h1>


<app-list-one> 
this is the content here wowowowwow 
</app-list-one>


</div>

</div>
```


In the template for the reusable add button component we use the <ng-content></ng-content> tag as our placeholder for the button text. This is telling Angular, “Hey, I don’t know what this is supposed to be right now but, I promise to tell you later”.
Then when the button component is actually being used… BAM! We put whatever text we want inside the component and then Angular will be like “Oh Snap! Now I know what value to use for the button’s text!”.
Pretty cool. It strips out so much of the extra setup we used in the earlier examples. No inputs to keep track of, no hard-coded values in the component. Just set up the original template and worry about it later when you actually need it.
Dynamic text is just the tip of the metaphorical iceberg though. You can put lots of different things inside the component. Including HTML tags and even other components



## ngOnInit() and understanding the component lifecyle 

ngOnInit is the part of lifecyle 

once new component is instantiated , angular goes through a couple of phases 

we can hook into these phases by implementing some methods and angular will call if they are present 


LifeCycle:
1. ngOnChanges called after a bound input property changse 
2. ngOnInit called once the component is initialized...   any difference between constructor and ngOnInit
??

3. ngDoCheck called during every change detection run 

4. ngAfterContentInit called after content ng-content has been projected into view 

5. ngAfterContentChecked called every time the projected content has been checked 

6. ngAfterViewInit called after the component's view and child views has been initalized 

7. ngAfterViewChecked called every time the view and child views have been checked 
8. ngOnDestory called once the component is about to be destroyed 




```TS
import { 
  Component, 
  OnInit, OnChanges, SimpleChanges, DoCheck, AfterContentInit, 
  AfterContentChecked,
AfterViewInit,
AfterViewChecked,
OnDestroy
} from '@angular/core';

@Component({
  selector: 'app-list-one',
  template : `
 <button class = "btn btn-default" > 

 <ng-content></ng-content>
</button>
  `,
  styleUrls: ['./list-one.component.css']
})
export class ListOneComponent implements OnInit, OnChanges, DoCheck, AfterContentInit, AfterContentChecked, AfterViewInit,AfterViewChecked , OnDestroy{

 

  constructor() {
   console.log("constructor is called");
   }

   ngOnChanges(changes: SimpleChanges){

   console.log("ngOnChanges is called");

   }

  ngOnInit(): void {

   console.log("ngOnInit is called ");
  }

  ngDoCheck(){
    console.log("ngDoCheck is called");
    // this checks changs and there are a couple triggers by clicking or a new Promise()
  }

  ngAfterContentInit(){
    console.log("ngAfterContentInit is called");
  }

  ngAfterContentChecked(){
    console.log("ngAfterContentChecked is called");
  }

  ngAfterViewInit(){
    console.log("ngAfterViewInit is called");
  }

  ngAfterViewChecked(){
    console.log("ngAfterContentChecked is called");
  }

  ngOnDestroy(){
    console.log("ngOnDestroy is called when it is destroyed");
  }








 

}


```

ngOnInit is called 
list-one.component.ts:39 ngDoCheck is called
list-one.component.ts:44 ngAfterContentInit is called
list-one.component.ts:48 ngAfterContentChecked is called
list-one.component.ts:52 ngAfterViewInit is called
list-one.component.ts:56 ngAfterContentChecked is called
core.mjs:24833 Angular is running in development mode. Call enableProdMode() to enable production mode.
list-one.component.ts:39 ngDoCheck is called
list-one.component.ts:48 ngAfterContentChecked is called
list-one.component.ts:56 ngAfterContentChecked is called
index.js:548 [webpack-dev-server] Live Reloading enabled.
index.js:548 [webpack-dev-server] App updated. Recompiling...
index.js:548 [webpack-dev-server] Nothing changed.




## template access and lifcyle hooks  @ViewChild, ElementRef

```TS

import { 
  Component, 
  OnInit, OnChanges, SimpleChanges, DoCheck, AfterContentInit, 
  AfterContentChecked,
AfterViewInit,
AfterViewChecked,
OnDestroy,
ViewChild,
ElementRef
} from '@angular/core';

@Component({
  selector: 'app-list-one',
  template : `
 <button class = "btn btn-default" > 

 <ng-content></ng-content>
</button>
<p #heading> this is me </p>
  `,
  styleUrls: ['./list-one.component.css']
})
export class ListOneComponent implements OnInit, OnChanges, DoCheck, AfterContentInit, AfterContentChecked, AfterViewInit, AfterViewChecked , OnDestroy{

@ViewChild('heading', {static:true}) header! : ElementRef; 

  constructor() {
   console.log("constructor is called");
   }

   ngOnChanges(changes: SimpleChanges){

   console.log("ngOnChanges is called");

   }

  ngOnInit(): void {

   console.log("ngOnInit is called ");
  }

  ngDoCheck(){
    console.log("ngDoCheck is called");
    // this checks changs and there are a couple triggers by clicking or a new Promise()
  }

  ngAfterContentInit(){
    console.log("ngAfterContentInit is called");
  }

  ngAfterContentChecked(){
    console.log("ngAfterContentChecked is called");
  }

  ngAfterViewInit(){
    console.log("ngAfterViewInit is called");
    console.log(this.header.nativeElement.textContent);
  }

  ngAfterViewChecked(){
    console.log("ngAfterContentChecked is called");
  }

  ngOnDestroy(){
    console.log("ngOnDestroy is called when it is destroyed");
  }








 

}

```

## @ContentChild and ng-content 
```TS

import { 
  Component, 
  OnInit, OnChanges, SimpleChanges, DoCheck, AfterContentInit, 
  AfterContentChecked,
AfterViewInit,
AfterViewChecked,
OnDestroy,
ViewChild,
ElementRef,
ContentChild,
} from '@angular/core';

@Component({
  selector: 'app-list-one',
  template : `
 <button class = "btn btn-default" > 

 <ng-content></ng-content>
</button>
<p> this is me </p>
  `,
  styleUrls: ['./list-one.component.css']
})
export class ListOneComponent implements OnInit, OnChanges, DoCheck, AfterContentInit, AfterContentChecked, AfterViewInit, AfterViewChecked , OnDestroy{

// @ViewChild('heading', {static:true}) header! : ElementRef; 
@ContentChild('heading',{static:true}) header! : ElementRef;

  constructor() {
   console.log("constructor is called");
   }

   ngOnChanges(changes: SimpleChanges){

   console.log("ngOnChanges is called");

   }

  ngOnInit(): void {

   console.log("ngOnInit is called ");
  }

  ngDoCheck(){
    console.log("ngDoCheck is called");
    // this checks changs and there are a couple triggers by clicking or a new Promise()
  }

  ngAfterContentInit(){
    console.log("ngAfterContentInit is called");
  }

  ngAfterContentChecked(){
    console.log("ngAfterContentChecked is called");
  }

  ngAfterViewInit(){
    console.log("ngAfterViewInit is called");
    console.log(this.header);
  }

  ngAfterViewChecked(){
    console.log("ngAfterContentChecked is called");
  }

  ngOnDestroy(){
    console.log("ngOnDestroy is called when it is destroyed");
  }








 

}

```








### error 
src/app/list-two/list-two.component.ts:11:13 - error TS2564: Property 'element' has no initializer and is not definitely assigned in the constructor.


you can add variable!: typename




## type script syntax note

1. an array with class type defined as variableName ; ClassType [] = []
2. add an object to an array is variableName.push(ClassType(eleme....))
3. delete the last elment in an array is variableName.pop()


4. getter and setter in type script is declared as 


```TS
public set xxx(variable:type){

}

public get xxx(){
    return this.variable;
}

```




