# JavascriptJsonNode class

JavascriptJsonNode class representes single tree JSON entity in application. 

## Properties

| Properties | Value Type | Access | Description |
| --- | --- | --- | --- |
| key | String | get / set | key of json node. (*a) |
| value | (String,Number,Boolean) |  get / set | value of json node |
| type | Number | get | Object:0, Array:1, String:2, Number:3, Boolean:4, Null: 5, SmartObject:6, SmartArray:7, Unknown:-1|
| parent | JavascriptJsonNode | get | parent node |
| children | Array of JavascriptJsonNode | get | Object,Array,SmartObject or SmartArray nodes can contain child nodes.|
| index | Number | get | Current index of node within its parent node | 
| isSmartNode | Number | get | 1 if node is SmartObject or SmartArray else 0 |
| isContainer | Number | get | 1 if node is Object, SmartObject, Array, SmartArray else 0 |

*a Smart Nodes are not supported to modigy (Key, Append child nodes)
