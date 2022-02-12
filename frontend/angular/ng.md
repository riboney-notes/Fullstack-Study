# ngBook notes

## CH3 How Angular works

* An angular app is nothing more than a tree of components

Components composed of these 3 parts:
  * Decorator (selector, template, css style, etc)
    * This is where you configure the component
  * View (template/ html)
  * Controller (typescript class)

Component Selector
  * By default, its used like this, Element: `<app-component></app-component>`
  * But can also be used like this:
    * Attribute: `<div app-component></div>`; Selector: `selector: "[app-component]"
    * Class: `<div class="app-component"></div>`; Selector: `".app-component"`

Input/ Output 
  * `[]` is used to *input* or pass data into child components
    * Ex: `<products-list [productList]="products">`, this inputs the `products` array from app=component, into the product-list component's productList property
    * `@Input()` is directive used to take the data being passed from parent component into the current component
      * Specifies the parameters expected by the component to receive from outside
      * Ex: `@Input() productList: Product[];`
        * Can also do this: `@Input("products") productList: Product[]`
          * `products` will be the attribute you use in the template to refer to `productList`; this practice is not recommended
  * `()` is used to send data out of components (from child component to parent component)
    * when property is wrapped by parenthesis, it means that component is listening for output from that property
    * Usually, events (referred to as `$event`) are outputted from such binded properties
    * Ex: `<products-list (onProductSelected)="selectProduct($event)">`
    * `@Output()` is the decorator that allows data from child to flow to the parent
      * For the `@Output` to raise events, it must have type of `EventEmitter`
      * Ex: `@Output() onProductSelected: EventEmitter<Product>`

NgModule and Booting the App
  * `NgModule` specifies which components are going to be used
    * Makes components accessible to others in the current module
    * Components must be declared in `NgModule`2 before it can be used in a template
    * `bootstrap` specifies the top-level / root component of the app
    * `BrowserModule` in `imports` is necessary for browser apps
  * `main.ts` is the entry point of the app
    * `platformBrowserDynamic().bootstrapModule(AppModule);` is what boots the app
    * running `ng serve` runs the app
      * when invoked, it refers to `angular-cli.json` to see which file is the entry point (its `main.ts` by default)
    * `main.ts` bootstraps `AppModule`
      * `AppModule` specifies that `AppComponent` is the top level component
        * Then `AppComponent` renders the rest of the app (components)

Deploying apps (simple)
  * Basic process:
    * compile all typescript code into javascript
    * bundle all javascript code into one or two files
    * upload javascript code and all other assets to a server
  * `ng build --prod`
  * then push the files to `dist` in the server

## CH4 Directives

**Directives **
  * these are attributes that we add to HTML elements that give us dynamic behavior
  * Ex: `ngFor`,`ngIf`, etc.

**ngIf**
  * used to diplay/ hide an element based on a condition determined by the result of the expression that is passed to the directive
  * Ex: `<div *ngIf="myFunction()"></div>`
  * Ex: `<div *ngIf="a > b"></div>`

**ngSwitch**
  * allows a single evaluation of an expression, and then displays the nested elements based on the value from that expression
  * Ex:
  ```HTML
  <div class="container" [ngSwitch]="myVar">
    <div *ngSwitchCase="'A'">Var is A</div>
    <!-- You can use the same switchcase value to get a different element/ display -->
    <div *ngSwitchCase="'A'">Var is A, again</div>
    <div *ngSwitchCase="'B'">Var is B</div>
    <!--ngSwitchDefault is optional; can be left out-->
    <!--If the case statements fail to match anything, then nothing will be rendered if default is left out-->
    <div *ngSwitchDefault>Var is something else</div>
  </div>
  ```

  **ngStyle**
  * allows you yo set a given DOM element CSS properties from Angular expressions
  * Ex: `<div [style.background-color]="'yellow'">This element's background is yellow</div>`
  * Ex: `<div [ngStyle]="{color: 'white', 'background-color': 'blue'}"> Uses fixed white text on blue background </div>`
    * Note: there are quotes around `background-color` but not `color` because the `-` character isn't allowed in an object key

**ngClass**
* allows you to dynamically set and change CSS classes for a given DOM element
* Ex: Passing object literal and setting it with boolean
```css
.bordered {
    border: 1px dashed black;
    background-color: #eee;
}
```
```html
  <div [ngClass]="{bordered: false}">This is never bordered</div>
  <div [ngClass]="{bordered: true}">This is always bordered</div>
  <div [ngClass]="{bordered: isBoolean}">This is bordered dynamically</div>
```

**ngFor**
* Allows you to repeat DOM elements and pass values from array on each iteration
* Syntax: `*ngFor="let item of items"`
* Get index of iterations by appending `let num = index` to the `ngFor`
  * Ex: 
  ```html
  <div class="ui list" *ngFor="let c of cities; let num = index">
      <div class="item">{{ num+1 }} - {{ c }}</div> 
  </div>
  ```

  **ngNonBindable**
  * Allows you to use syntax like `{{}}` without Angular compiling it
  * Example
  ```html
    <div class='ngNonBindableDemo'>
    <span class="bordered">{{ content }}</span>
    <span class="pre" ngNonBindable>
        ← This is what {{ content }} rendered
    </span>
    </div>
  ```

## CH5 Forms

Angular forms does the following things:
* Capture user input events from the view
* Validate user input
* Create form model and data model to update
* Provide a way to track changes

* Need to import `FormsModule` and `ReactiveFormsModule` in NgModule (`app.module.ts`) to use angular form directives
  * Ex: `import {FormsModule, ReactiveFormsModule} from '@angular/forms'`

**FormControl**
* typescript class that represents a single input field
  * the HTML attribute is `formControl`
    * Ex: `<input type="text" [formControl]="name" />`, this creates a `FormControl` object
* encapsulates the field's value and states whether it is valid, dirty (changed), or has errors
  * Ex:
    ```ts
        let nameControl = new FormControl("Nate");
        nameControl.errors // -> StringMap<string, any> of errors
        nameControl.dirty  // -> false
        nameControl.valid  // -> true
    ```

**FormGroup**
* Wrapper for a collection of `FormControl`s
* Allows you to do entire operations on the collection rather than doing things individually
* `FormGroup` and `FormControl` are both children of `AbstractControl` so that means you can use `.errors, .dirty, .valid` to check the status of the forms in `FormGroup`

**FormArray**
* Defines a dynamic form where you can add/ remove form controls during runtime
* Doesn't require you to define key for each control by name like in `FormGroup`

**NgForm**
* Comes from `FormsModule`
* Gets automatically attached to an `form` tags in HTML view (as long as `FormsModule` is imported)
  * Is not applied to `form` elements that have a `formGroup` attribute already defined
* Creates a form group for us `ngForm`
* Provides `ngSubmit` which is the what happens when form is submitted
* Ex: `<form #f="ngForm" (ngSubmit)="onSubmit(f.value)">`
* The `#f="ngForm` is creating a local variable `f` that is bounded to `ngForm`
  * thats why we can do `f.value`, which gives the value from the formgroup


To create a new FormGroup and FormControls implicitly use:
  * ngForm and ngModel (template-driven)

To bind to an existing FormGroup and FormControls use:
  * formGroup and formControl (reactive)


Reactive Form
* Setup of form model: explicit, created in component class
* data model: structured and immutable
* predictablity: synchronous
* form validation: functions
* More scalable than template-driven forms
* Data Flow
  * Since each form element in the view is linked to the form models in the component class, both are synced and don't depend on how UI is rendered

Template-Driven Form
* Good for adding simple forms
* Not good as reactive for scaling 
* Setup: implicit; created by directives
* Data model: unstructured and mutable
* Predictablity: Async
* Form validation: Directives
* the directive `NgModel` creates and manages `FormControl` instances for a given form element here
  * as opposed the form element being linked to an existing FormControl like with Reactive Forms
  * You don't have direct access to this `FormControl` instance; you only have access through `ngModel`
* Data flow
  * Each form element is linked to a directive that manages the form model internally

Validators
* Need to do when using validators:
  * Assign validator to the `FormControl` object
    * Ex: `let control = new FormControl('sku', Validators.required);`
  * Check status of the validator in the view and take action accordingly

## MISC

Not good idea to work directly with elementRefs (HTMLS ELEMENTS directly...)
  * This is because Angular can also work with service workers which may not have access to the DOM

Attribute binding
  * its recommended to instead bind to HTML properties instead of Attributes
  * Syntax is similiar except, attributes are referred to by appending with `attr.` 
  * Ex: `<p [attr.attribute-you-are-targeting]="expression"></p>`

Property binding vs String interpolation
* Property binding example: `<p [innerText]="validMessage"></p>
  * Here, we are binding the `p`'s DOM property "innerText" with the typescript variable `validMessage`
  * Note that the text between the quotation marks is *typescript code*
* String interpolation example: `<p>{{ validMessage }}</p>`
  * Here we are doing the same as the previous example, except we are using String interpolation
* The takeaway here is
  * Use string interpolation when you want to display some variable data
  * Use property binding when you want to change some HTML DOM element property or attribute

Non two-way binding vs two-way binding
```html
<!--Non two way-->
<input type="text" (input)="onInput($event)">

<!--Non two way-->
<input type="text" [(ngModel)]="serverName">
```

Directives
  * They are instructions in the DOM
  * Directives with templates are components
  * Example custom directive:
  ```ts
  @Directive({
    selector: '[appTurnGreen]'
  })
  export class TurnGreenDirective{
    //...
  }
  ```
  * structural directives changes the structure of the DOM
    * appended with `*`
    * ex: `ngIf` which will add an element if true
    * Cannot have more than one structural directive on an element
    * the `*` is a shorthand for `<ng-template [ngIf]="boolean">`
  * Attribute directives changes the elements they were placed on
    * ex: `<p [ngStyle]="{backgroundColor: getColor()}" [ngClass]="{online: serverStatus === 'online'}">{{ServerStatus}}</p>`

`@Input()` allows you to make properties in child components visible to parent components for data inputting
  * args inside `@Input()` are aliases for what to refer to the child component property in the view
    * Ex: `@Input('serverElement') element: any;`, then in the HTML: `[serverElement]="e"` (not `[element]="e"`)

`@Output()` allows you to emit events from child component to the parent component

CSS are applied only to the component they belong to, not the entire project/ globally
  * Normally, CSS is applied sitewide
  * Angular encapsulates views in this way that prevents such global styling
  * you can disable such encapsulation by using `ViewEncapsulation.None` in the component decorator (ViewEncapsulated.emulated is the default because shadowdom is not supported by all browswers)

You can reference specific HTML elements in other places in the same HTML code by placing a `#referenceVariable` in the element
  * You can even pass this as argument into typescript methods and refer to it as `HTMLInputElement` (if its an input element)
  * Ex: instead of binding an input element's value with `ngModel` and a typescript property, you can pass the input element directly into a typescript method and use the `.value()` to get the value (See `cockpit.component.ts` for code example)
  * You can also use `@ViewChild()` to refer to HTML elements in typescript code, but in an angular way
    * Ex: `      serverContent: this.serverContentInput.nativeElement.value` where `  @ViewChild('serverContentInput') serverContentInput: ElementRef;`
  
`ngContent` can be used to pass in HTML code from parent component, into child component
  * it is a placeholder for dynamic content
  * usually, you use property binding to pass in data from parent to child, but for large amounts of HTML, its better to use content projection (ng-content that is)

Lifecycle
* ngOnChanges: Called after a bound input property changes
* ngOnInit: Called once the component is initialized
* ngDoCheck: Called during every change detection run
* ngAfterContentInit: Called after content (ng-content) has been projected into view
* ngAfterContentChecked: Called every time the projected content has been checked
* ngAfterViewInit: Called after the component’s view (and child views) has been initialized
* ngAfterViewChecked: Called every time the view (and child views) have been checked
* ngOnDestroy: Called once the component is about to be destroyed

Click event to give parent component some value
  * Specify the values to propagate in the child component
    * Pass the value into the child component event emitter method, ex: `(click)="onSelect('recipe')"`
    * For input form values
      * create local reference to input element, ex: `<input type="text" id="name" #nameInput>`
      * Create `ElementRef` property in the component class, ex: `@ViewChild('nameInput') nameInputRef: ElementRef;`
  * Create EventEmitter property in child component class, ex: `@Output() featureSelected = new EventEmitter<string>();`
  * Create method that when triggered, will emit event to parent component, ex:
    ```ts
    onAddItem(feature: string){
      return this.featureSelected.emit(feature);
      // if the property is a ViewChild/ ElementRef
      // return this.ingredientAdded.emit(this.nameInputRef.nativeElement.value);

    }
    ```
  * Trigger the propagation of the values with some event:
    * Ex: `<button type="submit" (click)="onAddItem()">Add</button>`
  * Setup parent component to listen for custom events, ex: `<app-header (featureSelected)="onNavigate($event)"></app-header>`
  * Setup method in parent component that acts upon fired event, ex: 
    ```ts
      onNavigate(feature: string){
        this.loadedFeature = feature;
      }
    ```
  
  Creating Custom Directives
    * Create component folder
    * Create directive ts class, ex: `basic-highlight.directive.ts`
    * Class should have `@Directive({...})` decorator
      * Object to be passed inside directive shold have unique selector,
      * Ex:
      ```ts
      @Directive({
        // Attribute style
        selector: '[appBasicHighlight]'
      })
      export class BasicHighlightDirective implements OnInit{
        // elementRef is the HTML element in which the directive is placed
        // not good practice to use elementRef
        constructor(private elementRef: ElementRef){
        }

        ngOnInit(){
          this.elementRef.nativeElement.style.backgroundColor = "green";
        }
      }
      ```
      * Better example using `Renderer2`:
      ```ts
      @Directive({
        // Attribute style
        selector: '[appBasicHighlight]'
      })
      export class BasicHighlightDirective implements OnInit{


        constructor(private elRef: ElementRef, private renderer: Renderer2){
        }

        ngOnInit(){
          this.renderer.setStyle(this.elRef.nativeElement, 'background-color', 'green');
        }
      }
      ```
    * Use `@HostListener('eventName')` to have the directive react to events, ex: `@HostListener('mouseenter') mouseOver(event: Event){ this.renderer.setStyle(....)}`

    * Use `@HostBinding()` to have the directive bind to a specific DOM property on the HTML element it is on, ex: `@HostBinding('style.backgroundColor') bckColor: string;`

    * Create your own custom properties for Html elements provided by the directive by using `@Input()` on directive properties in the class







