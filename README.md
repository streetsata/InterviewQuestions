# Interviewer's questions about C#, ASP.NET, Data Bases concept and DevOps

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
These examples demonstrate encapsulation by using private fields and properties, inheritance by creating subclasses that inherit from a base class, and polymorphism by overriding methods in subclasses and using them interchangeably with base class references.

</details>
