There are several evaluation methods for custom value. A custom value is a user-defined key-value pair that an activity can create or set a value for. A custom value contains string values only.

## Custom value check

You can use a custom value check to calculate whether the value of a specified custom value is equal `(==)` or not equal `(!=)` to a defined value. Due to the behavior of JS we highly recommend not to use less than `(<)`, less or equal `(<=)`, greater than `(>)` or greater or equal `(>=)` than for custom value checks.

The following condition is valid, when the custom value “ImportSource” for a work item is equal to “C:\ImagesImport”.

`customValue[ImportSource] == "C:\Images\Import"`

## Custom value matches a regular expression

For custom values, you can also use a check against a regular expression. The evaluation returns true, if the value of a specified custom value matches a regular expression. In this case, the value must start with “DE” followed by one or several digits.

`customValue[MyTestField] Matches "(^DE\d*)"`

## Custom value exists

Checks whether a specified custom value exists. If the custom value for the configured name is available for the root document, the evaluation returns true.

`customValueExists[MyCustomValueKey]`

## Custom value starts with

Checks whether the value of a specified custom value starts with a specified data and then returns true.

`customValue[ImportSource] StartsWith "C:\Images"`

## Custom value ends with

Checks whether the value of a specified custom value ends with a specified data and then returns true.

`customValue[ImportSource] EndsWith "jpg"`

## Custom value contains

Checks whether the value of a specified custom value contains specified data and then returns true.

`customValue[ImportSource] Contains "\Images\Tif"`