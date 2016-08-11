# JavascriptContextController class (sje)

JavascriptContextController class represents a global application context. Context let you use Swift JSON Editor application internal helper functions to 

- Retrive Project Nodes
- Insert new Project Nodes
- Use helper functions for encoding etc.

## Functions
| Function | Parameters | Returns | Description |
| --- | --- | --- | --- |
| **log(object)** | Javascript/String/Number | String description | Use to print log information about provided objects |
| **newProjectModel(projectNodeID)** | String (project node identifier) or nil | creates and returns new child model project node as [JavascriptProjectNode](SwiftJSONEditor-JavascriptProjectNode.md) object | if you pass nil context will append to document root, if you pass projectNodeIdentifier, new child node will be appended. |
| **newProjectFolder(projectNodeID)** | String (project node identifier) or nil | creates and returns new child folder project node as [JavascriptProjectNode](SwiftJSONEditor-JavascriptProjectNode.md) object | if you pass nil context will append to document root, if you pass projectNodeIdentifier, new child node will be appended. |
| **rootJsonNode(projectNodeID)** | String (project node identifier) or nil | root JSON node associated with project node as [JavascriptJsonNode](SwiftJSONEditor-JavascriptJsonNode.md) object | returns root json node of project node |

Example:

```javascript
var sjeTreeNode = function (rootJsonNode, selectedJsonNodes) {
   
  	var filtered = rootJsonNode.jsonPath(jsonPath);
  
    for (var i = 0; i < filtered.length; i++) {
  		var item = filtered[i];
  		// Use JavascriptContextController via sje global object
      sje.log(item);
	}
}

```

Call sje global object to invoke JavascriptContextController functions.
