# Swift JSON Editor JSONPath

Swift JSON Editor implements custom JSONPath syntax to traverse JSON nodes in application and user scripting via javascript. Application will guide you to create JSONPath syntax in top JSONPath search field, **just press "Space" key on your keyboard and hints will be presented to you:**

![JsonPath](http://api.artproweb.com/sje/documentation/jsonPath.png "Json Path")
![JsonPath](http://api.artproweb.com/sje/documentation/jsonPath-Array.png "Json Path")
![JsonPath](http://api.artproweb.com/sje/documentation/jsonPath-Dot.png "Json Path")
![JsonPath](http://api.artproweb.com/sje/documentation/jsonPath-ArrayFilter.png "Json Path")

The current syntax has been modified from [http://goessner.net/articles/JsonPath/](http://goessner.net/articles/JsonPath/) implementation porting it to Apple Swift and modified to support more application relevant functionality such **input/output javascript scripted server** within application (Will come in next application update).

> Scripted Server project node will allow to create HTTP Rest server in Swift JSON Editor and exchange JSON stuctures to/from your development application. You will be able to send data to Swift JSON Editor and receive responses via HTTP Rest server.

JSON PATH can be used to extract structures from JSON tree wihout manually traversing the tree structure.

## Characteristics

- JSONPath expressions can use the dot–notation, **$.store.book[0].title** or or the bracket–notation **$['store']['book'][0]['title']**
- bracket-notation is requiered where path JSON key contains blank spaces such **$.store.book[0].['json path key with spaces']**

## Syntax


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

### Path Syntax


| Syntax        | Example           | Description  | Result |
| ------------- |-------------| -----|-----|
| **$**     | $ | Reffers root element, must be included in all json path queries. | Will return root JSON Element, the whole tree |
| **.**      | $.store , $.['store']      |   . path, use . to dive into subtrees | will return store object |
| **<p>*</p>** | $store.books[*]      | all elements in array | Will return all objects in books array |
| **[2]** | $store.books[2] | array element index | will return 3rd object from books array, remember indexings starts from 0 element in arrays |
| **[(@.length-1)]** | $store.books[(@length-1) ] | index condition, @length reffers to count of objects in array | will return last object in books array |
| **[0:3]** | $store.books[0:3] | sequence [startIndex:endIndex] | will return 4 objects in sequence from books array starting at 0 to 3 index (total of 4 objects) |
| **[0:10:2]** | $.store.book[0:4:2] | sequence with step [startIndex:endIndex:step] | will return every second objects from books array from sequence starting at 0 ending at 4 index (will return objects with indexes 0 and 2) |
| **[?]** | $.store.book[?] | randomly selected object in array | will return any single randomly selected object from books array |
| **[^]** | $.store.book[^] | distinct items | JSONPath will traverse the array, compare and return every object that has different key structure than differ from the most common object key structure in array.|
|**[(@.price < 10)]** | $.store.book[@.price<10] | filter condition in array | return all objects in array with price element lower than 10 |


Filtering array has been extended with additional functionality.

**[(@.price < 10)]** transfers to [(@.objectKey comparator value)]


### Comparators (Array Filter Condition)


| Comparators        | Example           | Description  |
| ------------- |-------------| -----|
| **=, ==** | $.store.book[(@.price = 12.99)], $.store.book[(@.category == 'fiction')]  | numeric or string value is equal to value |
| **!=, !==** | $.store.book[(@.price != 12.99)], $.store.book[(@.category !== 'fiction')]  | numeric or string value is not equal to value |
| **<** | $.store.book[(@.price < 12.99)]  | numeric value is less than |
| **<=** | $.store.book[(@.price <= 12.99)]  | numeric value is less or equal than |
| **>** | $.store.book[(@.price > 12.99)]  | numeric value is greater than |
| **>=** | $.store.book[(@.price >= 12.99)]  | numeric value is greater or equal than |
| **between** | $.store.book[(@.price between 5.6:15.0)]  | numeric value is between min:max value |
| **contains** | $.store.book[(@.author contains 'Evelyn')]  | string value contains string |
| **regex** | $.store.book[?(@.author regex '[a-zA-Z]')]  | string value is matching regex pattern, (experimental) |

* Remember that comparator values for string elements must contains ' ' wrap, where numeric do not.



