# JavascriptProjectNode

JavascriptProjectNode class represents scripting class for Swift JSON Editor project nodes. 

## Properties

| Properties | Value Type | Access | Description |
| --- | --- | --- | --- |
| **name** | String | get / set | project node name |
| **identifier** | String |  get / set | identifier for project node, in scripting functions you can obtain project nodes from global context using its identifier string |
| **type** | Number | get | Folder:0, Model:1, APIGroup:2, APIEndpoint:3, ScriptedServer:4, Note: 5, UnKnown:-1 |
| **parent** | JavascriptProjectNode | get | parent node |
| **children** | Array of JavascriptProjectNode objects | get | Object,Array,SmartObject or SmartArray nodes can contain child nodes.|
| **index** | Number | get | Current index of node within its parent node | 
| **rootJsonNode** | JavascriptJsonNode | get | the root json node associated with project node |
