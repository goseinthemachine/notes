# Entity Framework

## Links 
- [Getting Started with Entity Framework 6 Code First using MVC 5](https://docs.microsoft.com/en-us/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application)

## 3 ways of creating model layer
- Database
- Model
- Code

## Good Practice
Separate data layer from web project. Makes it useable elsewhere.

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
