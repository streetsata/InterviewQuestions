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

**Implementation:**
Abstract Class: Can contain both abstract and non-abstract (concrete) members. It can provide partial implementation of methods.
Interface: Contains only method signatures, properties, events, or indexers, without any implementation.
Inheritance:
Abstract Class: Supports single inheritance. A class can inherit from only one abstract class.
Interface: Supports multiple inheritance. A class can implement multiple interfaces.
Members:
Abstract Class: Can have fields, constructors, destructors, and defined methods.
Interface: Can only have method signatures, properties, events, or indexers. No fields, constructors, or destructors are allowed.
Accessibility:
Abstract Class: Can have access modifiers (public, private, protected, etc.) for its members.
Interface: All members are implicitly public and cannot have access modifiers (except for explicit interface implementations).
Usage:
Abstract Class: Used when a common base implementation is needed among derived classes or when some methods should have a default implementation.
Interface: Used when you want to enforce a contract for implementing classes without providing any default implementation.
  
</details>

<details>
<summary>Що дає ключове слово «virtual»? Які члени класу можуть бути позначені цим модифікатором?</summary>
</details>

<details>
<summary>Яка різниця між перевантаженням методу та перевизначенням методу?</summary>
</details>

<details>
<summary>Що таке upcast і downcast?</summary>
</details>

<details>
<summary>Що таке події та делегати? Яка основна різниця між ними? Як їх використовувати для реалізації зворотного виклику в C#?</summary>
</details>

### *Основні концепції C#*

## **Middle** 👱
## **Senior** 🧔
