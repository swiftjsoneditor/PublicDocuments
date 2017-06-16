# Value Plugins

For any **String**, **Number**, **Boolean** or **null** json value in Swift Json Editor one or more user defined value plugins can be appended. 

Value plugins let you **temporary override the editor value** to process many kind of customizations like:

- Generating fake data
- Replacing values
- Combining values

### How value plugins work

Value plugin is a simple Javascript code that interact with Swift Json Editor and passes the converted value back to editor. This **value is generally stored and cached** therefore your plugin in most cases will **execute and cache values for all associated editor value fields** in sigle operation upon editing parameters or code. 

Remember to use Save and Execute button to:
- Save your modified script text
- Generate and cache values for all editor fields with associated plugin.

### Smart Objects

Smart objects with value nodes will **share single instance of plugin**. You only use single editable instance on value nodes in Smart Object. Using value plugins in Smart Objects is the most preffered use for value plugins. 

Remember :
- Only single instance is used in Smart Objects
- Use Smart objects in Array container to get best usage
- Use arrayIndex to randomize or identify the position.

