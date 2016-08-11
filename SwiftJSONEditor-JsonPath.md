# Swift JSON Editor JSON PATH

Swift JSON Editor implements custom JSONPath syntax to traverse JSON nodes in application and user scripting. This document will explain the current JSONPath syntax that is suported in Swift JSON Editor application.

The current syntax has been modified from [http://goessner.net/articles/JsonPath/](http://goessner.net/articles/JsonPath/) implemntation porting to Apple Swift and modified to support more relevant options for future **Scripted Server** project nodes and implementation of input/output javascript scripted server within application (Will come in next application update).

JSON PATH can be used to extract structures from JSON tree wihout manually traversing the tree structure.

## Main Characteristics

- JSONPath expressions can use the dot–notation, **$.store.book[0].title** or or the bracket–notation **$['store']['book'][0]['title']**
- bracket-notation is requiered where path JSON key contains blank spaces such **$.store.book[0].['json path key with spaces']**
- 

## Implementation syntax

```javascript
{ "store": {
    "book": [ 
      { "category": "reference",
        "author": "Nigel Rees",
        "title": "Sayings of the Century",
        "price": 8.95
      },
      { "category": "fiction",
        "author": "Evelyn Waugh",
        "title": "Sword of Honour",
        "price": 12.99
      },
      { "category": "fiction",
        "author": "Herman Melville",
        "title": "Moby Dick",
        "isbn": "0-553-21311-3",
        "price": 8.99
      },
      { "category": "fiction",
        "author": "J. R. R. Tolkien",
        "title": "The Lord of the Rings",
        "isbn": "0-395-19395-8",
        "price": 22.99
      }
    ],
    "bicycle": {
      "color": "red",
      "price": 19.95
    }
  }
}
```

| Syntax        | Example           | Description  | Result |
| ------------- |-------------| -----|-----|
| $     | $ | Reffers root element, must be included in all json path queries. | Will return root JSON Element, the whole tree |
| .      | $.store      |   . reffers to path, use . to dive into subtrees | Will return store object |
| * | $store.books[*]      |    reffers to all elements in array | Will return all objects in books array |

