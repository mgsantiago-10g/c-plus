
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
 - No low-level facilities like pointers and keywords for memory manipulation.
  
Language technology
-------------------   

This language works with a transpiler pair. Does not compile by its own bytecode.   
The decisions behind this are:  

 - Avoid virtual machine design and build compilers from scratch.
 - Take the advantages of compiler optimization from well known languages (C).
 - Open the possibility by translate the language into any language in the future.
 - More easy development for concrete results.


Primitive types
---------------------
   
In type theory, there are a lot of classifications of types. The most simple classification starts with value-types and referenced-types. Value-types are the representation of the data by itself while Referenced-Types holds a reference to a one/many Value-types. The following draft have the primitive types proposal especifications:   

 - **byte**   
Minimal binary unit of data (unsigned integer of 8 bits)  
`byte example = 128;`   

 - **integer** 
Integer number with the largest range (signed/unsigned)   
`integer example = 900001;`   

 - **double**   
Long decimal number with floating point
`double example = 45.9;`     
   
 - **boolean**    
Boolean value (True/False)   
`boolean example = false;`   
   
 - **blob**   
Dynamic binary array of bytes.   
`blob example = []:`   
`blob example = [25,23,10,18,0,244,120];`
   
 - **string**   
Dynamic binary string without encoding like [PHP String Design](https://www.php.net/manual/en/language.types.string.php#language.types.string.details)   
`string example = 'Hello World'`   
    
 - **array[type]**   
Strong typed array of value-types accesed by integer index   
`array[string] example = ['Hello', 'World!'];`   
`out.write( example[1] );`    
  
 - **map[k-type, v-type]**   
Dynamic typed map of key-value pairs  
`map[string,string] example = { 'id':'2', 'name':'C+','description':'Programming Language' };`  
`out.write( example['id'] )`;   

Derived types
----------------- 

 - **null**   
Null is a constraint type that works with another type and can have only two possible values: 'null'  or a type-value.  
`string|null name;`
   
Internally null constraint type, works as a holder. When the instance is declared without initialization the holder state is empty and the value is 'null'. Otherhand, if holder is not empty the inner value.
    
`string|null name = 'Hello World!';`    
`name = null;`    
`name = 'Nice';`   
   
 - **struct *name***   
Fixed record of type-symbol pairs.  
`struct name example = ( integer id, string name, string|null description );`  
`out.write( example[id] );`  
    
Mechanism types   
---------------   
   
 - **function**    
By definition function is a stateless and functor is stateful. The functor is a generalization of functions, so is the default in C+   
The parameter list works as a anonymous struct object.   
`function functionName = (type0 arg0, type1 arg1, ... , typeN argN ) : type { ...code... }`  
   
 - With ordered arguments   
`type result = functionName( 1, 'hello', 'world');`   
   
 - With named arguments   
`type result = functionName( arg0:1, arg1:'hello', ..., argN:valueN );`    
    
 - **method**   
Is a special function that have available 'this' keyword to be used inside who can be bindable objects.   
`method name = className::(type0 arg0, type1 arg1, ... , typeN argN ) : type { ...code... }`  
`type result = methodName[object]( arg0, arg1, ..., argN);    
    
 - **class *name***    
Is a map of key('string') with values(method)  
   
Instance declarations   
---------------------   
   
Declarations works in all cases with 'type' signature at left side and 'rvalue' at right side.   
Without presence of null constraint working with paired type, the initialization is required by type value literal representation in other case default is null.    
    
`type instanceName = 'type-value';`   
`type|null instanceName;  //null is the default value`  
   
Dynamic types   
-----------------------------   
     
 - **var** or *undefined-type*  
This type is the indicator of dynamic typed element. And it have three possible states: 'undefined', 'null', *type-value*, *type-reference*   
Null constraint is not required to be defined. Ignoring type signature in function arguments is considered var.   
    
`var instance = 8;`  
`instance = 'Hello';`   
`instance = 123.4';`  
`instance = null;`  
`instance = undefined;`    
    
For functions:   
`function functionName = (arg0,arg1, ... ,argN ):var`   
`function functionName = (arg0,integer arg1, ... ,argN ):double`   
    
In this cases, the hidden type of return means 'undefined' in the case of no-return, or 'null'/'value' when return is utilized.   
    
`var example = functionName(1,2,3);`  
`example? out.write('value is: ', example) : out.write('no value'); 
