# JavascriptContextController class

JavascriptContextController class represents a global application context. Context let you use Swift JSON Editor application internal helper functions to 

- Retrive Project Nodes
- Insert new Project Nodes
- Use helper functions for encoding etc.

## Functions
| Function | Parameters | Returns | Description |
| --- | --- | --- | --- |
| **log(object)** | Javascript/String/Number | String description | Use to print log information about provided objects |
| **newProjectModel(projectNodeID)** | (project node identifier) or nil | creates and returns new child model project node as JavascriptProjectNode object | if you pass nil context will append to document root, if you pass projectNodeIdentifier, new child node will be appended. |
| **newProjectFolder(projectNodeID)** | (project node identifier) or nil | creates and returns new child folder project node as JavascriptProjectNode object | if you pass nil context will append to document root, if you pass projectNodeIdentifier, new child node will be appended. |
| **rootJsonNode(projectNodeID)** | String (project node identifier) or nil | root JSON node associated with project node as JavascriptJsonNode object | returns root json node of project node |
