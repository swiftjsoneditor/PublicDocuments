# Swift JSON Editor JSON PATH

Swift JSON Editor implements custom JSONPath syntax to traverse JSON nodes in application and user scripting. This document will explain the current JSONPath syntax that is suported in Swift JSON Editor application.

The current syntax has been modified from [http://goessner.net/articles/JsonPath/](http://goessner.net/articles/JsonPath/) implemntation porting to Apple Swift and modified to support more relevant options for future **Scripted Server** project nodes and implementation of input/output javascript scripted server within application (Will come in next application update).

JSON PATH can be used to extract structures from JSON tree wihout manually traversing the tree structure.

## Main Characteristics

- JSONPath expressions can use the dot–notation, **$.store.book[0].title** or or the bracket–notation **$['store']['book'][0]['title']**
- bracket-notation is requiered where path JSON key contains blank spaces such **$.store.book[0].['json path key with spaces']**

