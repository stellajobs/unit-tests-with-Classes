# [u]NIT [t]EST

The `ut` class is designed to manage unit testing.

## Summary

### Properties
|Properties|Type|Description|
|---------|:----:|------|
|**.desc**|Text|The description of the test suite
|**.tests**|Collection|The collection of the executed tests
|**.success**|Boolean|The status of the current test suite
|**.lastError**|`Test object`|The last failed test
|**.lastErrorText**|Text|The last failed test error description

### Functions
|Function\*|Action|
|--------|------|  
|.**suite** (description : `Text`)  → `cs.ut` | Initialize a new test suite
|.**test** ( description : `Text` {; type : `Integer`})  → `cs.ut` | Initializes a new test.<br>• The `type` option of the value is mandatory for time values in order to handle the formatted assert message correctly.<br>• If passed, it also allows to perform checks.
|.**expect** ( value : `Variant`)  → `cs.ut` : `Object` | Sets the expected test result
|.**equal** ( value : `Variant` \| **4D**.Function )| Performs the comparison with the expected result and generates an ASSERT with a formatted message if the values are identical.
|.**notEqual** ( value : `Variant` \| **4D**.Function )| Performs the comparison with the expected result and generates an ASSERT with a formatted message if the values are not identical.
|.**strict** ()  → `cs.ut`| Called before a `.equal()` or `.notEqual()` function defines that the comparison will be diacritical if relevant.
|.**skipError** ()  → `cs.ut`| Called before a `.equal()` or `.notEqual()` function, it prevents the ASSERT from being generated even if the `test` object is filled.

\*All functions that return `cs.ut` may include one call after another.

The error message od the assert is automatically formated like: 

> `{suite}: '{test}' gives {result} when '{expected}' was expected`

For examples:

* "Numeric: 'Integer' gives '1' when '2' was expected"
* "DateTime: 'Date' gives '00/00/00' when '08/08/1958' was expected"
* "Diacritical: 'Not strictly equal text' gives 'hello world' when 'Hello World' was expected"
* "Diacritical: 'Not strictly equal object' gives '{\"foo\":\"BAR\"}' when '{\"foo\":\"bar\"}' was expected")

## Test object

|Properties|Type|Description|
|---------|:----:|------|
|**.desc**| Text | The description of the test
|**.success**| Boolean | The status of the test after execution
|**.expected**| Variant | The expected test result
|**.result**| Variant | The result of the text after execution
|**.error**| Text | The formatted error description if the test failed

## How to

```4d
var $ut : cs.ut

```

