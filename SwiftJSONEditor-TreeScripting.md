
# Swift JSON Editor Tree Scripting

Swift JSON Editor incorporates a simple Javascript scripting to modify / edit document project json trees. Every project model contains a single script that can be executed to modify the project node main json tree.

Use scripting to:

- Modify key & values, search & replace
- Append nodes
- Delete nodes
- Select nodes
- Gather information & export to external text files
- Extract structures & create new project nodes with selected data

## Tree Scripting functions

Default script:

```javascript
/*  Swift JSON Editor - Json Tree Plugin */

var sjeTreeNode = function (rootJsonNode, selectedJsonNodes) {
    
}

/*
 var sjeRecursiveNode = function (node) {
 
 }
*/

/*
 var sjeTreeNodeExport = function () {
 return NULL;
 }
*/

```

Basic script pre-defines 3 main scripting functions. Swift JSON Editor will execute available functions in this order:

1. sjeRecursiveNode function is is implemented.
2. sjeTreeNode function 
3. sjeTreeNodeExport function

Comment sjeTreeNode if you want to execute sjeRecursiveNode function and vice versa. 

## Tree Node Function

```javascript
var sjeTreeNode = function (rootJsonNode, selectedJsonNodes) {
    
}
```
