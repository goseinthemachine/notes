# Repository Pattern
- Separate business code from data access
- Makes code more testable

## Intent
Encapsulate data access
- Data appears to live inside an in-memory collection

## Example
```csharp
namespace EmployeeData
{
    public interface IEmployeeRepository
    {
        void Add(Employee newEmployee);
        void Remove(Employee employee);
        // void Update(employee); //For WCF this is uncommon 
        // Use unit of work pattern for update.
        IEnumerable<Employee> Find(Expressions<Func<Employee, bool>> predicate);
        // or 
        IQueryable<Employee> Find(Expressions<Func<Employee, bool>> predicate);
        

        // public void DoWork(IEmployeeRepository repository){
        //     repository.Add(new Employee());
        //     repository.Remove(employee);

        //     var managers = repository.GetAllManagers();
        //     var otherManagers = repository.Find(e => e.IsManager == true);
        // }
    }
}
```

## Example Generic Interface Repository
```csharp
public interface IRepository<T>
{
    void Add(T newEntity);
    void Remove(T entity);
    IQueryable<T> Find(Expression<Func<T, bool>> predicate);
}

public interface IEmployeeRepository : IRepository<Employee> 
{

}
```

## Applicability
- Antime you need data persistence
 SQL Database
    - Web Service
    - File System

## Consequences
- Increased level of abstraction
    - More classes, less duplicated code
    - Maintainability, flexibility, testability
- Further away from data
    - Shielded from infrastructure    
    - Harder to optimize

## Other Patterns
List of other patterns that integrate with Repository Pattern
- Unit of Work
- Specification
- Identity Map
- Decorator

## Links
Found the following links that cover this topic 
- [RESTful Day #1: Enterprise Level Application Architecture with Web APIs using Entity Framework, Generic Repository Pattern and Unit of Work](https://www.codeproject.com/Articles/990492/RESTful-Day-sharp-Enterprise-Level-Application)
