4 Pillars
1.	Abstraction
Abstraction is a process of exposing essential feature of an entity
while hiding other irrelevant detail. Why would you want to use abstraction?
abstraction reduces code complexity and at the same time it makes your aesthetically 
pleasant.

2.	Encapsulation

We have to take in consideration that Encapsulation is somehow related to Data Hiding.
Encapsulation is when you hide your modules internal data and all other implementation 
details/mechanism from other modules. It is also a way of restricting access to certain 
properties or component. 
Remember, Encapsulation is not data hiding, but Encapsulation leads to data hiding.

3.	Inheritance
The ability of creating a new class from an existing class.
Like the word Inheritance literally means it is a practice of passing on property, titles, 
debts, rights and obligations upon the death of an individual. In OOP this is somewhat 
true(Except the death of an individual), where The base class(the existing class sometimes 
called as the Parent class) has properties and methods that will be inherited by the sub 
class(sometimes called a subtype or child class) and it can have additional properties or
methods.
Inheritance is also a way to use code of an existing objects.

4.	Polymorphism
Just like in biology, Polymorphism refers to the ability to take into different forms or stages. 
A subclass can define its own unique behaviour and still share the same functionalities or behavior 
of its parent/base class. Yes, you got it right, subclass can have their own behavior and share 
some behaviour from its parent class BUT!! not vice versa.
A parent class cannot have the behaviour of its subclass.

S.O.L.I.D.:
Single-responsibility principle
•	a class should have only a single responsibility (i.e. only one potential change in the software's 
    specification should be able to affect the specification of the class)
Open-closed principle
•	“software entities … should be open for extension, but closed for modification.”
Liskov substitution principle
•	“objects in a program should be replaceable with instances of their subtypes without altering the 
    correctness of that program.”
Interface segregation principle
•	“many client-specific interfaces are better than one general-purpose interface.”
Dependency Inversion Principle
•	one should “Depend upon Abstractions. Do not depend upon concretions.”


Definition of Class and Object
Objects have states and behaviors. Example: A dog has states - colour, name, breed as well as behaviours -wagging, 
barking, eating. An object is an instance of a class. 

A class can be defined as a template/blue print that describes the behaviours/states that object of its type support.

Method Overriding and Overloading:
Method overloading deals with the notion of having two or more methods in the same class with the same name but 
different arguments. Done at compile time.
Method overriding means having two methods with the same arguments, but different implementations. Done at runtime.

