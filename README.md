# tool-utils-mvc-application
### Tool / Utilities / UI / MVC / Application Framework &amp; Library
## Intro
This library & framework facilitates a module UI, MVC & routing structure with additional tools & utitlities.
## Getting started
Assuming you have a folder `application` containing `index.html`, 
which loads all the files in `/assets/` (`tool.js, utils.js, model.js, controller.js, view.js, ui.js` & `application.js`); 
Create `myApp.js`, link to it in `index.html`, with the following code;

```javascript
const myApp = function(){
  const config = {
    main : '#myAppMain',
    menu : '#myAppMenu',
    default : 'myAppModule'
   }
   const myAppModule = function(){
    console.log('this is myAppModule')
    return {
      label : 'My App Module'
    }
   }
   return {
    config : config,
    myAppModule : myAppModule
   }
}

application.init( myApp )
```
This is the very minimal code you will need to initialize an new application named `myApp` with only one module named `myAppModule` which only prints 'this is myAppModule' to the console. 

Because 'myAppModule'is defined as default in config, myAppModule will be executed as such if index.html (whithout hash) is called. 
Because myAppModule is returned by `MyApp`, and has a `label` property, a menu item link (links to '#myAppModule') with as text the value of `myAppModule.label`, is added to the element with the id in the `menu` property of `myApp.config`.
When `index.html#myAppModule` is called `myApp.MyAppModule` will be executed.

## Adding Tools, Utilities & MVC

Add by peference the following lines to your code to make shorthand references to `tool, utils, model, view, controller` & `application`

```javascript
const make = tool.make, // make( [ 'div', { id : 'newElementId' }, 'content of element' ]
```


| Function       | Method           | Description  |
| ------------- |:-------------:| -----:|
| `tool`      | `make([str,{obj}])` | Create HTML element from array |
| `utils`      | `obj({obj})` | Create object with properties/valus arrays from object|
| `view`      | `element(str)` | Get DOM element |
| `view`      | `set(parent,content)` | Set DOM element |
| `controller`      | `add(element,action,function)` | Add event handler to element |
| `application`      | `call(functionName)` | Create application call |
| `application`      | `before(functionName, function)` | Add before to application call |
