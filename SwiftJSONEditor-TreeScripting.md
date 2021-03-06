
# Swift JSON Editor Tree Scripting

Swift JSON Editor incorporates a simple Javascript scripting to modify / edit document project and json trees. Every project model contains a single script that can be executed to modify the project node json tree.

Use scripting to:

- Modify key & values, search & replace
- Append nodes
- Delete nodes
- Select nodes
- Gather information & export to external text files
- Extract structures & create new project nodes with selected data

JSON structure is simple tree structure, however when represented in Swift JSON Editor, JSON objects are translated to JsonNode class objects. JsonNode scripting class offers several methods and functionality and is represented in regular tree structure with parent / children relationship. **Inside scripting functions JavascriptJsonNode class is used insted of javascript JSON representation.**

### All Scripting Classes

| Name | Represents | Description |
|----|----|----|
| [JsonNode](SwiftJSONEditor-JavascriptJsonNode.md) | Json Node tree object in current editor | allows modification of json nodes |
| [ProjectNode](SwiftJSONEditor-JavascriptProjectNode.md) | Project node in project structure | allows modification of project nodes |
| [ContextController](SwiftJSONEditor-JavascriptContextController.md) | global Swift JSON Editor application context | exists as global "sje" object in scripts, calls functions available to process in host application |
| [SJEFile](SwiftJSONEditor-SJEFile.md) | Export file | Define export file and Swift JSON Editor will save your defined files to disk |


## Tree Scripting functions

Default script:

```javascript
/*  Swift JSON Editor - Json Tree Plugin */

var sjeTreeNode = function (rootJsonNode, selectedJsonNodes, parameters) {
    
}

/*
var sjeRecursiveNode = function (node, parameters) {
 
}
*/

/*
var sjeTreeNodeExport = function (parameters) {
	return NULL;
}
*/

/*
var sjeParameters = function () {
	return NULL;
}
*/

```

Basic script pre-defines 3 main scripting functions. **Swift JSON Editor will execute available functions in this order:**

1. **sjeRecursiveNode** function if is implemented.
2. **sjeTreeNode** function 
3. **sjeTreeNodeExport** function

Comment sjeTreeNode if you want to execute sjeRecursiveNode function and vice versa. 



# Tree Node Function

```javascript
var sjeTreeNode = function (rootJsonNode, selectedJsonNodes, parameters) {
    
}
```

Tree node function provides a way for your script to traverse complete JSON structure. 

| Parameter | Class | Description |
|---|----|----|
| rootJsonNode | **JsonNode** class | root tree node of your project model |
| selectedJsonNodes | **Array** of **JsonNode** class objects  | currently selected JSON nodes in UI |

sjeTreeNode function provides you a way to enumerate or filter using jsonPath nodes. 

*Example:*

```javascript
var sjeTreeNode = function (rootJsonNode, selectedJsonNodes, parameters) {
   
  	// Get all books
  	var allBooks = rootJsonNode.jsonPath("$.store.book[*]");
  
    for (var i = 0; i < allBooks.length; i++) {
  		// Get book JavascriptJsonNode classes
  		var book = allBooks[i];
  		// Append String Json Node into book Object
      	var published = book.appendBoolean("isPublished");
      	published.value = parameters.published;
	}
}
```

Example script filter rootJsonNode using jsonPath function (implemented in JavascriptJsonNode class) and appends new Boolean element into Book object with key "isPublished" and value "false"



# Recursive Node Function

```javascript
 var sjeRecursiveNode = function (node, parameters) {
 
 }
```

Recursive node function is executed on every single Json node in your current structure. Use this function for "search & replace" or similar functionality as this function will execute with every single Json node. Traversing starts from root to all children deep.

| Parameter | Class | Description |
|---|----|----|
| node | **JsonNode** class | json node  |


*Example:*

```javascript
var sjeRecursiveNode = function (node, parameters) {
 
   	var value = node.value;
  
   	if (value.search("http://") != -1) {
   		node.value = value.replace("http://","https://");
	}
}
```

Example script will search everywhere for "http://" string and replace it with "https://"

> sjeRecursiveNode will be executed multiple times, passing every json node in current tree.



# File Export Function

It is possible to gather information using tree or recursive functions and export gathered data to a file. Use sjeTreeNodeExport function to export information to disk. You can implement your own (Swift class file generators, JSON to XML ) etc.

```javascript
var sjeTreeNodeExport = function (parameters) {

}
```

*Example:*
```javascript
// Return Array of SJEFile class objects
var sjeTreeNodeExport = function () {
	
	var file = SJEFile.newFile();
	
   	file.fileName = "BookClass";
   	file.fileExtension = "swift";
   	file.contentString = myGeneratedSwiftClassString;
   	
  	return [file];
}
```

| Parameter | Class | Description |
|---|----|----|
| none | none | Create new SJEFile class object, set fileName,fileExtension and contentString object |
Return : Array of [SJEFile] objects

# Parameters Function

Parametes function allows you to define a visual user interface parameters for your script. User interface parameters will be stored in project and user is allowed to mofify them. Parameters will be passed as javascript object into all previous functionality functions where you can take advantage of user input. 

```javascript
var sjeParameters = function (parameters) {
    return [item0,item1,item2];
}
```

Parameters are simple javascript object instances with pre defined structure of key:value
All parameters has special keys:value pairs that you should follow:


