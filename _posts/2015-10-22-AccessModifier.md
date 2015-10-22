---
layout: post
title: Access Modifiers in c#
---

### Access Modifiers

“Access modifiers (or access specifiers) are keywords in object-oriented languages that set the 
accessibility of classes, methods, and other members. Access modifiers are a specific part of programming 
language syntax used to facilitate the encapsulation of components.”

### Summary

1.	Default access modifier is private in the class members.
2.	Default access modifier is internal for class
3.	Default access modifier is public for namespaces, and we cannot add access specifiers on namespace including public again to it.
4.	A class can only be public or internal. It cannot be marked as protected or private.
5.	A class member can be public, internal, private or protected
6.	If a class is marked public but member is marked internal, It can be instantiated but member cannot be called in another assembly.
7.	private members cannot be accessed outside the class. public members can be accessed from anywhere outside.
8.	protected members in the base class can be accessed in inherited derived class.
9.	Static methods can only call static members in the class as static can be called even without an instance of a class.
10.	If a class is marked as internal it cannot be accessed outside the current assembly
11.	Though you cannot have multiple access modifier on member protected internal is allowed. 
12.	A class marked sealed cannot be inherited
