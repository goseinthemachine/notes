# Interfaces, Abstract Classes, and Concrete Classes

## Interface
An interface is a public contract that contains plans for implementation. When a class inherits an interface it must implement the properties, functions, ... defined in the interface it implements.

The public set of members that an interface can define are
 - Properties
 - Methods
 - Events
 - Indexers

```csharp
//Example
public interface IPolygon {
    public double CalculateArea();
}

public class Polygon {
    public int NumberOfSides {get; set;}
    public double SideLength {get; set;}

    public Polygon(int sides, int length) {
        NumberOfSides = sides;
        SideLength = length;
    }

    public int CalculatePerimeter(){
        return NumberOfSides * SideLength
    }
}


public class Triangle : Polygon, IPolygon {  

    public Triangle (int length)
    :base(3, length)
    {        
    }

    public double CalculateArea(){
        return Math.sqrt(2)(SideLength*SideLength/4); //Something like that for equilateral triangle
    }
}

public class 

```

### Benefits
- Future Proofs Code
- Interface Implementation Errors found at Compile Time

#Using Interfaces to Future-Proof Code
Why use interfaces
- Maintainability

Best Practices
- Program to an interface rather than a concrete class

## Concrete Classes
Collections
- List<T>
- Array
- Queue
- Stack
- ...

Collection Interfaces
- IList
- ICollection
- IReadOnlyList
- IEnumerator 
    - foreach
    - listbox(WPF)


```csharp
```
```csharp
public class PeopleRepository
{
    public Person [] GetPeople(){}
    public Person GetPerson(string lastName) {}
    public void AddPerson(Person newPerson){}
    // Rest of CRUD methods
}
```

