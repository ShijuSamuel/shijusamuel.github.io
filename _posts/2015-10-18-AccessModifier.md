---
layout: post
title: Access Modifiers in c#
---

### Access Modifiers

“Access modifiers (or access specifiers) are keywords in object-oriented languages that set the 
accessibility of classes, methods, and other members. Access modifiers are a specific part of programming 
language syntax used to facilitate the encapsulation of components.”

### Overview

-  Default access modifier is private for class members
-  Default access modifier is internal for class
-  Default access modifier is public for namespaces, and an explicit access modifier on namespace
    cannot be specified including public again to it
-  A class can only be public or internal and it cannot be marked as protected or private
-  A class member can be public, internal, private or protected
-  If a class is marked public but member is marked internal, it can be instantiated but member
  cannot be called/accessed in another assembly
-  private members cannot be accessed outside the class 
-  public members can be accessed from anywhere outside
-  protected members in the base class can be accessed in inherited derived class
- Static methods can only access static members in the class as static can be called even without an instance
- If a class is marked as internal it cannot be accessed outside the current assembly
- Though you cannot have multiple access modifier on member, "protected internal" is allowed
- class marked sealed cannot be inherited

### References
[CodeProject:All About C# Access Modifiers ](http://www.codeproject.com/Articles/792326/Diving-into-OOP-Day-All-About-Csharp-Access-Modifi)
[MSDN:Accessibility Levels](https://msdn.microsoft.com/en-us/library/ba0a1yw2.aspx)
[MSDN:Modifiers](https://msdn.microsoft.com/en-us/library/6tcf2h8w.aspx)
