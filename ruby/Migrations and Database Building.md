# Migrations
I was working with rails last night (1/22/18) and have come to a realization. Ruby on Rails idea of convention of configuration is a simple but powerfult idea. When I was creating the database and following how to do migrations to create models I felt like I was being rewarded for following the conventions of rails. It seemed so easy to create migrations and make changes to the database.

For example
```bash
rails g migration CreateAssets name:string asset_type:string
```
This example creates a migration file that has the code to create a table called Assets with properties id, name, and asset_type. 

```ruby

    create_table :assets do |t|
      t.string :name
      t.string :asset_type
    end
```

Id is automatically added unless you specifically state that you do not want id. If you do this you can create your own primary key, but you need to acknowledge this in the model object by using <code>self.primary = :serial</code>
```ruby
    create_table :assets, :id => false do |t|
        t.string :name
        t.string :asset_type
        t.string :serial, primary: true
```
