C+ Programming Language
=======================

C+ is a programming language for educational purposes. The ideas behind this project is to create a similar C language without low level facilities and minimalistic syntax with the power of strong/weak typing and high level abstraction mechanisms.

Some objetives of this language are: 

a) Strong/Weak typing switching.
b) Remove all the low level keywords and low level utilities.
c) Add interfaces support and class/module abstraction mechanism.
d) Preserve C ABI interface.
e) No scripting, only compiled/binary executables.
f) Standarized mechanisms for serialization/deserialization of data structures.
g) Have a minimal set of primitive types (value-types and referenced-types).
h) Consistent syntax in order to avoid programmers to write code in different ways to perform same behaviour.
i) Clear policy of memory management and concurrency facilities.

Language technology
-------------------

This language works with a transpiler pair. Does not compile by its own bytecode.
The decisions behind this are:

a) Avoid virtual machine design and build compilers from scratch
b) Take the advantages of compiler optimization from well known languages (C)
c) Open the possibility by translate the language into any language.

Primitive value types
---------------------

In type theory, there are a lot of classifications of types. The most simple classification starts with value-types and referenced-types.
Value-types are the representation of the data by itself while Referenced-Types holds a reference to a one/many Value-types.

The following draft have the primitive type proposal with its possible C mapping implementation:

**byte**
Minimal binary unit of data
size: 1 byte / 8 bits
C mapping: char / uint8

**integer**, **uinteger**
Integer number with the largest range
size: 8 bytes
C mapping: int64, uint64

**double**
Floatting comma number with the largest range
size: 8 bytes
C mapping: double

**boolean**
Boolean value (True/False)
size: 1 byte
C mapping: int8

**blob**
Dynamic binary array of bytes. Block of raw memory.
size: 
C mapping: struct blob { size:integer, byte* }

**string**
Dynamic binary string
C mapping: struct string { size: integer, byte* }
https://www.php.net/manual/en/language.types.string.php#language.types.string.details 

**undefined**
Undefined value as type that represents a dynamic typed instance without type definition.


Primitive referenced types with parametrization
-----------------------------------------------

**array[type]** or **array:type** or **array of type**
Dynamic array of value-types.
Access: By integer index
C mapping: struct array { size: integer, type* }

**map[k-type,v-type]** or **map:k-type,v-type** or **map of ktype,vtype**
Dynamic record of key-value pairs.
Access: By k-type index

**struct**
Fixed record of symbol-value pairs.
Access: By symbol index
C mapping: classic packed struct


Constraint types
----------------

**null**
Null value as type constraint that represents a holder for a value.
If the holder is empty, the value is null, otherwise is the value itself.
Null is a characteristic not a type by itself. 
In declarations, if null is used as constraint the pair type|null conforms the holder.
If initial value is not defined, null symbol is initialized by default.

syntax:

type|null name;

c-representation:
struct null_value{ bool isNull; type value }

//This is valid for value-types. For referenced types needs to be polymorphic like null-reference

Mechanism types
---------------

**function** or **action** or **procedure**
By definition function is a stateless action and action statefull. In this case, all functions have state.
Argument List conforms a anonymous struct, so arguments can be named and used in interchangeable way.

declaration:

function functionName = (type0 arg0, type1 arg1, ... typeN argN ) : TypeR

execution:

a) With ordered arguments
TypeR result = functionName( 1, 'hello', 'world');

b) With named arguments
TypeR result = functionName( arg0:1, arg1:'hello', ..., argN:valueN );

c) Callable interface
execute functionName with { arg0:1, arg1:'hello', ..., argN:valueN };

Instance declarations
---------------------

type instanceName = initialValue | defaultValue;

Static/Dynamic typing switch
-----------------------------

**var**
This type is used as high level variant and represents all the primitive types including functions/object/prototypes

declaration with undefined

var name;

declaration with null is invalid with static types but valid in dynamic-typing
var name = null;

var name = 'hello';
name = 2;
name = 2.34;






