# SJEFile Class

SJEFile class representes file export identity for Swift JSON Editor. During scripting function you need to define one or several files and return SJEFile array in sjeTreeNodeExport function such:

```javascript 

var sjeTreeNodeExport = function () {
	
  var file = SJEFile.newFile();
  
  file.fileName = "Exported";
  file.fileExtension = "txt";
  file.contentString = fileString;
  
  return [file];
}

```
## Properties

| Properties | Value Type | Access | Description |
| --- | --- | --- | --- |
| **fileName** | String | get / set | file name on disk |
| **fileExtension** | String |  get / set | file extension on disk such "txt", "swift", etc |
| **contentString** | String | get / set | content string that will be written to disk |

## Functions
| Function | Parameters | Returns | Description |
| --- | --- | --- | --- |
| **class function newFile()** | none | newly created SJEFile object | creates new file object |

> Remember !!! sjeTreeNodeExport function must return Array of SJEFile objects...

