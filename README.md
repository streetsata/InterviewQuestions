# Interviewer's questions about C#, ASP.NET, Data Bases concept and DevOps

| Term  | Description |
| ------------- | ------------- |
| None | Has no or little understanding
| Basic | Has an idea of the subject and its parts. Can explain. Has experience of use
| Good | Can name examples of use in different contexts. Is guided by best-practices and specifications.
| Advanced | Systematically applies best-practices, design patterns and tool specifications for solving complex issues
| Outstanding | Takes into account technology limitations and its weaknesses. Successfully solves non-standard tasks. Master of debugging, optimization and style.

## **Trainee/Junior** 👼

### *OOP concepts*

<details>
<summary>What are the basic principles of OOP? How are they implemented in C#?</summary> 
<br>
  
<ul>
  <li>Encapsulation: Bundling data and methods that operate on the data into a single unit (class).</li>
  <li>Inheritance: Allowing a class (subclass) to inherit properties and methods from another class (superclass).</li>
  <li>Polymorphism: Objects of different classes can be treated as objects of a common superclass.</li>
</ul>
In C#, these principles are implemented as follows: 
  
| Title  | Description |
| ------------- | ------------- |
| Encapsulation  | In C#, encapsulation is achieved through access modifiers (public, private, protected) to control the access to class members. Properties and methods can be used to manipulate the internal state of objects, while hiding the implementation details.  |
| Inheritance  | C# supports single inheritance, where a class can inherit from only one base class, but it also supports multiple interface inheritance. This allows classes to inherit behavior from a superclass or implement multiple interfaces. |
| Polymorphism | C# supports polymorphism through method overriding and method overloading. Method overriding allows a subclass to provide a specific implementation of a method that is already defined in its superclass. Method overloading allows multiple methods with the same name but different parameters in the same class or different classes.

<h3>Code Examples</h3>
<h4>Encapsulation:</h4>

```cs
using System;

public class Person
{
    private string name;
    private int age;

    // Constructor
    public Person(string name, int age)
    {
        this.name = name;
        this.age = age;
    }

    // Properties
    public string Name
    {
        get { return name; }
        set { name = value; }
    }

    public int Age
    {
        get { return age; }
        set { age = value; }
    }

    // Method
    public void DisplayInfo()
    {
        Console.WriteLine($"Name: {name}, Age: {age}");
    }
}

class Program
{
    static void Main(string[] args)
    {
        Person person = new Person("John", 30);
        person.DisplayInfo(); // Accessing method
        person.Age = 35; // Accessing property
        person.DisplayInfo();
    }
}
```
<h4>Inheritance:</h4>

```cs
using System;

public class Animal
{
    public void Eat()
    {
        Console.WriteLine("Animal is eating.");
    }
}

public class Dog : Animal
{
    public void Bark()
    {
        Console.WriteLine("Dog is barking.");
    }
}

class Program
{
    static void Main(string[] args)
    {
        Dog dog = new Dog();
        dog.Eat(); // Inherited method
        dog.Bark(); // Method of the subclass
    }
}

```

<h4>Polymorphism:</h4>

```cs
using System;

public class Animal
{
    public virtual void MakeSound()
    {
        Console.WriteLine("Animal makes a sound.");
    }
}

public class Dog : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Dog barks.");
    }
}

public class Cat : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Cat meows.");
    }
}

class Program
{
    static void Main(string[] args)
    {
        Animal[] animals = new Animal[2];
        animals[0] = new Dog();
        animals[1] = new Cat();

        foreach (Animal animal in animals)
        {
            animal.MakeSound(); // Polymorphic method call
        }
    }
}

```
<p>These examples demonstrate encapsulation by using private fields and properties, inheritance by creating subclasses that inherit from a base class, and polymorphism by overriding methods in subclasses and using them interchangeably with base class references.</p>

</details>

<details>
<summary>What is an abstract class? And how is it different from a regular class?</summary>
  <p>An abstract class in C# is a class that cannot be instantiated directly. It's designed to be a blueprint for other classes, serving as a base for other classes to inherit from. Abstract classes may contain abstract methods, which are methods without a body, meant to be implemented by derived classes.</p>
  <p>Here's how an abstract class is different from a regular class:</p>
  
  | Term  | Different from a regular class |
  | ------------- | ------------- |
  | Instantiation | Abstract classes cannot be instantiated directly, meaning you cannot create objects of an abstract class. Regular classes can be instantiated, allowing you to create objects directly. 
  | Abstract Methods | Abstract classes can have abstract methods, which are methods without implementation. These methods must be implemented by any non-abstract subclass. Regular classes may or may not have abstract methods, but if they do, they must be marked as abstract and the class itself must be marked as abstract. 
  | Inheritance | Abstract classes are used as base classes from which other classes can inherit. Regular classes can also be used as base classes, but they can also be instantiated directly without needing to be inherited.


<h4>Here's an example illustrating the differences:</h4>

```cs
using System;

// Abstract class
public abstract class Shape
{
    // Abstract method
    public abstract double Area();
}

// Regular class inheriting from the abstract class
public class Rectangle : Shape
{
    public double Width { get; set; }
    public double Height { get; set; }

    // Implementation of the abstract method
    public override double Area()
    {
        return Width * Height;
    }
}

class Program
{
    static void Main(string[] args)
    {
        // Abstract class cannot be instantiated directly
        // Shape shape = new Shape(); // This will cause an error

        // Regular class can be instantiated
        Rectangle rectangle = new Rectangle();
        rectangle.Width = 5;
        rectangle.Height = 3;
        Console.WriteLine($"Area of rectangle: {rectangle.Area()}"); // Output: 15
    }
}

```

<h4>In this example, Shape is an abstract class that contains an abstract method Area(). The Rectangle class inherits from Shape and implements the Area() method. You cannot create an instance of Shape directly, but you can create instances of Rectangle.</h4>
</details>

<details>
<summary>What is an interface and what are its key differences from an abstract class?</summary>
  <p>
  An interface in C# is a reference type that defines a contract for other classes to implement. It contains only method signatures, properties, events, or indexers, without providing any implementation. Any class that implements an interface must provide concrete implementations for all members declared in that interface.</p>
<p>
  Here are the key differences between an interface and an abstract class:
</p>

| Term  | Different |
| ------------- | ------------- |
| **Implementation** | **Abstract Class**: Can contain both abstract and non-abstract (concrete) members. It can provide partial implementation of methods. <br> **Interface**: Contains only method signatures, properties, events, or indexers, without any implementation.
| **Inheritance** | **Abstract Class:** Supports single inheritance. A class can inherit from only one abstract class. <br> **Interface:** Supports multiple inheritance. A class can implement multiple interfaces.
| **Members** | **Abstract Class:** Can have fields, constructors, destructors, and defined methods. **Interface:** Can only have method signatures, properties, events, or indexers. No fields, constructors, or destructors are allowed.
| **Accessibility** | **Abstract Class:** Can have access modifiers (public, private, protected, etc.) for its members. <br> **Interface:** All members are implicitly public and cannot have access modifiers (except for explicit interface implementations).
| **Usage** | **Abstract Class:** Used when a common base implementation is needed among derived classes or when some methods should have a default implementation. <br> **Interface:** Used when you want to enforce a contract for implementing classes without providing any default implementation.

<p>Here's an example illustrating these differences:</p>

```cs
using System;

// Abstract class
public abstract class Animal
{
    // Abstract method
    public abstract void MakeSound();

    // Concrete method
    public void Eat()
    {
        Console.WriteLine("Animal is eating.");
    }
}

// Interface
public interface IJumpable
{
    // Method signature
    void Jump();
}

// Concrete class implementing an interface
public class Dog : Animal, IJumpable
{
    // Implementation of abstract method from abstract class
    public override void MakeSound()
    {
        Console.WriteLine("Dog barks.");
    }

    // Implementation of interface method
    public void Jump()
    {
        Console.WriteLine("Dog jumps.");
    }
}

class Program
{
    static void Main(string[] args)
    {
        // Abstract class can't be instantiated
        // Animal animal = new Animal(); // This will cause an error

        // Abstract class instance
        Dog dog = new Dog();
        dog.MakeSound(); // Output: Dog barks.
        dog.Eat(); // Output: Animal is eating.

        // Interface instance
        dog.Jump(); // Output: Dog jumps.
    }
}

```
<p>In this example, Animal is an abstract class containing both abstract and concrete members, while IJumpable is an interface containing only method signatures. Dog class inherits from the abstract class Animal and implements the interface IJumpable.</p>

</details>

<details>
<summary>What does the keyword "virtual" provide? Which class members can be marked with this modifier?</summary>
<p>The virtual keyword in C# is used to define a method, property, or indexer in a base class that can be overridden in derived classes. It allows derived classes to provide a specific implementation for that member, effectively enabling polymorphic behavior.</p>

<p>Here's what virtual provides:</p>

| Term  | Description |
| ------------- | ------------- |
| Method Overriding | It allows a method in a base class to be overridden by a method with the same signature in a derived class.
| Polymorphism | It enables polymorphic behavior, meaning that the appropriate method implementation is called based on the actual type of the object at runtime.

<p>The class members that can be marked with the virtual modifier are:</p>

* Methods
* Properties (get and/or set accessors)
* Indexers (get and/or set accessors)

<p>Fields cannot be marked as virtual.</p>

<p>Here's an example demonstrating the use of the virtual keyword with methods:</p>

```cs
using System;

public class Animal
{
    // Virtual method
    public virtual void MakeSound()
    {
        Console.WriteLine("Animal makes a sound.");
    }
}

public class Dog : Animal
{
    // Override the virtual method
    public override void MakeSound()
    {
        Console.WriteLine("Dog barks.");
    }
}

public class Cat : Animal
{
    // Override the virtual method
    public override void MakeSound()
    {
        Console.WriteLine("Cat meows.");
    }
}

class Program
{
    static void Main(string[] args)
    {
        Animal animal1 = new Dog();
        Animal animal2 = new Cat();

        animal1.MakeSound(); // Output: Dog barks.
        animal2.MakeSound(); // Output: Cat meows.
    }
}
```
<p>In this example, the MakeSound() method in the Animal class is marked as virtual, allowing derived classes Dog and Cat to override it with their own implementations. The actual method called depends on the type of object at runtime, demonstrating polymorphism.</p>

</details>

<details>
<summary>What is the difference between method overloading and method overriding?</summary>

Method overloading and method overriding are both mechanisms used in object-oriented programming, but they serve different purposes and are used in different contexts.

**Method Overloading:**

Method overloading involves defining multiple methods with the same name but with different parameters within the same class. These methods can have different parameter types, different numbers of parameters, or a different order of parameters. The compiler differentiates between these methods based on their method signatures.

Here's an example of method overloading:

```cs
public class Calculator
{
    public int Add(int a, int b)
    {
        return a + b;
    }

    public double Add(double a, double b)
    {
        return a + b;
    }

    public int Add(int a, int b, int c)
    {
        return a + b + c;
    }
}

```
n this example, the `Add` method is overloaded three times with different parameter types and numbers.

**Method Overriding:**

Method overriding, on the other hand, occurs when a method in a subclass has the same name, return type, and parameters as a method in its superclass. The purpose of method overriding is to provide a specific implementation of a method in a subclass that overrides the implementation in the superclass. It is used in inheritance to achieve polymorphic behavior.

Here's an example of method overriding:

```cs
public class Animal
{
    public virtual void MakeSound()
    {
        Console.WriteLine("Animal makes a sound.");
    }
}

public class Dog : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Dog barks.");
    }
}

public class Cat : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Cat meows.");
    }
}

```

In this example, both `Dog` and `Cat` classes override the `MakeSound` method defined in the `Animal` class.

**Key Differences:**

1.  **Purpose**:
    
    -   Method Overloading: Provides multiple methods with the same name but different signatures within the same class for convenience and flexibility.
    -   Method Overriding: Provides a way for a subclass to provide a specific implementation of a method defined in its superclass.
2.  **Inheritance**:
    
    -   Method Overloading: Not related to inheritance. Methods are defined within the same class.
    -   Method Overriding: Specifically used in inheritance. The overridden method belongs to a superclass, and the overriding method belongs to a subclass.
3.  **Usage**:
    
    -   Method Overloading: Used to create methods that perform similar tasks but operate on different types or numbers of parameters.
    -   Method Overriding: Used to customize or extend the behavior of inherited methods in subclasse

</details>

<details>
<summary>What are upcast and downcast?</summary>

**Upcasting:**

Upcasting is the process of casting a reference of a derived class to one of its base classes. It's essentially moving up the inheritance hierarchy. When you upcast, you are treating an object of a derived class as an object of its base class.

Here's an example:
```cs
class Animal { }
class Dog : Animal { }

class Program
{
    static void Main(string[] args)
    {
        Dog myDog = new Dog();
        Animal animal = myDog; // Upcasting
        
        // Now 'animal' is treated as an Animal, even though it's actually a Dog
    }
}

```

In this example, `myDog` is a `Dog` object, but it's assigned to a variable of type `Animal`. This is upcasting because `Dog` inherits from `Animal`, so it's implicitly treated as an `Animal`.

**Downcasting:**

Downcasting is the opposite process, where you cast a reference of a base class to one of its derived classes. It's moving down the inheritance hierarchy. Downcasting requires explicit casting and might throw an exception at runtime if the object being cast isn't actually an instance of the derived class.

Here's an example:

```cs
class Animal { }
class Dog : Animal { }

class Program
{
    static void Main(string[] args)
    {
        Animal animal = new Dog();
        Dog myDog = (Dog)animal; // Downcasting
        
        // Now 'myDog' is treated as a Dog
    }
}
```

In this example, `animal` is an `Animal` object, but it's actually referencing a `Dog` object. We explicitly cast `animal` to `Dog`, indicating that we're treating it as a `Dog`.

It's important to note that downcasting can fail at runtime if the object being cast isn't actually an instance of the derived class. To avoid exceptions, you can use the `as` keyword:

```cs
Dog myDog = animal as Dog;
if (myDog != null)
{
    // Downcasting successful
}
else
{
    // Downcasting failed
}

```

This way, if `animal` isn't a `Dog`, `myDog` will be `null` rather than throwing an exception.

</details>

<details>
<summary>What are events and delegates? What is the main difference between them? How can they be used to implement callbacks in C#?</summary>

**Events and Delegates in C#**

**Delegates:**

Delegates in C# are similar to function pointers in C or C++. They are reference types that hold references to methods with a specific signature. Delegates allow methods to be passed as parameters, stored in collections, and invoked dynamically.

Here's how a delegate is declared:

```cs
public delegate void MyDelegate(string message);
```

Delegates are especially useful for implementing callbacks because they allow you to define a contract for a method without needing to know the concrete implementation.

**Events:**

Events provide a way for objects to notify other objects when something of interest happens. They are based on the observer design pattern. An event is a special type of delegate that can only be invoked from within the class that declares it.

Here's how an event is declared:

```cs
public class Publisher
{
    public event MyDelegate SomeEvent;
    
    public void RaiseEvent(string message)
    {
        SomeEvent?.Invoke(message);
    }
}
```

**Difference between Events and Delegates:**

The main difference between events and delegates is that events encapsulate delegates. While you can assign a delegate directly, you can't directly invoke an event outside the class where it's declared. Events provide more control over how delegates are used and who can invoke them.

**Using Delegates and Events to Implement Callbacks:**

Callbacks in C# can be implemented using delegates and events. Here's a simple example:

```cs
using System;

public delegate void MyCallback(string message);

public class Publisher
{
    public event MyCallback SomeEvent;

    public void RaiseEvent(string message)
    {
        SomeEvent?.Invoke(message);
    }
}

public class Subscriber
{
    public void OnEventCallback(string message)
    {
        Console.WriteLine($"Subscriber received message: {message}");
    }
}

class Program
{
    static void Main(string[] args)
    {
        Publisher publisher = new Publisher();
        Subscriber subscriber = new Subscriber();

        // Subscribe to the event
        publisher.SomeEvent += subscriber.OnEventCallback;

        // Raise the event
        publisher.RaiseEvent("Hello from publisher!");
    }
}
```
In this example, `Publisher` declares an event `SomeEvent` of type `MyCallback`, and `Subscriber` defines a method `OnEventCallback` that matches the signature of `MyCallback`. When `SomeEvent` is raised, the `OnEventCallback` method of `Subscriber` is invoked. This allows for the implementation of a callback mechanism.

</details>

### *Basic C# Concepts*

<details>
<summary>What is the difference between an array (T[]) and a list (List<T>)? What are collections and how are they used?</summary>


**Difference between Array (T[]) and List (List<T>)**

**Array (T[])**:

-   Arrays in C# are fixed-size collections of elements of the same type.
-   Once created, the size of an array cannot be changed.
-   Arrays offer direct access to elements using indexers.
-   They are more memory efficient than lists because they don't need extra memory to store their elements.
-   Arrays are less flexible than lists, especially in terms of resizing and manipulation.

**List<T>**:

-   Lists in C# are dynamic-size collections of elements of the same type.
-   Lists automatically resize themselves as needed when elements are added or removed.
-   Lists provide methods to manipulate their elements, such as adding, removing, inserting, and sorting.
-   They offer more flexibility and functionality compared to arrays.
-   Lists are implemented as a wrapper around an array and use additional memory to store their elements.

**Collections and How They Are Used**

In C#, collections are objects that can hold multiple elements. They are used to store, organize, and manipulate data efficiently. Collections provide various data structures, each designed for specific purposes and requirements.

Here are some commonly used collection types in C#:

1.  **List<T>**: Dynamic-size list that provides methods for adding, removing, and accessing elements.
    
2.  **Dictionary<TKey, TValue>**: Key-value pair collection that provides fast lookup by key.
    
3.  **Queue<T>**: First-in-first-out (FIFO) collection used for storing and retrieving elements in the order they were added.
    
4.  **Stack<T>**: Last-in-first-out (LIFO) collection used for storing and retrieving elements in the reverse order of their addition.
    
5.  **HashSet<T>**: Unordered collection of unique elements with no duplicates.
    
6.  **LinkedList<T>**: Doubly linked list collection that allows efficient insertion and removal of elements at any position.
    

Collections are used in various scenarios:

-   Storing and managing data in memory.
-   Implementing algorithms and data structures.
-   Passing data between methods or components.
-   Working with collections of objects obtained from databases or external sources.
-   Manipulating data in LINQ queries.

Here's an example of using a list to store and manipulate data:

```cs
using System;
using System.Collections.Generic;

class Program
{
    static void Main(string[] args)
    {
        // Creating a list of integers
        List<int> numbers = new List<int>();

        // Adding elements to the list
        numbers.Add(10);
        numbers.Add(20);
        numbers.Add(30);

        // Accessing elements by index
        Console.WriteLine("First element: " + numbers[0]);

        // Iterating through the list
        Console.WriteLine("All elements:");
        foreach (int number in numbers)
        {
            Console.WriteLine(number);
        }

        // Removing an element
        numbers.Remove(20);

        // Checking if an element exists
        if (numbers.Contains(20))
        {
            Console.WriteLine("20 is still in the list.");
        }
        else
        {
            Console.WriteLine("20 is not in the list anymore.");
        }
    }
}

```

In this example, we create a list of integers, add elements to it, access elements by index, iterate through the list, remove an element, and check if an element exists in the list. Lists provide flexibility and ease of use for managing collections of data.

</details>

<details>
<summary>What is a hash table? What is a hash function? How are collisions handled in dictionaries?</summary>


**Hash Table:**

A hash table is a data structure that stores key-value pairs. It uses a hash function to compute an index into an array of buckets or slots, from which the desired value can be found. The key advantage of a hash table is its ability to perform lookups, insertions, and deletions in constant time on average, making it highly efficient for large datasets.

**Hash Function:**

A hash function is a mathematical function that takes an input (or "key") and produces a fixed-size string of characters, typically a hash code or hash value. The output of a hash function is used to index into a hash table or hash map.

A good hash function should have the following properties:

1.  **Deterministic**: For a given input, the hash function should always produce the same hash value.
    
2.  **Efficient**: The hash function should be computationally efficient.
    
3.  **Uniform Distribution**: The hash function should distribute the keys uniformly across the available hash table buckets to minimize collisions.
    
4.  **Minimal Collisions**: Collisions should be minimized, but they are practically unavoidable due to the pigeonhole principle.
    

**Handling Collisions in Dictionaries:**

Collisions occur when two different keys produce the same hash value, which results in them being mapped to the same bucket in the hash table. There are several common techniques to handle collisions:

1.  **Separate Chaining**:
    
    -   Each bucket in the hash table contains a linked list or other data structure (e.g., an array) to store multiple key-value pairs that hash to the same index.
    -   When a collision occurs, the new key-value pair is added to the linked list at the corresponding bucket.
2.  **Open Addressing**:
    
    -   In open addressing, collisions are resolved by finding an alternative location within the hash table.
    -   Common open addressing strategies include linear probing (check the next bucket), quadratic probing (check buckets with quadratic increments), and double hashing (use a secondary hash function to calculate the next bucket).
3.  **Robin Hood Hashing**:
    
    -   This is a variation of open addressing where items are stored based on how far they are from their "natural" position.
    -   When inserting a new item, if the bucket is already occupied, it checks how far the existing item has traveled from its natural position. If the new item has traveled less, it swaps places with the existing item.
4.  **Cuckoo Hashing**:
    
    -   In cuckoo hashing, each key is stored in one of two hash tables. When a collision occurs in one table, the key is moved to the other table.
    -   If there's a cycle or the other table is full, the tables are resized and rehashed.

Each collision resolution strategy has its advantages and disadvantages, and the choice depends on factors such as the expected number of collisions, memory requirements, and performance considerations.

</details>

<details>
<summary>What is Boxing and Unboxing?</summary>

**Boxing and Unboxing in C#**

**Boxing:**

Boxing is the process of converting a value type (e.g., int, double, struct) to an object reference type (e.g., System.Object). When you box a value type, the CLR allocates memory on the heap to store the value type's value, wraps it within an object, and returns a reference to that object.

Here's an example of boxing:

```cs
int i = 42; // Value type
object obj = i; // Boxing: int is boxed into an object
```

In this example, the value `42` is boxed into an object `obj`. Now, `obj` holds a reference to the boxed value on the heap.

**Unboxing:**

Unboxing is the opposite process of boxing. It involves converting an object reference type back to a value type. Unboxing extracts the value type from the boxed object.

Here's an example of unboxing:

```cs
object obj = 42; // Boxed int
int i = (int)obj; // Unboxing: Object is unboxed to int
```


In this example, the boxed value `42` is unboxed from the object `obj` and assigned to the variable `i`.

**Performance Considerations:**

Boxing and unboxing involve copying values between the stack and the heap, which can have performance implications, especially in performance-sensitive scenarios. Boxing creates additional memory allocations and introduces overhead, while unboxing involves type checking and casting.

**Avoiding Boxing and Unboxing:**

To avoid unnecessary boxing and unboxing, use generics and value types wherever possible. For example, instead of using `ArrayList` (which stores objects and leads to boxing), use `List<T>` with a specific type.

```cs
// Avoid boxing:
ArrayList list = new ArrayList();
list.Add(42); // Boxing occurs

// Use generics to avoid boxing:
List<int> list = new List<int>();
list.Add(42); // No boxing occurs
```

Generics provide type safety and eliminate the need for boxing and unboxing in many cases, resulting in improved performance and reduced memory overhead.

</details>

<details>
<summary>Які особливості використання запису (record) і запису-структури (record struct)?</summary>
</details>

<details>
<summary>Що дає ключове слово «static»? Яка особливість статичних класів?</summary>
</details>

<details>
<summary>Що дає ключове слово «sealed»?</summary>
</details>

<details>
<summary>Яка різниця між типами значень і типами посилань? Коли який тип доцільно використовувати? Наведіть приклади неправильного використання типу посилання.</summary>
</details>

<details>
<summary>У чому різниця між структурами та класами в C#?</summary>
</details>

<details>
<summary>У чому різниця між стеком і купою (heap)?</summary>
</details>

<details>
<summary>Що таке приведення типів? Яка різниця між явним і неявним приведенням типів?</summary>
</details>

<details>
<summary>Як реалізувати патерн Singleton в C# та які його переваги й недоліки?</summary>
</details>

<details>
<summary>Що таке LINQ-запити?</summary>
</details>

<details>
<summary>Поясніть різницю між методами LINQ First vs FirstOrDefault vs Single vs SingleOrDefault.</summary>
</details>

### *Обробка винятків та управління помилками*
### *Структура коду та синтаксис*
### *Принципи та шаблони проєктування програмного забезпечення*
### *Тестування*
### *Інше*

## **Middle** 👱
## **Senior** 🧔
