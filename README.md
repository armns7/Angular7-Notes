# Angular7-Notes
I took these notes while watching Udemy course. Might be helpful to some one!

====================================================================

			Angular Building Blocks

====================================================================

- Data Binding Uses

	- Communication

	- Output Data

		- String Interpolation		{ Template (HTML) }

		- Property Binding	 	{ Template (HTML) }

- Data Binding Types

	- Expressions

	- String Interpolation

		- {{ code }}

- Property Binding

	- E.g <button [disabled]="isBtnDisabled"> Click! </button>

	- E.g <p> fooModelName <p>	

	- E.g <p [innerText]="fooModelName()"><p>

- Event Binding

	- Syntax

		- (click)="OnEventTriggered()"

	- $event pass event from html 

- Two Way Binding

	- Syntax 

		- [(ngModel)]="userName"

- Directive 

	- Instructions in DOM

	- There are also built in directives

	- Components

		- Directives with a template. (instruction in DOM to replace it with a template)

	- Structural

		- Change the DOM layout/structure by adding and removing DOM elements.

		- *ngIf ? 

		- Why * in angular directives

			- Angular turn * into ng-template tag

				- <div *ng-if="condition"> </div>

			- Otherwise it would be

				- <ng-template [ng-if]="condition"> </ng-template>

			- A sytactic sugar

		- Cant have more than 1 structural directive on an element

		- ng-swtich

			- <div [ngSwitch]="value">   <p *ngSwitchCase="1"> One </p>  <p *ngSwitchDefault> Error </p> </div>

	- Attribute

		- Change the appearance or behavior of an element, component, or another directive, thery dont add or remove elements

		- [ngStyle] = " { backgroundColor: 'red' } " or [ngStyle] = " { backgroundColor: getBgColor() } "

		- [ngClass]

			- <some-element [ngClass]="'first second'">...</some-element>

			- <some-element [ngClass]="['first', 'second']">...</some-element>

			- <some-element [ngClass]="{'first': true, 'second': true, 'third': false}">...</some-element>

			- <some-element [ngClass]="stringExp|arrayExp|objExp">...</some-element>

			- <some-element [ngClass]="{'class1 class2 class3' : true}">...</some-element>

		- *ngFor

			- Converted to

				- <ng-template [ngIf]="Expression"> </ng-template>

- Property Binding Syntax

	- <span defaultColor="red"> </span>

	- <span [defaultColor]="'red'"> </span>

		

- Local reference

	- Can be set on html for referencing element to access from Classes(components, directives, etc)

	- <p #localRefOfp> </p>

- Renderer

	- Renderer for any DOM manipulations

	- In scenarios When in service workers you dont have access to DOM, renderes come in handy 

- @HostListener

	- Decorator that helps to listen events(any) on the host element or component, and provides a handler method to run when that event occurs.

	- Can Custom Events can also be created ?  

- @HostBinding

	- Decorator that helps to set properties(any) on the element or component that hosts the directive 

	- If directive selector and hostbinding alias is same it can be used as

		- <span [textColorHighlight]="'red'"> </span>

	- @HostBinding('class.hightlightText') isApplyClass = false || true;	

		- If its false hightlightText class would be remove from the element

 		- If its true hightlightText class would be applied to the element

- ng-template

	- Directive with * is converted to this

- Routing

	- <router-outlet>

		- where selected route's component would be rendered

	- Ways to construct routes

		- [routerLink]="'/home'"

		- routerLink="/home"

		- [routerLink]="['/home']"

		- Used forward slash "/" for absolute paths

		- Path can be relative of absolute

		- Go up one level "../"

		- Redirecting route

		- Wildcards in routes



	- Route Params can be passed as well

	- Routes can be nested via children property

	- Manage routes in seperate file and module

	- Route Gaurds

		- canActivate gaurds the route against some login e.g authentication

		- canActivateChild

		- canDeactivate

		- resolve gaurd

	

	- Dynamic Error can be passed using data property in routes

- Resolver

	- So basically resolver is that intermediate code, which can be executed when a link has been clicked and before a component is loaded.

- Observable (ng uses it alot - important concept)

	- Various Data Source

	- Observable Pattern

		- Observable and Observer and between it there is a timeline which has certain events getting triggered

	- Observer Hanldes Observable's certain events (I think its very much like Promise)

		- Data

		- Error

		- Completion

	- If self created also clean it(unsubscribe the subscription usually in ngDestory), if angular creates it angular takes care of its cleaning 

	- switchMap

		- takes care of existing observable and runs only one observable at a time instead of leaving all observable in running condition

		- returns new observable based on existing obervable

		- 

	- mergeMap

		- 

	- Real power of observable are its operators, we can transform the data in multiple shapes easily

- rxJs Operators

	- To Transform data in to different form

	- There are many operators, Some are E.g

		- of

		- map

		- merge

		- filter etc etc



- Forms

	- Angular provide JS object representation of forms

	- Approaches

		- Template Driven

			- Infers the form Object from the DOM

			- Form is created programmatically and syncs with the DOM

		- Reactive

			- Pass Js Object that creates form

			- Values can be initialized using FormControl object

			- Validation is done using "Validators" 

			 	- E.g new FormControl('defaultValue', Validators.required | Validators[])

				- E.g Validators.email

			- Controls can be group as well in Reactive approach

		

	- Validations

		- Built-in validators

		- Can write own validators

		- Can be Async

		- this.SomeForm.valueChanges.subscribe

      		- this.SomeForm.statusChanges.subscribe

		- this.ManageRolesForm.patchValue

			- To patch the part of the form

		

	- ngModelGroup

		- Used to group data from ngModels

		- 

- Pipes

	- Transforms output in templates

	- E.g {{ userName | uppercase }}

	- E.g {{ fooDate | date }}

	- Params can be passed to it

	- Can be chained

		- {{ fooDate | date : 'fulldate' | uppercase }} 

			- Here sequence is very important, if uppercase is used first it cant upper case the date format so will throw error

	- Can be applied  to Loops as well 

	- Pure / Impure Pipes

	- Async Pipes

		- {{ fooServerValue | async }}

- Ajax Calls

	- HttpClient is used for server communication

	- Http methods return Returns Observables

	- Data can be tranformed using map

	- If On Error want to throw error wrapped in Observable

		- Observable.throw('Some Error Occured')



- Authentication

	- Traditional

		- Send Auth From Client -> Set Session Cookie on client -> Identity Via Cookie 

	- SPA

		- Send Auth From Client -> Send Back Token to client -> Identity via Token (attached with each request going to server)

- Modules

	- Restructure & Organise App

	- Increase Performance & Decrease file size

	- Easier to maintain code

	- Mutiple modules can be used in app

	- Single Module

		- Component

		- Component

		- Directives

	- Bundles Certain functionality together so we can import it

	- Boostrap Property

		- Tells the root component, the starting point of the app

	- Its a good idea to import items(components, services, directive, etcs) in the modules where they are actually used ()

	- RouterModule.forRoot 

		- Used in root module

	- RouterModule.childRoot

		- Used in any child/feature module

	- Shared Module

		- Something which is shared across modules

	- If you want to use some thing from shared/feature module, that thing must be exported from shared/feature module

 	- Can be lazy load according to the need 

		- RouterModule.forRoot(appRoutes, { preloadingStrategy: PreloadAllModules })

			- Own strategy can be written as well

	- Lazy Load Routes can be Pre Loaded

	- E.g The child router is only loaded when user visits that module

	- Dont provide services in shared modules, especially not, if you plan to use them in lazy loaded Modules. (?)

	- Core Modules

	- Its a good idea to give only AppComponent in delaration and move every other thing in seprate/core/shared modules

	- Move providers as well in core module

	

- Compilation (turns templates into javascript)

	- JIT compilation 

		- Dev => Prod => App Downloaded in Browser => Angular Parses & Compiles Templates (to JS)

	- AOT compilation

		- Dev => Angular Parses & Compiles Templates (to JS) => Prod => App Downloaded in Browser

		- Advantages

			- Faster Startup		

			- Templates get checked during devs

			- Smaller file size

- Deployment

- Http

	- Old: HttpModule

	- New: HttpClientModule

		- Gives Interceptor 

		- You can also tell the get method the type	

	- Property observe in get gives full response instead of extracting data from it

	- Response types

		- text

		- json

		- arrayBuffer

		- blob

		- etc etc

 	- HttpEventType

		- Sent

		- Response

		- etc etc

	- HttpHeaders

		- http header can be set as well with request

		- Tokens can be set

	- HttpParams

		- To send additional data with request

	- HttpRequest

		- Also helpful to see the progres 

		- When all configurations are to be done by self

		- (new HttpClient()).request(new HttpRequest()) to send request 

	- Interceptor 

		- Code which runs before sending every request

		- Implement Interface HttpInterceptor

		- Register it in module in "providers" by passing object in array

			- [ { provide: HTTP_INTERCEPTORS, useClass: MyCoolestInterceptor, multi:true } ]

			- Order Matter

		- Requests are immutable so clone the request (even clones are immutables) so just pass modified request in clone method

			- req.clone({ headers: (req.headers.append or req.header.set)  })

				- Params can also be changed like this

		- next.handle(req).do()

			-  Response can be Intercepted like this

		-

- State	

	- The State of application

	- Loses when app is refreshed

	- Backend state is persistant

		- Like user create products from front end and then its saved on backend and we update it on UI as well (we are managing state here)

		- Its difficult to manage state when app grows into large size

		

	- ngRx

		- Not part of angular

		- Used to apply Redux Pattern in angular application



	- Redux (A Pattern not just related to specific framework)

		- A way to manage the app state in a central store

		- Keys Terms

			- Actions -> Reducers -> Store

			- Actions

				- We Dispatch Actions (data can also be passed with actions)

				- E.g SaveProduct(product)

			- Reducers

				- These are simple pure functions you write

				- Actions are received by Reducers 

				- Reducers take actions with payload and manipulate original state in an immutable way

					- It doesnt edit original state it over writes the original state

			- Store

				- Application state is saved here

		- Dont need to handle subscription, events, memory leaks, Redux handles its everything for us

		- Can be used with Guards



	- Spread Operator is used alot in Redux to its immutable nature of store

		- let p1 = { Id: 1, Name: "Ali", Age: 29 };

		- let updateP = { ...p1, Age: 18 };

		- Age updated to 18



	- Reducers can be bundled as well to make global state

		- ActionReducerMap

		- 

	- Only react to actions once

	- Side Effects

		- Async Tasks are side effects in ngrx world

		- These side effect dispatch actions explicitly but doesnt alter state directly

		- npm isntall --save  @ngrx/effects

			- Handling aysnc Tasks

			- @Effect() decorator

			- action$

				- All actions we have in app

				- tell the type by ofType

		- Much act like reducers but instead of dealing with pure functions they 

	- Manage state only when it is to be used across multiple components not just in a single component

	- If Services and subcject Pattern is doing good then its not neccessary to use Redux pattern

	

- RxJS (Reactive Extensions for JavaScript)

	- Library for reactive programming using observables that makes it easier to compose asynchronous or callback-based code

	- Rxjs 6 compat package is for backward compatibility

	- Provides utility functions for creating and working with observables.

	- Uses

		- Converting existing code for async operations into observables

		- Iterating through the values in a stream

		- Mapping values to different types

		- Filtering streams

		- Composing multiple streams

- IvyRender	

	- New Angular Renderer Engine

- Angular Elements

	- Angular components packaged as custom elements, a web standard for defining new HTML elements in a framework-agnostic way

	- Converts angular components into native html elements (web components)

	- Angular recognied these elements and Even these Custom elements are recognized after app is fully rendered and life cycle is completed

	- Angular wraps the custom element by using createCustomElement



- template Changed to ng-template



		

- Typescript

	- Strong typings

	- Get more features

	- Reduce errors

	- Generics

		- Create types without type and when using it be specific about the type

	- Types

		- string, number, boolean, Array, any, void, enums, customTypes

	- Compiles to JS

	- Interface

		- Not compiled to JS

		- Creates contracts 

	- Keyword export

		- Exported class/interface/enums/func/property/etc can be used outside the file



	

	









====================================================================

			Angular Sample Project

====================================================================



- App Structure

	- Root

		- Header

		- Shopping List (Model: Ingredient)

			- Shopping List

			- Shopping List Edit

		- Recipe Book (Model: Recipe)

			- Recipe List

			- Recipe Item

			- Recipe Detail

- Image src 

	- "{{ imagePath }}"

	- [src] = "imagePath"

- Components Communications

- Augury (Debugging Tool)

- Property & Event Binding

	- @Input() 

		- Decorator for exposing property to outside to get data

		- Alias can be assigned

	- @Output()

		- Decorator for exposing property to outside to give data

		- Alias can be assigned

- Pass Data to Child Component from Parent

- Pass Data to Parent Component from Child

- Style Encapsulation Mechanisms

	- Emulated

	- None

	- ShadowDOM

	- Native

- Local Reference 

	- Can be added in any html element

	- <p #localRefp> </p>

		- So can be accessed in component

- Angular Life Cycle

	- ngOnChanges 

		- Called after a bouund  input property changes

	- ngOnInit

		- Component is initialized

	- ngDoCheck

		- Every change detection run

	- ngAfterContentInit

		- Called after content projected into view

	- ngAfterContentChecked

		- Called every time the projected content has been checked

	- ngAfterViewInit

		- View has been initialized

	- ngAfterViewChecked

		- View has been checked

	- ngDestory

		- When Component is about to destroy

- @ViewChild()

	- Decorator

	- Alias can be assigned

- @ContentChild()

	- Decorator

	- Alias can be assigned

- Services & DI

	- Code re-usability (DRY)

	- Centralizing the code

	- Easy to manage

	- Clean Code

	- Help to communicate between components

	- Dont instantiate it, Angular handles it via DI

	- Heirarchical Injector	

		- When a service is passed to Component same instance is passed to it and its child components - Important

		- Service Instances  dont propogate up, they propogate down in tree of components - Important

		- If on each component services is passed via provider the instance is overridden

		- Highest level for adding service is module



	- Services can be injected into other services

	- Service should be decorated by @Injectable() if its needs to be injected via DI

	- Services can have events to help cross components communications	

	

- Angular Universal

	- For server side rendering of the angular

- Angular Animation

- Unit Testing with Angular









====================================================================

			Personal Notes

====================================================================

- Decorators

	- There are four main types

		- Class decorators, e.g. @Component and @NgModule

		- Property decorators for properties inside classes, e.g. @Input and @Output

		- Method decorators for methods inside classes, e.g. @HostListener

		- Parameter decorators for parameters inside class constructors, e.g. @Inject

		- Decorators are just a magic which can turn simple TS class into modules, components, services, pipes etc

 

- Commands

	- npm i -g typescript 

	- npm i -g @angular/cli

	- ng new App --skip-tests --style=css

	- ng build --extractCss --watch

		- Run this at the end for mvc project cli automatically rebuild the project when file is changed

	- --skip-tests 

		- Command to make project or component without test files

	- ng g =>

		- appShell

    		- application

    		- class

    		- component

    		- directive

    		- enum

    		- guard

    		- interface

    		- library

    		- module

    		- pipe

    		- service

    		- serviceWorker

    		- universal

	- ng g c

		- Short for generating Components

	- ng g d

		- Short for generating Directive

	- ng build --prod --aot

		- make build ready for  prod

	- ng serve --open

		- while developing the app

	- Installing Bootstrap in angular project

		- npm install bootstrap

		- Reference "node_modules/bootstrap/dist/css/bootstrap.min.css" in angular.json file in styles array

	- cd..

		- Go one directory back from current position

	- npm install --save rxjs-compat

		- For backward compatibility



- References

	- https://alligator.io/angular/component-inheritance/

	- https://medium.com/@saniyusuf/part-1-the-case-for-component-inheritance-in-angular-a34fe2a0f7ac

	- https://rangle.io/blog/angular-2-ngmodel-and-custom-form-components/

	- https://ultimatecourses.com/blog/angular-decorators

	- https://alligator.io/angular/hostbinding-hostlistener/

	- https://jwt.io/introduction/

- Accessing Elements Directly is not a good practice

- Bindings In Angular

	- Property Binding

	- Event Binding

	- Two Way Binding

	- String interpolation

- ElementRef

	- Gives reference to the elements

- TemplateRef

	- Gives reference to the template

- ViewContainerRef

- Its Better to use Angular for any kind of DOM manipulation instead of using jquery or even bootstrap js

- When we create new component we dont instantiate its instance somewhere angular handles this for us

- When returning arrays dont return the actual reference, return the copy of the array so original content cant be modified

	- Using slice method

- DI Types

	- Constructor

	- Property

	- Interface (method)

	

- "+" 

	- Used for casting

-  TypeScript Config

	- Can also be used to shorten import file in case deep directory structure

- Subject class from "rxjs"

	- Used for notify when something is changed 

		- this.somethingChange.next("Hey,Its Changed")

			- Anything is subscribed to this will be notified about the change with the message "Hey,Its Changed"



- If there are alot of pipe symbol | (union type) is used to tell about possible types, make an interface.

- DomSanitizer


## Udemy Course Link
This is a really good course [Angular 7 Udemy Course](https://www.udemy.com/the-complete-guide-to-angular-2/).
