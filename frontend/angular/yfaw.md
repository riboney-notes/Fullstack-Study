# Angular Learning
 From the book *Writing Your First Angular Web application* book

## Project Setup

 **Requirements**
 * Node
 * NPM
 * Typescript
 * Angular CLI

**Angular CLI Commands**

```bash
# creates new project from scratch
ng new <project-name>

# runs application 
ng serve

# generates component with all relevent files
# places it as a directory into the `/app` directory
ng generate component <component-name>
```

**Modules**

Input 
  - Allows you to pass in a vlaue from the parent template

HostBinding
  - Syntax; `@HostBinding()`
  - used to set properties on the host element


**Files Descriptions**

`index.html`
  - this is where the application is rendered with the `<app-root>` tag

`app/app.component.html` 
  - defines the HTML/ components that will injected into the webpage
    - through `<app-root>` in `index.js`

`angular.json` 
  - angular configurations

`main.ts` 
  - entry point for the angular app; bootstraps the application
  * boots an angular module `AppModule`

`AppModule` 
  - specifies which component to use as the top level component; also declares the components 


## Concepts

**Components**
* HTML tags that have custom functionality attached to them
* Defined inside `.ts` file 
  * ex: `app.component.ts`
* Consists of two parts:
  * [Decorator](https://www.typescriptlang.org/docs/handbook/decorators.html) - provides metadata to HTML template:
    * selector (html tag name)
    * templateURL (html)
    * styleUrls (css)
  * Class
    * Defines properties & fields
    * Uses typescript classes to carry out business logic
    * Defines getters and setters

**Change Detection**
  * Where angular synchronizes UI with component data to synchronize any changes between the two
  * Events that can trigger "change detection":
    * When component data is updated
    * When User interacts with UI



**Data binding**

Data binding types:
* One-way from class to template (HTML)
  * Interpolation:
    * `{{ some expression here }}` - substitutes value from expression here
  * Property/ attribute/ class binding:
    * `[target]="expression"` *or* `attribute="expression"` - binds value from expression to the *target* element (DOM property or HTML attribute or some variable)
* One way binding from template to class
  * Event 
    * `(target)="statement"`
    * `on-target="statement"`
* Two-way binding from class to template and vice-versa
  * `[(target)]="expression"`
  * `bindon-target="expression"`

Data binding syntax:
  * The binding punctuation of `[], (), [()]`, and the prefix specify the direction of data flow.
    * Use `[]` to bind from source to view.
    * Use `()` to bind from view to source.
    * Use `[()]` to bind in a two way sequence of view to source to view.


**NgModules**

* Properties:
  * `Declarations` 
    - specifies the components that are defined in this module
    - these components must be declared here to be used in the templates
  * `imports` 
    - describes the dependencies this module has
  * `providers`
    - used for dependency injection
  * `bootstrap` 
    - tells Angular which component to use as top-level compnent when this app runs

## Components

Components are main building blocks for Angular apps; Component folder consists of:
  * CSS Selector - ex: `<app-selector></app-selector>
  * HTML Template - ex: `<h1>Title</h1>`
  * CSS styling - ex: `styleUrls: ['./random.compononent.css]`
  * Typescript Class - ex: (`export class AppSelector{...}`)
  
  
