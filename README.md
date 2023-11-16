
C+ Programming Language
=======================

C+ is a project of programming language for educational purposes. The ideas behind this project is to create a similar C language without low level facilities and minimalistic syntax with the power of strong/weak typing and high level abstraction mechanisms.

Some objetives of this language are:   

 - Strong/Weak typing switching
 - Remove all the low level keywords and low level utilities.
 - Add interfaces support and class/module abstraction mechanism.
 - Preserve C ABI interface
 - No scripting, only compiled/binary executables.
 - Standarized mechanisms for serialization/deserialization of data structures. 
 - Have a minimal set of primitive types (value-types and referenced-types).
 - Consistent syntax in order to avoid programmers to write code in different ways to perform same behaviour.  
 - Clear policy of memory management and concurrency facilities.   
  
Language technology
-------------------   

This language works with a transpiler pair. Does not compile by its own bytecode.   
The decisions behind this are:  

 - Avoid virtual machine design and build compilers from scratch.
 - Take the advantages of compiler optimization from well known languages (C).
 - Open the possibility by translate the language into any language in the future.
 - More easy development for concrete results.

   

Primitive value types
---------------------
   
In type theory, there are a lot of classifications of types. The most simple classification starts with value-types and referenced-types. Value-types are the representation of the data by itself while Referenced-Types holds a reference to a one/many Value-types. The following draft have the primitive type proposal especification:   

**byte**   
Minimal binary unit of data (unsigned integer of 8bits) : 0 ... 256   
`byte example = 128;`   

**integer**, **uinteger**    
Integer number with the largest range (signed/unsigned)   
`integer example = 900001;`   

**double**   
Long decimal number with floating point
`double example = 45.9;`     
   
**decimal**   
Long decimal number with fixed point
`decimal example = 44.00D;`

**boolean**    
Boolean value (True/False)   
`boolean example = false;`   
   
**blob**   
Dynamic binary array of bytes.
`blob example = []:`
`blob example = [25,23,10,18,0,244,120];`
   
**string**   
Dynamic binary string without encoding like [PHP String Design](https://www.php.net/manual/en/language.types.string.php#language.types.string.details)   
`string example = 'Hello World'`
    
Primitive referenced types with parametrization   
-----------------------------------------------   
 **array**
Dynamic typed array by accesed by integer index
`array example = ['Hello', 1, 3.1416 ];`

**array[type]**   
Strong typed array of value-types accesed by integer index
`array[string] example = ['Hello', 'World!'];`
`out.write( example[1] );`   

**map**   
Dynamic typed map of key-value pairs
`map example = { 'id':2, 233:'C+','price':23.17 };`
`out.write( example['id'] )`;

**map[k-type,v-type]**   
Strong typed map of key-value pairs
`map[string,int] example = { 'id':2, 'name':'C+', 'description':'Programming Language' };
out.write( example['id'] );`    

**struct**   
Fixed record of symbol-value pairs.   
Access: By symbol index   
C mapping: classic packed struct   

`struct example = ( integer id, string name, string description );`
out.write( example[id] );`

Predefined standard types
--------------------------    

**resource**
External resources with predefined properties and interface   
   
Constraint Auxiliar types   
--------------------------
   
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
   
**function**
By definition function is a stateless action and action statefull. In this case, all functions have state.   
Argument List conforms a anonymous struct, so arguments can be named and used in interchangeable way.   
   
declaration:   
      
`**function** functionName = (**type0** arg0, **type1** arg1, ... , **typeN** argN ) : **TypeR**`
   
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

