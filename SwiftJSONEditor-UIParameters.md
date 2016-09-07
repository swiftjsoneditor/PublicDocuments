# Parameters

Swift JSON Editor allows you to take user inpunt inside your tree scripts. You can define serie of UI input fields including:

* Description Header
* Text / Number Inputs
* True / False checkbox input
* Exclusive options matrix input
* Map View, location coordinate input
* 

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

