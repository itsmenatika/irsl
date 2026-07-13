# types

There are several predefined types:

## undefined (ID 0)

undefined means no value. Setting something to undefined deletes it.

It is however also defined as its own type that is inaccessible to user.

## null (ID 1)

null means an absence of a value but with reserved place for said value.
The rest of implementation is left to interpreter, transpiler or 


## boolean (ID 2)

It represents true or false. The implementation is left to interpreter, transpiler or compiler.



## number (ID 3)

Every number is by default [IEEE 754 double-precision binary floating-point format](https://en.wikipedia.org/wiki/Double-precision_floating-point_format). It means that every number is signed and can represent floating values.

It is divided into three parts:
* sign (1 bit) -> to indicate if the value is positive or negative
* exponent (11 bits) -> to indicate the exponent
* mantisa (52 bits) -> the representation of the number between 0 and 1


Optimization by interpreter, transpiler or compiler is permitted, but all numbers have to be able to be used like IEEE 754 double-precision binary floating-point format numbers.

It's expected to be converted to decimal (id 20) or bigint (19) before it exceeds its maximum value.

## string (ID 4)

It uses UTF encoding. The rest of implementation is left to interpreter, transpiler or compiler.


## array (ID 5)

array can contain every type at the same time. The implementetion is left to interpreter, transpiler or compiler.

Optimization by interpreter, transpiler or compiler is permitted, but all numbers have to be able to be used like IEEE 754 double-precision binary floating-point format numbers.

## object (ID 6)

Objects work like a maps with keys that can be dynamically added and removed during runtime.

Their value can be of any type, also an another object.


Optimization by interpreter, transpiler or compiler is permitted, but all numbers have to be able to be used like IEEE 754 double-precision binary floating-point format numbers.

## int8 (ID 7)

8 bit signed integer

## uint8 (ID 8)

8 bit unsigned integer

## int16 (ID 9)

16 bit signed integer
 
## uint16 (ID 10)

16 bit unsigned integer

## int32 (ID 11)

32 bit signed integer

## uint32 (ID 12)

32 bit unsigned integer

## int64 (ID 13)

64 bit signed integer

## uint64 (ID 14)

64 bit unsigned integer

## function (ID 15)

Yes, function is a type.

## bytes (id 16)

an immutable byte array of a fixed size

## char (id 17)

It's a string (id 4) that is forced to be only one character

## symbol (id 18)

It represents a unique value. Each symbol holds also a descriptor.

## bigint (id 19)

It's used to store arbitally large integer numbers.

## decimal (id 20)

It's used to store arbitally large float numbers.


## function (id 21)





RESERVED







# conversion to other types


## undefined

CONVERSION IS PROHIBITED.

## null

CONVERSION IS PROHIBITED.

## boolean

* undefined -> false
* null -> false
* bool -> retains the same value
* number -> true if number is not 0 or negative
* string -> true if a string is not empty
* array -> true
* object -> true
* int8 -> true if they're not negative or 0
* uint8 -> true if they're not all 0s
* int16 -> true if they're not negative or 0
* uint16 -> true if they're not all 0s
* int32 -> true if they're not negative or 0
* uint32 -> true if they're not all 0s
* int64 -> true if they're not negative or 0
* uint64 -> true if they're not all 0s
* symbol -> true
* bytes -> true if there's no 0
* char -> true if a string is not empty
* bigint -> true if it's not 0 or negative
* decimal -> true if it's not 0 or negative
* function -> true

## number

* undefined -> 0
* null -> 0
* bool -> 0 if false, 1 if true
* number -> retains
* string -> tries to convert it if possible. Error is thrown is there's no way to convert it
* array -> throws an error
* object -> throws an error
* int8 -> tries to convert it if possible. Error is thrown is there's no way to convert it
* uint8 -> tries to convert it if possible. Error is thrown is there's no way to convert it
* int16 -> tries to convert it if possible. Error is thrown is there's no way to convert it
* uint16 -> tries to convert it if possible. Error is thrown is there's no way to convert it
* int32 -> tries to convert it if possible. Error is thrown is there's no way to convert it
* uint32 -> tries to convert it if possible. Error is thrown is there's no way to convert it
* int64 -> tries to convert it if possible. Error is thrown is there's no way to convert it
* uint64 -> tries to convert it if possible. Error is thrown is there's no way to convert it
* symbol -> throws an error
* bytes -> tries to convert it if possible. Error is thrown is there's no way to convert it
* char -> tries to convert it if possible. Error is thrown is there's no way to convert it
* bigint -> tries to convert it if possible. Error is thrown is there's no way to convert it
* decimal -> tries to convert it if possible. Error is thrown is there's no way to convert it
* function -> throws an error


## string

* undefined -> "undefined"
* null -> "null"
* bool -> "false" if false, "true" if true
* number -> "{number}" where number is a string representation of that number
* string -> retains
* array -> "[...elements]" for example [1,2,5, "s"]. If there's more than 100 elements it is: "[array with (number of elements) elements]"
object -> tries to convert to json like pretty representation
* int8 -> "{int}" where int is a string representation of that int
* uint8 -> "{int}" where int is a string representation of that int
* int16 -> "{int}" where int is a string representation of that int
* uint16 -> "{int}" where int is a string representation of that int
* int32 -> "{int}" where int is a string representation of that int
* uint32 -> "{int}" where int is a string representation of that int
* int64 -> "{int}" where int is a string representation of that int
* uint64 -> "{int}" where int is a string representation of that int
* symbol -> symbol descriptor
* bytes -> "[(number of bytes) raw bytes]"
* char -> retains
* bigint -> "{int}" where int is a string representation of that int
* decimal -> "{decimal}" where decimal is a string representation of that decimal
* function -> "function(...args): returntype"




## array

* undefined -> [undefined]
* null -> [null]
* bool -> [that bool]
* number -> [that number]
* string -> [that string]
* array -> retains
* object -> [that object]
* int8 -> [that int]
* uint8 -> [that int]
* int16 -> [that int]
* uint16 -> [that int]
* int32 -> [that int]
* uint32 -> [that int]
* int64 -> [that int]
* uint64 -> [that int]
* symbol -> [that symbol]
* bytes -> [...an array using int fixed sized types]
* char -> [that char]
* bigint -> [that big int]
* decimal -> [that decimal]
* function -> [that function]

NOTE: explicit conversion to an array rarely occures.


## object


* undefined -> throws an error
* null -> throws an error
* bool -> throws an error
* number -> throws an error
* string -> throws an error
* array -> throws an error
* object -> throws an error
* int8 -> throws an error
* uint8 -> throws an error
* int16 -> throws an error
* uint16 -> throws an error
* int32 -> throws an error
* uint32 -> throws an error
* int64 -> throws an error
* uint64 -> throws an error
* symbol -> throws an error
* bytes -> throws an error
* char -> throws an error
* bigint -> throws an error
* decimal -> throws an error
* function -> creates an empty object with call() function



## (u)int(8/16/32/64) or bigint or decimal


* undefined -> 0
* null -> 0
* bool -> 0 if false, 1 if true
* number -> tries to convert it if possible. Error is thrown is there's no way to convert it
* string -> tries to convert it if possible. Error is thrown is there's no way to convert it
* array -> throws an error
* object -> throws an error
* int8 -> tries to convert it if possible. Error is thrown is there's no way to convert it
* uint8 -> tries to convert it if possible. Error is thrown is there's no way to convert it
* int16 -> tries to convert it if possible. Error is thrown is there's no way to convert it
* uint16 -> tries to convert it if possible. Error is thrown is there's no way to convert it
* int32 -> tries to convert it if possible. Error is thrown is there's no way to convert it
* uint32 -> tries to convert it if possible. Error is thrown is there's no way to convert it
* int64 -> tries to convert it if possible. Error is thrown is there's no way to convert it
* uint64 -> tries to convert it if possible. Error is thrown is there's no way to convert it
* symbol -> throws an error
* bytes -> tries to convert it if possible. Error is thrown is there's no way to convert it
* char -> tries to convert it if possible. Error is thrown is there's no way to convert it
* bigint -> tries to convert it if possible. Error is thrown is there's no way to convert it
* decimal -> tries to convert it if possible. Error is thrown is there's no way to convert it
* function -> throws an error

## symbol

CONVERSION IS PROHIBITED.

## bytes

* undefined -> 0 as one byte
* null -> 0 as one byte
* bool -> 0 if false, 1 if true (one byte)
* number -> tries to convert it if possible. Error is thrown is there's no way to convert it
* string -> tries to convert it if possible. Error is thrown is there's no way to convert it
* array -> tries to convert it if possible. Error is thrown is there's no way to convert it
* object -> tries to convert it if possible. Error is thrown is there's no way to convert it
* int8 -> tries to convert it if possible. Error is thrown is there's no way to convert it
* uint8 -> tries to convert it if possible. Error is thrown is there's no way to convert it
* int16 -> tries to convert it if possible. Error is thrown is there's no way to convert it
* uint16 -> tries to convert it if possible. Error is thrown is there's no way to convert it
* int32 -> tries to convert it if possible. Error is thrown is there's no way to convert it
* uint32 -> tries to convert it if possible. Error is thrown is there's no way to convert it
* int64 -> tries to convert it if possible. Error is thrown is there's no way to convert it
* uint64 -> tries to convert it if possible. Error is thrown is there's no way to convert it
* symbol -> throws an error
* bytes -> tries to convert it if possible. Error is thrown is there's no way to convert it
* char -> tries to convert it if possible. Error is thrown is there's no way to convert it
* bigint -> tries to convert it if possible. Error is thrown is there's no way to convert it
* decimal -> tries to convert it if possible. Error is thrown is there's no way to convert it
* function -> throws an error

## char

It works like with string type, but it will throw an error if it can't convert it to the length of one.

## function

CONVERSION IS PROHIBITED.




# type attributes

## const

every type can be a const meaning it can be assigned to a different value,
however it doesnt indicate that value itself can't be changed.


## immutable (readonly can be also used as an alias)

It means that the value itself can be changed. However its name can be assigned to a different object


## difference between const and readonly


```
let s = 0;
s = 1;

```

will produce an error if it's a const. It will not if it's only readonly.



```
let s = 0;
s += 1;

```

will produce an error if it's a readonly. It will not if it's only const.


Both examples will produce it if it's readonly and const. For instance:
```
let const readonly s = 0;
s += 0;
s = 0;
```
will produce two errors