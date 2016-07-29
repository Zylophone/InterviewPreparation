<h1>Java</h1>

<h3>What is static in Java?</h3>
The static keyword in Java means that the variable or function is shared between all instances of that 
class as it belongs to the type, not the actual objects themselves. So if you have a variable: private 
static int i = 0; and you increment it (i++) in one instance, the change will be reflected in all instances.

<h3>What is final in Java?</h3>
**Variable** -
  Once a final variable has been assigned, it **always contains the same value.** If a final variable holds a 
  reference to an object, then the state of the object may be changed by operations on the object, but the 
  variable will always refer to the same object. This applies also to arrays, because arrays are objects; 
  if a final variable holds a reference to an array, then the components of the array may be changed by 
  operations on the array, but the variable will always refer to the same array.

**Class** -
  A final class **cannot be subclassed**. Doing this can confer security and efficiency benefits, so many of 
the Java standard library classes are final, such as java.lang.System and java.lang.String.

**Method** -
  A final method **cannot be overridden or hidden by subclasses**. This is used to prevent unexpected behavior 
from a subclass altering a method that may be crucial to the function or consistency of the class.


<h3>Difference between C++ and Java:</h3>
The most important difference is that Java is a memory-safe language, whereas C++ is not. This means 
that errors in Java programs are detected in defined ways—for example, attempting a bad cast or indexing 
an array out of bounds results in an exception. Similar errors in C++ lead to undefined behaviour, where 
instead of raising an exception or crashing, your program might keep running and crash later or even 
give the wrong answer or behaviour. Overall, the presence of unsafe features in C++ such as unchecked 
casts, pointer arithmetic, and manual memory management (delete) means that C++ programming is much more 
error-prone that Java programming.

<h3>Does Java support multiple inheritances?</h3>
**No**, C++, Common lisp and few other languages supports multiple inheritances while java doesn't support it. 
It is just to remove ambiguity, because multiple inheritances *can* cause ambiguity in few scenarios.

<h3>Interfaces</h3>
An interface is a contract: the guy writing the interface says, "hey, I accept things looking that way", and 
the guy using the interface says "Ok, the class I write looks that way". <br/>
An interface is an empty shell, there are only the signatures of the methods, which implies that the methods 
do not have a body. The interface can't do anything. It's just a pattern. <br/>
Implementing an interface consumes very little CPU, because it's not a class, just a bunch of names, and 
therefore there is no expensive look-up to do. It's great when it matters such as in embedded devices.

<h3>Abstract classes</h3>
Abstract classes, unlike interfaces, are classes. They are more expensive to use because there is a look-up 
to do when you inherit from them. <br />
Abstract classes look a lot like interfaces, but they have something more : you can define a behavior for them. 
It's more about a guy saying, "these classes should look like that, and they have that in common, so fill 
in the blanks!".

<h3>Can you Override/Overload a Constructor?</h3>
**Constructor overloading:** It means defining constructor in same class with different parameter list (parameter types, no of parameter). <br/>
**Constructor Overriding** is not possible.

<h3>4 Different Modifiers</h3>
Access level modifiers determine whether other classes can use a particular field or invoke a particular method. There are two levels of access control:
* At the top level—public, or package-private (default).
* At the member level—public, private, protected, or package-private (default). <br>

The following table shows the access to members permitted by each modifier. <br>

Modifier    | Class | Package | Subclass | World
  ---       | ---   | ---     | ---      | ---
public      |  y    |    y    |    y     |   y
protected   |  y    |    y    |    y     |   n
default     |  y    |    y    |    n     |   n
private     |  y    |    n    |    n     |   n

<h3>Can we have a Private Class?</h3>
Yes but only if it is a nested/ inner class.  A private outer class would be useless since nothing can access it.

<h3>Can we have a Private Constructor?</h3>
Yes, a constructor can be private. There are different uses of this. One such use is for the singleton design anti-pattern, which I would advise against you using. Another, more legitimate use, is in delegating constructors; you can have one constructor that takes lots of different options that is really an implementation detail, so you make it private, but then your remaining constructors delegate to it. <br>
As an example of delegating constructors, the following class allows you to save a value and a type, but it only lets you do it for a subset of types, so making the general constructor private is needed to ensure that only the permitted types are used. The common private constructor helps code reuse.

```
public class MyClass {
     private final String value;
     private final String type;

     public MyClass(int x){
         this(Integer.toString(x), "int");
     }

     public MyClass(boolean x){
         this(Boolean.toString(x), "boolean");
     }

     public String toString(){
         return value;
     }

     public String getType(){
         return type;
     }

     private MyClass(String value, String type){
         this.value = value;
         this.type = type;
     }
}
```

<h3>Why are String immutable?</h3>
String is immutable for several reasons, here is a summary:
* **Security:** parameters are typically represented as String in network connections, database connection urls, usernames/passwords etc. If it were mutable, these parameters could be easily changed.
*	**Synchronization and concurrency:** making String immutable automatically makes them thread safe thereby solving the synchronization issues.
*	**Caching:** when compiler optimizes your String objects, it sees that if two objects have same value (a="test", and b="test") and thus you need only one string object (for both a and b, these two will point to the same object).
*	**Class loading:** String is used as arguments for class loading. If mutable, it could result in wrong class being loaded (because mutable objects change their state).

<h3>What are the different types of Java memory?</h3>
* **Heap memory** is used by java runtime to allocate memory to Objects and JRE classes. Whenever we create any object, it’s always created in the Heap space. Garbage Collection runs on the heap memory to free the memory used by objects that doesn’t have any reference. Any object created in the heap space has global access and can be referenced from anywhere of the application.

* **Stack memory** is used for execution of a thread. They contain method specific values that are short-lived and references to other objects in the heap that are getting referred from the method. Stack memory is always referenced in LIFO (Last-In-First-Out) order. Whenever a method is invoked, a new block is created in the stack memory for the method to hold local primitive values and reference to other objects in the method. As soon as method ends, the block becomes unused and become available for next method. <br> Stack memory size is much smaller compared to Heap memory.

* **What is PermGen space?** It refers to a special part of the heap. The permanent generation is special because it holds meta-data describing user classes (classes that are not part of the Java language). Examples of such meta-data are objects describing classes and methods and they are stored in the Permanent Generation. Applications with large code-base can quickly fill up this segment of the heap which will cause java.lang.OutOfMemoryError: 

<h3>What is a Garbage Collector?</h3>
The garbage collector is a program which runs on the Java Virtual Machine which gets rid of objects which are not being used by a Java application anymore. It is a form of automatic memory management.
<h4>Can I run a GC in my program?</h4>
There is no way to force and immediate collection though as the garbage collector is non-deterministic. However, you can call System.gc() which simply is a hint to the garbage collector that you want it to do a collection.
<h4>What is the latest GD algorithm?</h4>
As of today, there are 4 GC algorithms available in the Java Hotspot VM:<br>
*	**The Serial GC** - recommended for client-style applications that do not have low pause time requirements.
*	**The Parallel GC** - use when the throughput matters.
*	**The Mostly-Concurrent GC** (also known as Concurrent Mark-Sweep GC(CMS)) - use when the latency matters.
*	**The Garbage First GC (G1)** - new GC algorithm, for CMS replacement.

<h3> What is a Thread? </h3>
Multithreading refers to two or more tasks executing concurrently within a single program. A thread is an independent path of execution within a program. Many threads can run concurrently within a program.

<h3> What is multithreading? </h3>


