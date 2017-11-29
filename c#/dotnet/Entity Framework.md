# Entity Framework

## Links 
- [Getting Started with Entity Framework 6 Code First using MVC 5](https://docs.microsoft.com/en-us/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application)

## 3 ways of creating model layer
- Database
- Model
- Code

## Good Practice
Separate data layer from web project. Makes it useable elsewhere.

## Models

### Creating a model
```csharp
//Example of multiple models. With data annotations
```
### Data Annotations
```csharp
//Place to hold different data annotations and what they do
```
><bold>IMPORTANT:</bold> Foreign Key relationships will be set to delete on cascade when a migration is processed. Make sure that is the option you want.

## Migrations
- Create, seed, and apply schema changes
- Now supports multiple DbContexts in a project (EF 6)
    - ContextTypeName
    - MigrationsTypes

### Enable Migrations
<code>enable-migrations -ContextTypeName IdentityDb -MigrationsDirectory DataContex\IdentityMigrations</code>

### Adding a Migration
<code>add-migration InitialCreate</code>

### Adding a Migration for Multiple Migrations
<code>add-migration -ConfigurationTypeName Books.Web.DataContexts.IdentityMigrations.Configuration "InitialCreate"</code>
> Points to the configuration.cs file that is located in the Migration folder generated fomr enable-migrations

This creates a migration file using the fluent api to map out the tables, keys, indexes and so on.

If the schema changes before commiting the migration you can re-scaffold the migration by running <code>add-migration InitialCreate</code> again.
If using multiple dbContexts make sure to user -ConfingurationTypeName

### Committing Changes to the Database
<code>update-database -ConfigurationTypeName Books.Web.DataContexts.IdentityMigrations.Configuration</code>

### Reversing Migrations
It is possible to reverse a migration with the following commands
```powershell
#Removes all database changes up to this migration
update-database -TargetMigration <MigrationName> 

#Removes all database changes. Essentially a clean database.
update-database -TargeMigration 0 
```



### Fluent API
TODO
- Discuss