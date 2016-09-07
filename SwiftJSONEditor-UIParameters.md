# Parameters

Swift JSON Editor allows you to take user inpunt inside your tree scripts. You can define serie of UI input fields including:

* Description Header
* Text / Number Inputs
* True / False checkbox input
* Exclusive options matrix input
* Map View, location coordinate input

Input fields are stored along with project node, therefore user can undo/ redo parameter values. 

To implement UI input fields implement simple function in your script: 

###Example:

```javascript
var sjeParameters = function () {
  ...
  ...
  // return array of objects
   return [parameter1,parameter2,...];
}

## Shared keys

Parameters are Javascript objects. All parameters have shared keys that define they properties.

| Key | Value type| Possible Values | Description |
| --- | --- | --- | --- |
| **name** | String | parameter name in script code | parameter name provides access to return values from parameters |
| **displayName** | String |  parameter display name in user interface | displayName will be presented as parameter name in interface |
| **description** | String | short informative description about parameter | description will be presented to user |
| **type** | String | "String","Number","Map","Bool","Options" | type of user interface element |
