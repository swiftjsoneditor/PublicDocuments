# JavascriptJsonNode class

JavascriptJsonNode class representes single tree JSON entity in application. 

## Properties

| Properties | Value Type | Access | Description |
| --- | --- | --- | --- |
| key | String | get / set | key of json node. (*a) |
| value | (String,Number,Boolean) |  get / set | value of json node |
| type | Number | get | Object:0, Array:1, String:2, Number:3, Boolean:4, Null: 5, SmartObject:6, SmartArray:7, Unknown:-1|
| parent | JavascriptJsonNode | get | parent node |
| children | Array of JavascriptJsonNode objects | get | Object,Array,SmartObject or SmartArray nodes can contain child nodes.|
| index | Number | get | Current index of node within its parent node | 
| isSmartNode | Number | get | 1 if node is SmartObject or SmartArray else 0 |
| isContainer | Number | get | 1 if node is Object, SmartObject, Array, SmartArray else 0 |

(*a) key and structure modifications are disabled in Smart nodes. (cannot append, delete or modify key structure of smart objects)

## Functions
| Function | Parameters | Returns | Description |
| --- | --- | --- | --- |
| jsonPath("jsonPathString") | [String (JSONPath string)](SwiftJSONEditor-JsonPath.md) | Array of JavascriptJsonNode class objects | Use to filter and return nodes using JSONPath querries |
| appendObject() | none | newly created JavascriptJsonNode class object | appends new Object node (*b) |
| appendArray() | none | newly created JavascriptJsonNode class object | appends new Array node (*b) |
| appendString() | none | newly created JavascriptJsonNode class object | appends new String node (*b) |
| appendNumber() | none | newly created JavascriptJsonNode class object | appends new Number node (*b) |
| appendBoolean() | none | newly created JavascriptJsonNode class object | appends new Boolean node (*b) |
| appendNull() | none | newly created JavascriptJsonNode class object | appends new Null node (*b) |
| delete() | none | none | deletes node (*c)|
| select() | none | none | upon operation finishes, node will be selected in UI |
| debugInfo() | none | key + value formatted string | prints basic information about node |


(*b) appending new nodes is only allowed in container nodes (Object,Array), SmartNodes are not supported.
(*c) deleting smart nodes is not allowed.

##Smart Nodes

Smart nodes offers most efficiency in user interface editing therefore editing is only supported via user interface. Smart Nodes were created to quickly edit and create JSON structures in interface.
