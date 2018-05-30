# Java Interview Questions Compilation

## 1. Explain JVM, JRE and JDK?

__JVM (Java Virtual Machine)__: It is an abstract machine. It is a specification that provides run-time environment in which java bytecode can be executed. It follows three notations:

* Specification: It is a document that describes the implementation of the Java virtual machine. It is provided by Sun and other companies.
* Implementation: It is a program that meets the requirements of JVM specification.
* Runtime Instance: An instance of JVM is created whenever you write a java command on the command prompt and run the class.

__JRE (Java Runtime Environment)__ : JRE refers to a runtime environment in which java bytecode can be executed. It implements the JVM (Java Virtual Machine) and provides all the class libraries and other support files that JVM uses at runtime. So JRE is a software package that contains what is required to run a Java program. Basically, it’s an implementation of the JVM which physically exists. 

__JDK(Java Development Kit)__ : It is the tool necessary to compile, document and package Java programs. The JDK completely includes JRE which contains tools for Java programmers. The Java Development Kit is provided free of charge. Along with JRE, it includes an interpreter/loader, a compiler (javac), an archiver (jar), a documentation generator (javadoc) and other tools needed in Java development. In short, it contains JRE + development tools.

Refer to this below image and understand how exactly these components reside: ![java](https://cdn-images-1.medium.com/max/1600/0*MsGzRuN1Q09dOkwi.png)

## 2. Is Java a Compiled or an Interpreted programming language ?

Java implementations typically use a two-step compilation process. Java source code is compiled down to bytecode by the Java compiler. The bytecode is executed by a Java Virtual Machine (JVM). Modern JVMs use a technique called Just-in-Time (JIT) compilation to compile the bytecode to native instructions understood by hardware CPU on the fly at runtime.

Some implementations of JVM may choose to interpret the bytecode instead of JIT compiling it to machine code, and running it directly. While this is still considered an "interpreter," It's quite different from interpreters that read and execute the high level source code (i.e. in this case, Java source code is not interpreted directly, the bytecode, output of Java compiler, is.)

It is technically possible to compile Java down to native code ahead-of-time and run the resulting binary. It is also possible to interpret the Java code directly.

At run time, JVM interprets the byte code and executes them. However, a full interpreter based execution potentially hurts the performance of application since pretty much everything that a compiler could have done upfront at compile time will now be done repeatedly by the interpreter and this adds to the overall execution time of the program.

To summarize, depending on the execution environment, bytecode can be:

* compiled ahead of time and executed as native code (similar to most C++ compilers)
* compiled just-in-time and executed
* interpreted
* directly executed by a supported processor (bytecode is the native instruction set of some CPUs)

![java](http://novtopro.qiniudn.com/blog/2017/01/21/kotlin-kickstart/jit.png)

## 3. Why java is not 100% Object-oriented?

Java is not 100% Object-oriented because it makes use of eight primitive datatypes such as boolean, byte, char, int, float, double, long, short which are not objects.

## 4. What are wrapper classes?

Wrapper classes converts the java primitives into the reference types (objects). Every primitive data type has a class dedicated to it. These are known as wrapper classes because they “wrap” the primitive data type into an object of that class. Refer to the below image which displays different primitive type, wrapper class and constructor argument. 

## 5. What is singleton class and how can we make a class singleton?

Singleton class is a class whose only one instance can be created at any given time, in one JVM. A class can be made singleton by making its constructor private.

```java
// Java program implementing Singleton class
// with getInstance() method
class Singleton
{
    // static variable single_instance of type Singleton
    private static Singleton single_instance = null;
 
    // variable of type String
    public String s;
 
    // private constructor restricted to this class itself
    private Singleton()
    {
        s = "Hello I am a string part of Singleton class";
    }
 
    // static method to create instance of Singleton class
    public static Singleton getInstance()
    {
        if (single_instance == null)
            single_instance = new Singleton();
 
        return single_instance;
    }
}
```

## 6. What is the difference between Array list and vector?

|Array List	| Vector |
| ---------- | -------|
|Array List is not synchronized. | Vector is synchronized. |
|Array List is fast as it’s non-synchronized. | Vector is slow as it is thread safe. |
|If an element is inserted into the Array List, it increases its Array size by 50%.	|Vector defaults to doubling size of its array. |
|Array List does not define the increment size.	| Vector defines the increment size. |
|Array List can only use Iterator for traversing an Array List.	| Except Hashtable, Vector is the only other class which uses both Enumeration and Iterator. |

## 7.  What is the difference between equals() and == ?

Equals() method is defined in Object class in Java and used for checking equality of two objects defined by business logic.
“==” or equality operator in Java is a binary operator provided by Java programming language and used to compare primitives and objects. public boolean equals(Object o) is the method provided by the Object class. The default implementation uses == operator to compare two objects. For example: method can be overridden like String class. equals() method is used to compare the values of two objects.

* .equals(...) will only compare what it is written to compare, no more, no less.
* If a class does not override the equals method, then it defaults to the equals(Object o) method of the closest parent class that has overridden this method.
* If no parent classes have provided an override, then it defaults to the method from the ultimate parent class, Object, and so you're left with the Object#equals(Object o) method. Per the Object API this is the same as ==; that is, it returns true if and only if both variables refer to the same object, if their references are one and the same. Thus you will be testing for object equality and not functional equality.
* Always remember to override hashCode if you override equals so as not to "break the contract". As per the API, the result returned from the hashCode() method for two objects must be the same if their equals methods show that they are equivalent. The converse is not necessarily true.

## 8. What are the differences between Heap and Stack Memory?
The major difference between Heap and Stack memory are:

|Features	| Stack |	Heap |
|-----------| -------| ------|
|Memory	| Stack memory is used only by one thread of execution.	| Heap memory is used by all the parts of the application.|
| Access |	Stack memory can’t be accessed by other threads. |	Objects stored in the heap are globally accessible. |
| Memory Management	| Follows LIFO manner to free memory. |	Memory management is based on generation associated to each object. |
| Lifetime	| Exists until the end of execution of the thread.	| Heap memory lives from the start till the end of application execution. |
| Usage |	Stack memory only contains local primitive and reference variables to objects in heap space. |	Whenever an object is created, it’s always stored in the Heap space. |

## 9. What is Polymorphism?

If you think about the Greek roots of the term, it should become obvious.

* Poly = many: polygon = many-sided, polystyrene = many styrenes (a), polyglot = many languages, and so on.
* Morph = change or form: morphology = study of biological form, Morpheus = the Greek god of dreams able to take any form.
So polymorphism is the ability (in programming) to present the same interface for differing underlying forms (data types).

For example, in many languages, integers and floats are implicitly polymorphic since you can add, subtract, multiply and so on, irrespective of the fact that the types are different. They're rarely considered as objects in the usual term.

But, in that same way, a class like BigDecimal or Rational or Imaginary can also provide those operations, even though they operate on different data types.

The classic example is the Shape class and all the classes that can inherit from it (square, circle, dodecahedron, irregular polygon, splat and so on).

With polymorphism, each of these classes will have different underlying data. A point shape needs only two co-ordinates (assuming it's in a two-dimensional space of course). A circle needs a center and radius. A square or rectangle needs two co-ordinates for the top left and bottom right corners and (possibly) a rotation. An irregular polygon needs a series of lines.

By making the class responsible for its code as well as its data, you can achieve polymorphism. In this example, every class would have its own Draw() function and the client code could simply do:

shape.Draw()
to get the correct behavior for any shape.

This is in contrast to the old way of doing things in which the code was separate from the data, and you would have had functions such as drawSquare() and drawCircle().

__Another definition__

The word polymorphism is used in various contexts and describes situations in which something occurs in several different forms. In computer science, it describes the concept that objects of different types can be accessed through the same interface. Each type can provide its own, independent implementation of this interface. It is one of the core concepts of object-oriented programming (OOP).

If you’re wondering if an object is polymorphic, you can perform a simple test. If the object successfully passes multiple is-a or instanceof tests, it’s polymorphic. As I’ve described in my post about inheritance, all Java classes extend the class Object. Due to this, all objects in Java are polymorphic because they pass at least two instanceof checks.

Different Types of Polymorphism
Java supports 2 types of polymorphism:

* static or compile-time
* dynamic

### Static Polymorphism
Java, like many other object-oriented programming languages, allows you to implement multiple methods within the same class that use the same name but a different set of parameters. That is called method overloading and represents a static form of polymorphism.

The parameter sets have to differ in at least one of the following three criteria:

* They need to have a different number of parameters, e.g. one method accepts 2 and another one 3 parameters.
* The types of the parameters need to be different, e.g. one method accepts a String and another one a Long.
* They need to expect the parameters in a different order, e.g. one method accepts a String and a Long and another one accepts a Long and a String. This kind of overloading is not recommended because it makes the API difficult to understand.

In most cases, each of these overloaded methods provides a different but very similar functionality.

Due to the different sets of parameters, each method has a different signature. That allows the compiler to identify which method has to be called and to bind it to the method call. This approach is called static binding or static polymorphism.

Let’s take a look at an example.

__A Simple Example for Static Polymorphism__

I use the same CoffeeMachine project as I used in the previous posts of this series. You can clone it at https://github.com/thjanssen/Stackify-OopInheritance.

The BasicCoffeeMachine class implements two methods with the name brewCoffee. The first one accepts one parameter of type CoffeeSelection. The other method accepts two parameters, a CoffeeSelection, and an int.

```
public class BasicCoffeeMachine {
    // ...
    public Coffee brewCoffee(CoffeeSelection selection) throws CoffeeException {
        switch (selection) {
        case FILTER_COFFEE:
            return brewFilterCoffee();
        default:
            throw new CoffeeException(
                "CoffeeSelection ["+selection+"] not supported!");
        }   
    }
    public List brewCoffee(CoffeeSelection selection, int number) throws CoffeeException {
        List coffees = new ArrayList(number);
        for (int i=0; i<number; i++) {
            coffees.add(brewCoffee(selection));
        }
        return coffees;
    }
    // ...
}
```

Now when you call one of these methods, the provided set of parameters identifies the method which has to be called.

In the following code snippet, I call the method only with a CoffeeSelection object. At compile time, the Java compiler binds this method call to the brewCoffee(CoffeeSelection selection) method.

```
BasicCoffeeMachine coffeeMachine = createCoffeeMachine();
coffeeMachine.brewCoffee(CoffeeSelection.FILTER_COFFEE);
```

If I change this code and call the brewCoffee method with a CoffeeSelection object and an int, the compiler binds the method call to the other brewCoffee(CoffeeSelection selection, int number) method.

```
BasicCoffeeMachine coffeeMachine = createCoffeeMachine();
List coffees = coffeeMachine.brewCoffee(CoffeeSelection.ESPRESSO, 2);
```
### Dynamic Polymorphism

This form of polymorphism doesn’t allow the compiler to determine the executed method. The JVM needs to do that at runtime.

Within an inheritance hierarchy, a subclass can override a method of its superclass. That enables the developer of the subclass to customize or completely replace the behavior of that method.

It also creates a form of polymorphism. Both methods, implemented by the super- and subclass, share the same name and parameters but provide different functionality.

Let’s take a look at another example from the CoffeeMachine project.

__Method Overriding in an Inheritance Hierarchy__
The BasicCoffeeMachine class is the superclass of the PremiumCoffeeMachine class.

![java](https://stackify.com/wp-content/uploads/2017/12/word-image-13.png)

Both classes provide an implementation of the brewCoffee(CoffeeSelection selection) method.

```
import java.util.ArrayList;
import java.util.List;
import java.util.Map;
public class BasicCoffeeMachine extends AbstractCoffeeMachine {
    protected Map beans;
    protected Grinder grinder;
    protected BrewingUnit brewingUnit;
    public BasicCoffeeMachine(Map beans) {
        super();
        this.beans = beans;
        this.grinder = new Grinder();
        this.brewingUnit = new BrewingUnit();
        this.configMap.put(CoffeeSelection.FILTER_COFFEE, new Configuration(30, 480));
    }
    public List brewCoffee(CoffeeSelection selection, int number) throws CoffeeException {
        List coffees = new ArrayList(number);
        for (int i=0; i<number; i++) {
            coffees.add(brewCoffee(selection));
        }
        return coffees;
    }
    public Coffee brewCoffee(CoffeeSelection selection) throws CoffeeException {
        switch (selection) {
        case FILTER_COFFEE:
            return brewFilterCoffee();
        default:
            throw new CoffeeException("CoffeeSelection ["+selection+"] not supported!");
        }
    }
    private Coffee brewFilterCoffee() {
        Configuration config = configMap.get(CoffeeSelection.FILTER_COFFEE);
        // grind the coffee beans
        GroundCoffee groundCoffee = this.grinder.grind(this.beans.get(CoffeeSelection.FILTER_COFFEE), config.getQuantityCoffee());
        // brew a filter coffee
        return this.brewingUnit.brew(CoffeeSelection.FILTER_COFFEE, groundCoffee, config.getQuantityWater());
    }
    public void addBeans(CoffeeSelection selection, CoffeeBean newBeans) throws CoffeeException {
        CoffeeBean existingBeans = this.beans.get(selection);
        if (existingBeans != null) {
            if (existingBeans.getName().equals(newBeans.getName())) {
                existingBeans.setQuantity(existingBeans.getQuantity() + newBeans.getQuantity());
            } else {
                throw new CoffeeException("Only one kind of beans supported for each CoffeeSelection.");
            }
        } else {
            this.beans.put(selection, newBeans);
        }
    }
}
```

```
import java.util.Map;
public class PremiumCoffeeMachine extends BasicCoffeeMachine {
    public PremiumCoffeeMachine(Map beans) {
        // call constructor in superclass
        super(beans);
        // add configuration to brew espresso
        this.configMap.put(CoffeeSelection.ESPRESSO, new Configuration(8, 28));
    }
    private Coffee brewEspresso() {
        Configuration config = configMap.get(CoffeeSelection.ESPRESSO);
        // grind the coffee beans
        GroundCoffee groundCoffee = this.grinder.grind(this.beans.get(CoffeeSelection.ESPRESSO), config.getQuantityCoffee());
        // brew an espresso
        return this.brewingUnit.brew(
            CoffeeSelection.ESPRESSO, groundCoffee, config.getQuantityWater());
    }
    public Coffee brewCoffee(CoffeeSelection selection) throws CoffeeException {
        if (selection == CoffeeSelection.ESPRESSO)
            return brewEspresso();
        else
            return super.brewCoffee(selection);
    }
}
```

If you read the post about the OOP concept inheritance, you already know the two implementations of the brewCoffee method. The BasicCoffeeMachine only supports the CoffeeSelection.FILTER_COFFEE. The brewCoffee method of the PremiumCoffeeMachine class adds support for CoffeeSelection.ESPRESSO. If it gets called with any other CoffeeSelection, it uses the keyword super to delegate the call to the superclass.

__Late Binding__

When you want to use such an inheritance hierarchy in your project, you need to be able to answer the following question: which method will the JVM call?

That can only be answered at runtime because it depends on the object on which the method gets called. The type of the reference, which you can see in your code, is irrelevant. You need to distinguish three general scenarios:

* Your object is of the type of the superclass and gets referenced as the superclass. So, in the example of this post, a BasicCoffeeMachine object gets referenced as a BasicCoffeeMachine.
* Your object is of the type of the subclass and gets referenced as the subclass. In the example of this post, a PremiumCoffeeMachine object gets referenced as a PremiumCoffeeMachine.
* Your object is of the type of the subclass and gets referenced as the superclass. In the CoffeeMachine example, a PremiumCoffeeMachine object gets referenced as a BasicCoffeeMachine.


__Superclass Referenced as the Superclass__

The first scenario is pretty simple. When you instantiate a BasicCoffeeMachine object and store it in a variable of type BasicCoffeeMachine, the JVM will call the brewCoffee method on the BasicCoffeeMachine class. So, you can only brew a CoffeeSelection.FILTER_COFFEE.

```
// create a Map of available coffee beans
Map beans = new HashMap();
beans.put(CoffeeSelection.FILTER_COFFEE,
new CoffeeBean("My favorite filter coffee bean", 1000));
// instantiate a new CoffeeMachine object
BasicCoffeeMachine coffeeMachine = new BasicCoffeeMachine(beans);
Coffee coffee = coffeeMachine.brewCoffee(CoffeeSelection.FILTER_COFFEE);
```

__Subclass Referenced as the Subclass__

The second scenario is similar. But this time, I instantiate a PremiumCoffeeMachine and reference it as a PremiumCoffeeMachine. In this case, the JVM calls the brewCoffee method of the PremiumCoffeeMachineclass, which adds support for CoffeeSelection.ESPRESSO.

```
// create a Map of available coffee beans
Map beans = new HashMap();
beans.put(CoffeeSelection.FILTER_COFFEE,
new CoffeeBean("My favorite filter coffee bean", 1000));
beans.put(CoffeeSelection.ESPRESSO,
new CoffeeBean("My favorite espresso bean", 1000));
// instantiate a new CoffeeMachine object
PremiumCoffeeMachine coffeeMachine = new PremiumCoffeeMachine(beans);
Coffee coffee = coffeeMachine.brewCoffee(CoffeeSelection.ESPRESSO);
```

__Subclass Referenced as the Superclass__

This is the most interesting scenario and the main reason why I explain dynamic polymorphism in such details.

When you instantiate a PremiumCoffeeMachine object and assign it to the BasicCoffeeMachine coffeeMachine variable, it still is a PremiumCoffeeMachine object. It just looks like a BasicCoffeeMachine.

The compiler doesn’t see that in the code, and you can only use the methods provided by the BasicCoffeeMachine class. But if you call the brewCoffee method on the coffeeMachine variable, the JVM knows that it is an object of type PremiumCoffeeMachine and executes the overridden method. This is called late binding.

```
// create a Map of available coffee beans
Map beans = new HashMap();
beans.put(CoffeeSelection.FILTER_COFFEE,
new CoffeeBean("My favorite filter coffee bean", 1000));
// instantiate a new CoffeeMachine object
BasicCoffeeMachine coffeeMachine = new PremiumCoffeeMachine(beans);
Coffee coffee = coffeeMachine.brewCoffee(CoffeeSelection.ESPRESSO);
```

__Summary__

Polymorphism is one of the core concepts in OOP languages. It describes the concept that different classes can be used with the same interface. Each of these classes can provide its own implementation of the interface.

Java supports two kinds of polymorphism. You can overload a method with different sets of parameters. This is called static polymorphism because the compiler statically binds the method call to a specific method.

Within an inheritance hierarchy, a subclass can override a method of its superclass. If you instantiate the subclass, the JVM will always call the overridden method, even if you cast the subclass to its superclass. That is called dynamic polymorphism.


### __Easy ones but worth mentioning:__ 

* Explain public static void main(String args[])
* Why Java is platform independent?
* What are constructors in Java?
