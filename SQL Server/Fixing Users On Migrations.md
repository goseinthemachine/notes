# Fixing User on Migrations
1. First run this stored procedure in SQL Server Management Studio(SSMS). This command will change the users password to what is in the @Password field.
```sql
EXEC sp_change_users_login 
     @Action = 'Auto_Fix'
    ,@UserNamePattern = '<user>'
    ,@Password = '<password_that_works_with_password_policy>'
```
    > This works with server 2005 and up I believe
    
2. If applications rely on a password that doesn't comply with the password policy, then the policy check needs to be disabled.
    - In SSMS expand Security > Login on the database server the user resides.
    - Right-click the user > click properties
    - Select the General page, if not already opened, uncheck Enforce password policy
    - Enter in needed password
    - click ok


