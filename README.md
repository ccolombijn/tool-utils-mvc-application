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

## Adding more modules
Like `myAppModule` you could add as many modules as ar needed;

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
   const myAppSecondModule = function(){
    console.log('this is myAppSecondModule')
    return {
      label : 'My App 2nd Module'
    }
   }
   const myAppThirdModule = function(){
    console.log('this is myAppThirdModule')
    return {
      label : 'My App 3rd Module'
    }
   }
   return {
    config : config,
    myAppModule : myAppModule,
    myAppSecondModule : myAppSecondModule,
    myAppThirdModule : myAppThirdModule
   }
}

application.init( myApp )
```
Which will add more menu items (because the added modules have a `label` property and are returned by `myApp`) like `myAppModule`, `index.html#mySecondModule` will execute `myApp.mAppSecondModule` and so on.

## Using `UI` with `application.call`
`UI` is a Component library for ready-to-use interface elements, like forms, tables and other elemnts visible to the end user. `application.call` stores a component from a library like `UI` for later use, and to attach `application.before` and `application.hook`  to this call.

```javascript
const call = application.call
const overview = (args) => call('UI','overviewTable',args);
hook( 'UI', 'overviewTable' , () => {
    // hook function to any call instance of UI.overviewTable
    console.log('UI.overviewTable call hook')
});

before( 'UI', 'overviewTable' , () => {
  // before function to any call instance of UI.overviewTable
  console.log('UI.overviewTable call before')
});
```

## Adding Tools, Utilities & MVC

Add by peference the following lines to your code to make shorthand references to `tool, utils, model, view, controller` & `application`

```javascript
const make = tool.make, // make( [ 'div', { id : 'newElementId' }, 'content of element' ] -> <div id="newElementId">content of element</div>
const obj = utils.obj, // obj( { foo : 'foo' , bar : 'bar' } ) -> { properties : [ foo, bar ], values : [ 'foo', 'bar' ] }
```


| Function       | Method           | Description  |
| ------------- |:-------------:| -----:|
| `tool`      | `make([str,{obj}])` | Create HTML element from array |
| `utils`      | `obj({obj})` | Create object with properties/valus arrays from object|
| `view`      | `element(str)` | Get DOM element |
| `view`      | `set(parent,content)` | Set DOM element |
| `view`      | `add(parent,content)` | Add DOM element |
| `controller`      | `add(element,action,function)` | Add event handler to element |
| `application`      | `call(functionName)` | Create application call |
| `application`      | `before(functionName, function)` | Add before to application call |
| `application`      | `hook(functionName, function)` | Add hook to application call |
