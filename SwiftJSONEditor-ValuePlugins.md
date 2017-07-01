# Value Plugins

For any **String**, **Number**, **Boolean** or **Null** json value in Swift Json Editor one or more user defined value plugins can be appended. 

Value plugins let you **temporary override the editor value** to process many kind of customizations like:

- Generating fake testing data
- Replacing values
- Combining values

### How value plugins work

Value plugin is a simple **Javascript code** that interact with Swift Json Editor and passes the converted value back to editor. This **value is generally stored and cached** therefore your plugin in most cases will **execute and cache values for all associated editor value fields** in sigle operation upon editing parameters or code. 

Remember to use Save and Execute button to:
- Save your modified script text
- Generate and cache values for all editor fields with associated plugin.

### Smart Objects

Smart objects with value nodes will **share single instance of plugin**. You only use single editable instance on value nodes in Smart Object. Using value plugins in Smart Objects is the most preffered use for value plugins. 

Remember :
- Only single instance is used in Smart Objects.
- Use Smart objects in Array container for best use as possible.
- Use arrayIndex to randomize or identify the position of smartObject value node.

## Basic Value Plugin

Quick script:
```javascript
var ValuePlugin = function () {
    this.displayName = "Value Plugin Quick Script";
    this.identifier = "com.swiftjsoneditor.valueplugin.user.<IDENTIFIER>";// !!! Do not modify !!!
    this.executeScript = function (inputValue, jsonValue, arrayIndex, parameters) {
        return inputValue;
    };
}

function sjePluginClass() {
    return new ValuePlugin();
}
  
```


Default script:

```javascript
var ValuePlugin = function () {
    
    // Required displayName
    this.displayName = "Value Plugin User Script";
    
    // Required !!! Do not modify this identifier !!!
    this.identifier = "com.swiftjsoneditor.valueplugin.user.<IDENTIFIER>";
    
    // Optional set to true for timestamp type of plugins
    this.isCacheDisabled = false;
    
    // Optional set to true if you want to lock
    this.isEditingDisabled = false;
    
    // Optional define UI input controls
    this.parameters = function () {
        return []
    }
    
    // Requiered function executeScript
    // @param {String} inputValue - Value from editor or value generated from previous value plugin in queue.
    // @param {String} jsonValue - Original stored value in json editor.
    // @param {Number} arrayIndex - Index of this value node relative to first array container.
    // @param {Object} parameters - Your defined parameters as object.
    // @returns {String} - Override value for display or next value plugin.
    this.executeScript = function (inputValue, jsonValue, arrayIndex, parameters) {
        return inputValue
    };
}

// Requiered global function
function sjePluginClass() {
    return new ValuePlugin();
}


```

| Parameter/function | Requiered | Type | Returns | Description |
|----|----|----|----|----|
| **displayName** | yes | String | none | Plugin display name. Will be presented in UI|
| **identifier** | yes | String | none | Automatically generated unique plugin identifier. This cannot be modified.|
| **executeScript** | yes | function | String | Main transform/generate function. Use transform logic and return String/Number/Boolean/Null representation back to editor.|
| isCacheDisabled | no | Boolean | none | Set to true if your plugin cannot cache values such timestamp generator. If you set to true, editor will process the plugin script on every display, webserver request etc.|
| isEditingDisabled | no | Boolean | none | Set to true you do not want to edit anymore the plugin in UI.|
| parameters | no | Function | Array of Objects | Define your Interface parameters.|

## Main Function (executeScript)

``` javascript
this.executeScript = function (inputValue, jsonValue, arrayIndex, parameters) {
    return inputValue
};
```

Execute script function is a main transform function. The parameters are pased from Swift JSON Editor and you are able to transform the value using simple javascript.

### inputValue

Input value is a parameter value passed from Swift JSON Editor as a main value to use for transform operations. This value is a **result of previous value plugin output or output directly of the value from outline** if this is a first value plugin. You should use this value as it is the input for transforming operations.

### jsonValue

Json value is a parameter value that is representation of the inputted Json value in editor. This value represent the original value that actually exists and is passed unmodified to every value plugin in a row. 

### arrayIndex

Array index position of the first parent Array container. Use this value as a base for randomization or iteration. 


