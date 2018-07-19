# Java Core

* How to make a class clonable
    + override `clone` method of `Object`.
    + implements `Clonable` interface.
* Immutability
    + the status of the object can not be changed once it has been initilized.
* How to make a class immutable
    + class should be final(no class can extend) 
    + a field should mark with `final`, if field is public/have setter
    + if field 
    + if there is collections, need to return new collections in getters
    + Make all mutable fields final so that it’s value can be assigned only once.
    + Initialize all the fields via a constructor performing deep copy.
* What is Garbage Collection? Explain how it is used. Is there a way to force garbage collection?
    + [ref](https://www.dynatrace.com/resources/ebooks/javabook/how-garbage-collection-works/) ++
    + java program stacks and one heap
    + garbage collection responsible for memory management
    + developer don't need to explicitly allocate memory and dealocate space.
    + the memory space of objects that don't refered by any varaible will be auto reclaim 
    + eliminating memory leaks
* What is the difference between final, finally & finalize?
    + **final** is used to apply restrictions on class/method/variable. Final class can't be inherited, final method can't be overridden and final variable value can't be changed.
    + **finally** in [try block], [close resources] code in the `finally` will be executed whether exception is handled or not.
    + **finalize** is used to perform clean up processing just **before object is garbage collected**. `public void finalize(){ }`
* What's `this` and `super`?
    + super is used to access methods of the base class while this is used to access methods of the current class.
    + `super()`, it refers to constructor of the base class
    + `this()`, it refers to the constructor of the current class
* What's a java package?
    + A package is a collection of related classes and interfaces providing access privileges and namespace management.
    + namespace management
    + diff class same purpose
    + 
* Explain the difference between the “equals ()” method and the “equals-equals (==) operator?
* When would you use an Interface instead of an abstract class?
* What does the "static" keyword do?
* What are exceptions? Discuss Exception Handling.

* What's a constructor?

* What are annotations?

## Java Core - Collections

* ?? how hashmap internally works??
    + hashmap use put and get 
    + key object should be immutable
    + put: 1. hashcode on key object 2. hashcode passed hash function 3. according to hashvalue, the key value pairs will be stored in an entry.
* What is the difference between List, Set, & Map? [ref](http://www.java67.com/2013/01/difference-between-set-list-and-map-in-java.html)
    + interfaces of Java collection framework
    + `List` provides **ordered/indexed/duplicates** collection of objs
    + `Set` provides **unordered/unique** collectin of objs
    + `Map` provides collection objs **based on Key-Value pair and HASHing**.
* Classes implements `List` interface. ??
* Classes implements `Set` interface. ??
* Classes implements `Map` interface. ??
    + HashTable, HashMap, TreeMap, LinkedHashMap, ConcurrentHashMap
* HashTable vs ConcurrentHashMap??
* What are generics/generic collections?
* HashMap: 2 object with same hashcode, how they stored in 
    + https://stackoverflow.com/a/6493946

## Java Core - Exception

* Explain try-catch, finally

