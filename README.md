# SystemMethodsRemover
Removes system ($) methods from the codebase. Tool for InterSystems Caché

It currently does 3 things:

1. Replaces `.$` with `.<something of your choice>` (`.%` by default)
2. Capitalizes the letter after `$`
3. Replaces references from `%Object` to `%DynamicObject` etc

## Use

Import classes and call one of the entry points: 

`s st = ##class(SMR.Main).RemoveFromAllClasses(Replace, Capitalize)` - for all user classes

`s st = ##class(SMR.Main).RemoveFromSubclassesOf(Class, Replace, Capitalize)` - for subclasses

`s st = ##class(SMR.Main).RemoveFromMatchingClasses(Mask, Replace, Capitalize)` - for LIKE SQL

Arguments:

- `Replace` - what to replace $ with (% by default but, for example, you can specify `$$$`)
- `Capitalize` - capitalize the letter after $ (boolean, yse by default)
- `Class` - class which subclasses the utility would try to convert (including the class)
- 'Mask' -  pattern, value for the SQL query `SELECT ID FROM %Dictionary.ClassDefinition Where ID LIKE ?`

More docs are in the code docs.

## Requirements

Works in 2016.2 Field Test or later. 
