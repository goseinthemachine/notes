# Entity Framework Core

## Adding DotNet EF
To work with Entity Framework Core in dotnet core one must add the tool package for dotnet ef. 

## DbContext

### Working with multiple DbContext
```csharp
//In DAL
public AppContext : DbContext<AppContext>{ //Required or migration fails
    public AppContext(DbContextOptions options)
        :base(options)
    {

    }
}

public UserContext : DbContext<UserContext>{ //Required or migration fails
    public AppContext(DbContextOptions options)
        :base(options)
    {

    }
}
```
```csharp
//startup.cs
//TODO Add startup code
//Can write to the same database or different ones.
```
#### Migrating Multiple DbContext
```bash
#Creates migration that targets AppContext and outputs to ./Migrations/AppContext
dotnet ef add migration --context AppContext -o ./Migrations/AppContext

#Creates migration that targets UserContext and outputs to ./Migrations/UserContext
dotnet ef add migration --context UserContext -o ./Migrations/UserContext
```
