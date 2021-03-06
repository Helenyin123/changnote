# Languages and OOP Basic Knowledge

## Java, C++ and Python

#### [Difference Between Java and C++](https://www.wikiwand.com/en/Comparison_of_Java_and_C%2B%2B)

| Java | C++ |
| :---: | :---: |
| Platform Independent | Platform Dependent |
| Run in Java Virtual Machine | Run in Native Executable Machine |
| No pointers | Have Pointers |
| Support Pass-by-Reference and Pass-by-Value on all types | All types\(primitive & reference\) are passed by value |
| \(Arithmetic, Comparison\) Operators Not Overridable | Support Operator Overloading |
| Automatic Garbage Collection | Manually Memory Management |
| Support Multithreading | Doesn't Support Multithreading |
| No Templates, support Generic | Support Templates |
| No Global Variables | Have Global Variables |
| Only Single Inheritance of class | Support multiple inheritance of class |
| Class\(structure + method\) and Object | Structures and Unions |

##### What is Platform Independent?

Platform independence means that the same program works on any platform \(operating system\) without any modification.

Some languages are platform independent at the source code level \(C/C++ is a good example\) but lose platform independence once the code is compiled \(since native code is platform specific\). Java retains platform independence even after code is compiled because it compiles to platform independent byte code \(the actual conversion to native code is handled at a later time after the byte code is loaded by the JVM\). The same Java algorithms \(typically compiled to Java byte code and packaged in a .jar file\) will run identically on Windows and Linux.

##### Inheritance

##### Garbage Collection & Memory Management

Java offers automatic garbage collection, which may be bypassed in specific circumstances via the real time java specification. Memory management in C++ is usually done via constructors, destructors and small pointers. The C++ standard permits garbage collection, but doesn't require it. Garbage collection is rarely used in practice.

#### Comparison Between Java and Python

**Similarity**  
1. Object Oriented Language  
2. Excellent cross platform support  
3. Immutable Strings  
4. Deep Relative Standard Library

**Difference**  
1. Java and C++ use braces and semicolon to separate sentence, while Python use tab/indentation, which makes it to be the most human readable programming languages in wide use.  
2. Python compile the program automatically at runtime, java need to compile first then run the program  
3. Python have a large library for machine learning and data science research, java has much less resource in those field.  
4. Java is statically typed, which means Names are bound to types at compile time via explicit type declaration. Python is dynamically typed. Names have no strong binding to their type, which can be very powerful and convenient.

| Java | Python |
| :---: | :---: |
| Static Types | Dynamic Types |
| Braces and Semicolon to separate sentence | Indentation/Tab to separate sentence |
| Compile first then rum the program | Compile automatically at runtime |
| Less resources than Python | large library for machine learning and data science |

**Type**

In java, all variable names must be explicitly declared. In python. you never declare anything. Assignment statement binds a name to an object and the object can be any type. Java container objects\(vector and arraylist\) hold objects of generic type. But can't hold primitive type. You must first convert int to Integer.

### Java

**Difference between HashMap Vs HashTable:**

* Hashtable is synchronized, whereas Hashmap is not. Hashmap is better for non-threaded application.
* Hashtable doesn't allow null keys or values. HashMap allows one null key and any number of null values.
* One of Hashmap's LinkedHashMap,  

#### Java 8 New Features

* **Lambda Expression**: enable you to treat a function as a method argument or code as data. 
* **Method Reference**: It's used to refer methods of functional interface. They are a subset of lambda expression.
* **Default Method**: enable you to add a new method to the interface of your library ad ensure binary compatibility with older version.
* **ForEach\(\) Method**: a new method to iterate over collections. It's defined in Iterable and Stream interface.
* **Stream API**: stream is introduced to process elements in sequence
* **Date and Time API**: being improved compare to previous version

## Object Oriented Programming

OOP is a programming paradigm that based on the concept of objects. Object contains data, called filed/attributes and code in the form of procedures, known as method. we can access and modify an object's data filed by calling methods.

One significant OOP style is **class-based,** meaning that objects are instance of classes.

Another OOP style is** prototype-based, **in which the inheritance is performed via a process of reusing existing object via delegation that serve as prototypes. In prototype-based language, there are no explicit classes, objects inherit directly from other objects through a prototype property. There are two methods of constructing new a new object: create an object from nothing or through cloning an existing object.

```js
var foo = {name: "foo", one: 1, two:2};
var bar = {two: "two", three: 3};
// Object.setPrototypeOf() is a method to set inheritance
// foo is now bar's prototype
Object.setPrototypeOf(bar, foo);
bar.one; //return 1
bar.two; // return "two"
bar.three; // return 3
bar.name; // return "foo"
```

```js
var foo = {one: 1, two: 2};
var bar = Object.create(foo);
bar.three = 3;
bar.one;//return 1
bar.two; //return 2
bar.three; // return 3
```

In class-based language, a new instance is constructed through a class's constructor function. The new instance will inherit all the methods and properties that were defined in the class.

Prototype OOP use generalized objects, which can be cloned and extended. Many prototype-based systems encourage the alternation of prototypes during runtime, whereas only a few class-based system allow classes to be altered during execution of a program.

Almost all prototype-based system are dynamically typed. In most prototype languages there exist a root object, often called Object, which is the default prototype for all other created objects.

| Class-Based OOP | Prototype-Based OOP |
| :---: | :---: |
| C++, Java, Python, Ruby | JavaScript, Python, Perl, R, Self |
| Object inherits from class | Object inherits from other object through prototype property |
| Inheritance\(relationship between class and object\) | Delegation \(link between objects\) |
| Class is defined beforehand, normally can't be changed later | Prototype's variables and methods can be added or changed later. Both data and methods are referred as "slots". |
| Objects are instance of class | Objects are primary entities. Prototype is implicit. |
| C++ support multiple inheritance. Java support single inheritance. | Every Object has one prototype link. Only support single inheritance. |
| C++, Java is statically typed. Python is dynamically typed. | Mostly dynamically typed |

**Class: **The abstraction of a give type of real objects. It define the data members and member functions.

**Object**: instances of classes

**Encapsulation:** If a class doesn't allow outside code to access internal object data, it permits access through class methods only, this form of data hiding is called encapsulation.** **Encapsulation** **binds the data field and methods together and keep both safe from outside interference and misuse. Java and C++ have keywords like "public"\(access form all classes\), "private"\(access form the same class\), "protected"\(access from the same class and its subclasses\).

**Inheritance: **"is a type of" relationship.

subclasses can override the methods defined by superclasses. Abstract classes can't be instantiated as objects, they exist only for the purpose of inheritance into other concrete class.

**Polymorphism**: calling code can be altered based on whether an object belongs to a parent class or one of its descendants.

## Design Pattern

A design pattern is a template for how to solve a problem that can be used in many different situations.

#### Creational Design Pattern

A design pattern that deal with object creation mechanism

* **Singleton Pattern**:
* **Factory Pattern**: uses factory methods to deal with creating objects without specifying the exact class of object that will be created. This is done by creating objects via a factory method, which is either specified in an interface and implemented in implementing classes \(concrete classes\); or implemented in a base class, which can be overridden when inherited in derived classes; rather than by a constructor.

```java
public class CurrencyFactory {
    public static Currency getCurrencyByCountry(String cnty) throws Exception{
        if("IN".equalsIgnoreCase(cnty)){
            return new India();
        } else if("USA".equalsIgnoreCase(cnty)){
            return new USA();
        }
        throw new Exception("Invalid country...");
    }
    public static void main(String a[]){
        Currency india = CurrencyFactory.getCurrencyByCountry("IN");
        Currency usa = CurrencyFactory.getCurrencyByCountry("USA");
        System.out.println("Indian currency: "+india.getCurrency());
        System.out.println("Indian currency symbol: "+india.getSymbol());
    }      
}
public interface Currency {
    public String getCurrency();
    public String getSymbol();
}
public class USA implements Currency{
    @Override
    public String getCurrency() {
        return "Dollar";
    } 
    public String getSymbol() {
        return "$";
    }
}
public class India implements Currency{
    @Override
    public String getCurrency() {         
        return "Rupee";
    }
    public String getSymbol() {
        return "Rs";
    }
}
```

* **Abstract Factory Pattern**
* **Builder Pattern**
* **Prototype Pattern**

#### Structural Design Pattern

* Adapter Pattern
* Bridge Pattern
* Composite Pattern
* Proxy Pattern

#### Behavior Design Pattern

* Command Pattern
* Iterator Pattern
* Visitor Pattern



