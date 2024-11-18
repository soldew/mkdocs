The field value check allows you to check whether the value of the specified field is equal `(==)` or not equal `(!=)` to a defined value. String comparisons are case insensitive so that `"value" == "VALUE"` is _true_. For case sensitive comparisons, use 3 equal signs `(===)`.

You can also check if a field value is less than `(<)`, less or equal `(<=)`, greater than `(>)` or greater or equal `(>=)` than a certain value. However, we highly recommend to consider the field's field type for any field check as else the evaluation whether a field is greater than 100 using `field[myField] > "100,00"` may not return the expected result.

!!! dps-note "Warning"
    If an expression uses calculations that the system can't perform, for example, because the typed amount value does not exist, then it can't _properly evaluate_ `[amount] *1.19 > 20` and fails! Note that the platform does not cast text values to typed values nor applies further fallbacks. Therefore, we recommend to use **simple** and easy to read expressions. In case of an unexpected routing decision, you can use the work item audit to get more information about the evaluation result.

When you add a field to a document type you specify the field's type, such as, string, date, or decimal. Each field in Primus has a text and a typed value. A field that has no field value, is **null**, for both the text and the typed value. For conditions, the platform handles a field value that is null the same way as an _empty_ field value. Most activities set the field's text value only so that the corresponding typed value is _null_. It may also happen that text and typed value have different values for example, when the formatting fails. For example, if the field's text value is “34,B5” for a decimal field, the typed value is not set (null) as a decimal field cannot contain letters.

The platform provides the generic field value check, additional value checks on the text, typed, and captured value of a field and checks on Date as well as on Boolean fields. The following field value checks are provided.

## Generic field value check

For the generic field value check, the platform uses the field's text value for evaluating the condition. That means it is similar to using the field text value check so that 
`field[fieldName] == fieldTextValue[fieldName]` is always true.  

For the following sample, the platform returns true if the field's text value is equal to _ClassA_.

`field[MyDocClass] == "ClassA"`

A field that has no field value set yet, is null. However, for checking if a field is empty, it is sufficient to check whether the field is empty by using the following condition.

`field[MyField] == ""`

The platform returns _true_ when the field text value is empty or null. The same is valid for the typed and captured value check, **if** the field is of the type string. Comparing dates, booleans, or numbers to a string fails when you access the typed value.

>[!warning]
> For versions prior to Primus 3.0.2, the field check behaves differently. It first checks the condition for the field's typed value and if this is not available it uses the field's text value for verifying the condition. In addition, to check whether a field is empty or not, you have to check whether a field is either empty or null. With version 3.0.2 and newer, it is sufficient to check whether the field is empty.  

As a result, you may need to change the conditions for a process created with an earlier version to ensure that you have the same results for your routes and activity filters with the newer platform version.
    
**Important** String comparisons are case insensitive: `"value" == "VALUE"` is `true`. For case sensitive comparisons, use 3 equal signs: `"value" === "Value"` is `false`.

## Field text value 

Evaluates the text value of a field. We recommend to use the field text value check only for string fields and to evaluate whether the text value has a certain value or not and if you are sure which content the field can have.

`field[MyDocClass] == "ClassA"`

## Field typed value

Evaluates the typed value of a field. Use this method especially for non-string field, especially for numerical, date, and Boolean fields. There are 2 ways how you can access the typed value:

`fieldTypedValue[amount] < 200.00 [amount] < 200.00`


If the typed value is not set on a field, the expression fails to execute and evaluates to false.

>[!important] 
>The platform comprises a breaking change with Primus version 3.1 where the typed value comparison fails if the field types do not match. In previous versions, comparing `50 == "5"` evaluated to _true_. Now, this comparison evaluates _false_. Therefore, you have to be careful using conditions such as `[amount] < field[otherAmount]` or `[amount] < "50"`.

## Field captured value

Evaluates the captured value of a field. The captured value is a string value that contains the field's original value extracted from the document. The sample evaluation below returns _true_, if the classification result is not “Invoice”.

`fieldCapturedValue[DocClass] != "Invoice"`

## Field regular expression match

Checks whether the value of a specified field matches a regular expression, a 1 to 5-digit number.

`field[MyTestField] Matches "(\d){1,5}"`

## Field exists

Checks whether a specified field exists in the document independent from its value. If a document type is assigned that does not contain the field or no document type is assigned, the evaluation returns false.

`fieldExists[MyTestField]`

## Field starts with

Checks whether the value of a specified field starts with the specified path data and then returns true.

`field[ImportSource] StartsWith "C:\Images"`

## Field ends with

Checks whether the value of a specified field ends with the configured image file extension and then returns true.

`field[ImportSource] EndsWith "jpg"`

## Field value contains

Checks whether the value of a specified field contains the specified image path and then returns true.

`field[ImportSource] Contains "\Images\Tif"`

## Boolean field is true check

Checks whether a Boolean field is _true_, based first on the typed value, then on the text value. If the typed value exists and is true, the evaluation returns true. If the typed value is false, the result is false. If the typed value does not exist and the text value is "true", it returns true. If the text value is "somethingElse", it returns false. If the field is not a Boolean field, the result is false.

`isBoolFieldTrue[myBoolField]`

## Boolean field is false check

Checks whether a Boolean field is _false_, based first on the typed value, then on the text value. If the typed value exists and is true, the evaluation returns false. If the typed value is false, the result is true. If the typed value does not exist and the text value is "false", it returns true. If the text value is "somethingElse", it returns false. If the field is not a Boolean field, the result is false.  
`isBoolFieldTrue` and `isBoolFieldFalse` need to both exist, because the evaluation of a field that has the value xx is neither true nor false.

`isBoolFieldFalse[myBoolField]`

## Date check

Allows you to evaluate date and date/time values for a field or custom value. For the date check, you can set the date value in two different ways. Either by passing the date literal or by multiple numbers as parameters. The evaluation returns true if the date for the field, myDueDate, is January 1st, 2022.

    `fieldTypedValue[myDueDate] == date('2022-01-01') fieldTypedValue[myDueDate] == date('2022-01-01T11:50:13') fieldTypedValue[myDueDate] == dateTime('2022-01-01T11:50:13')`
    
Initializing the date with the date literal works if a date or date/time string is formatted as the ISO 8601 date format. Note that not all formats defined in ISO 8601 are supported. For initializing the date without the time component, you can use the string in one of the following formats: `yyyy-MM-dd` or `yyyyMMdd`.

For initializing the date-time to the allowed date formats, you append one of the following formats: `THH:mm:ss`, `HH:mm:ss`, `THHmmss`, or `HHmmss`. Note that the platform initializes a date with a string that is not following the allowed formats, the min DateTime is `01.01.0001 00:00:00`.

!!! dps-note "Important"
    For dates, the platform expects that date and date/time fields have the value in the UTC format. The reason for that is that you can handle from one multiple runtimes with different time-zones or even have the design-time and runtime on individual machines with different time zones. Also, every date/time aspect of the platform is handled in UTC so that using local times is not useful.
    
Alternatively to configuring the date literal in brackets, you can specify the date parts. To initialize the date, you can use date[year, month, day]. The platform returns true if the field, myDueDate, is equal to December, 20th 2021.

`fieldTypedValue[myDueDate] == date[2021, 12, 20] fieldTypedValue[myDueDate] == dateTime(2022, 1, 1, 11, 50, 13)`

If you want to initialize the date-time, you have to specify all the date-time components up to seconds: date[year, month, day, hour, minute, second].

!!! dps-note "Important"
    Specifying an invalid number of parameters or parameters that are out of the allowed range, the expression initializes with the min date and evaluation may return unexpected results.

You can compare date and date/time objects. In this case, the date/time object's day is taken for the comparison.


``` py title="Comparison example"
    myDate = '2022-05-10',  
    myDateTime = '2022-05-10 15:30:21',  
    myDateTime2 = '2022-05-10 15:30:20'  
    [myDate] < [myDateTime] // false  
    [myDate] <= [myDateTime] // true  
    [myDate] >= [myDateTime] // true  
    [myDateTime2] == [myDateTime] // false
```

The platform also supports arithmetic on date and time values, by using a time span. Time spans are created by using either days, hours, minutes, or seconds, giving the amount in parenthesis, for example, minutes(5). You can use multiple time spans in the same condition.

`// myDate = '2020-05-10', myDateTime = '2020-05-10 15:30:21' [myDate] < today() - days(50) // true (in march 2022) [myDate] < today() - days(5000) // false (in march 2022) [myDateTime] < now() + hours(5) // true if now() is '2020-05-10 10:30:22' or later today() == now() // true today() == now() + days(1) + hours(5) + minutes(10) - seconds(5000) // false`


Related topics : [[Custom Value Evaluation Methods]]

