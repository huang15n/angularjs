

angular is a javascript framework which allows you to create reactive single page applications SPAs, javscript changes the DOM, changes whatever is displayed in html during runtime 


angular has updates for incremental, backward compatibility every six months.






## Install angular js 

download nodejs: https://nodejs.org/en/




download angularjs: https://angularjs.org/ 
or we will use official angular command line interface



https://angular.io/cli

```shell

npm install -g @angular/cli

ng new my-app --no-strict
## would you like to add angular routing? No 
## stylesheet CSS
cd my-app
ng serve
```



```javascript 

import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'my-app';
}

```

ts file is the definition of our components which will be converted to javascript by workflow 
there is title = "", you you go back to app.component.html 
this is related to that, this is called **data biding**

<ap-root> is something that we see in the app.component.ts file they are injected dynamically 
then we hae these dynamically injected script imports and will replace ap-root with our components 




let's go to app.component.html

```html

<input type = "text" [(ngModel)] = "name">

<p> {{name}}</p>
```

and app.compnent.ts

```javascript

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

app.modules.ts

```javascript 
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';

import { AppComponent } from './app.component';
import { FormsModule } from '@angular/forms';
 


@NgModule({
  declarations: [
    AppComponent
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





components/ data binding -> directives -> services & dependency injection -> routing -> observables -> forms -> piepes -> http -> authenticate -> optimizations 




## TypeScript


TypeScript is the suset of javascript more features than vanilla js which is strongly typed 
it is technically possible that TypeScript compiled to javascript, it is an addition to javascript 







## Bootstrap setup 

we need to download bootstrap , it is downloaded locally not globally 



```shell
npm install --save boostrap@3

```

C:\Users\Eddie\Desktop\angularjs\p1\my-app>npm install --save bootstrap@3

added 1 package, removed 1 package, and audited 1011 packages in 4s

91 packages are looking for funding
  run `npm fund` for details

40 vulnerabilities (3 low, 37 moderate)

To address issues that do not require attention, run:
  npm audit fix

To address all issues (including breaking changes), run:
  npm audit fix --force

Run `npm audit` for details.





angular.json configures the project 
we need to change "styles "
"node_modules/bootstrap/dist/css/boostrap.min.css"


```json
 "styles": [
              "src/styles.css",
			  "node_modules/bootstrap/dist/css/bootstrap.min.css"
            ],
           

```


restart the server using ng serve 








