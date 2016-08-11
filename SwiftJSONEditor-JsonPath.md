# Swift JSON Editor JSON PATH

Swift JSON Editor implements custom JSON Path syntax to traverse JSON nodes in application and user scripting. This document will explain the current JSON PATH syntax that is suported in Swift JSON Editor application.

The current syntax has been modified from [http://goessner.net/articles/JsonPath/](http://goessner.net/articles/JsonPath/) implemntation to support more relevant options for future *8Scripted Server8* project nodes and implementation of input/output javascript scripted server implementation.

JSON PATH can be used to extyract structures from JSON representation wihout manually traversing the tree structure. Use JSON PATH within application whenever you need to filter requiered results.

Few initial characteristis:

- JSONPath expressions can use the dot–notation, $.store.book[0].title or or the bracket–notation



