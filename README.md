# c-plus
C+ Programming Language Design

C+ Programming Language and Transpilation design
================================================

C+ is a programming language design project and transpiler software to C standard output code.

The main objective of which is to provide a similar C language but with significant reduction in syntax complexity and low-level features that can be used in the development of high-level applications.
Inspired by the syntax and base ideas of C, C++ and ECMAScript we have a humble aproximation of want we want.

A language that:

a) Allows the possibility to write code with the flexibility of dynamic typed languages as ECMAScript but with strong typing and interface support with a uniform and clean syntax.
b) Allows the possibility to build binary executables.
c) Standarized mechanisms for serialization/deserialization of data structures.
d) Have a minimal set of primitive datatypes and data structures.
e) Inhibits the programmers to write code with a lot of ways to perform the same.
f) Clear policy of memory management and concurrency facilities.

Primitive types
===============

Types can be classified over a long list. There are an extensive classification of "types". The simplified classification is:

Value Types: Is the value itself (the representation). Ex: int, float, double, bool, date, etc..
Referenced Types: Are types that holds a representation of values or collection of values. (Data Structures, Pointers, SharedPointers, etc)


C+ have the following Primitive Types

Value Types    		C Possible Mapping		Semantic												
---------------------------------------------------------------------------------------------------------------
byte				int8					Minimal Unit of Information for Low Level Exchange Compatibility

int					int64					Integer number with the maximum range (signed/unsigned) variants
uint				uint64

double				double					Double

bool				int8					Boolean (true/false)

blob				void*					Binary Array of Bytes

time				double 					Time
date 				char[]					Date
datetime			char[]					Date+Time
	
string				char*					String text (unfixed size)


Reference Types
--------------------------------------------------------------------------------------------------------------

object				struct 					
array				struct array { uint64, void* }
map 				struct pair { string, value }; struct map { uint64, pair* }


Utility Types
---------------------------------------------------------------------------------------------------------------
null				struct null;
undefined			struct undefined;



function name( type:name, type:name ) : type:name
{
	
}


let fname = function(type:name, type:name):type:name;

fname.call() || fname();


class X
{
	private:



	public:

	
}




