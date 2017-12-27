# Getting Started
Creating a new application
<code>rails new [app name]</code>
This command produces the following structure
```bash
app  config     db       Gemfile.lock  log           public    README.md  tmp
bin  config.ru  Gemfile  lib           package.json  Rakefile  test       vendor
```

To start your newly created application run the following
> <code>rails s</code>

This starts the application which can be accessed at **localhost:3000**.

Rails comes with some helpful generators to quickly create components for your applications.

to generate a controller you can use the following command
```bash
rails generate controller Welcome index
#The following is the console output
create  app/controllers/welcome_controller.rb
 route  get 'welcome/index'
invoke  erb
create    app/views/welcome
create    app/views/welcome/index.html.erb
invoke  test_unit
create    test/controllers/welcome_controller_test.rb
invoke  helper
create    app/helpers/welcome_helper.rb
invoke    test_unit
invoke  assets
invoke    coffee
create      app/assets/javascripts/welcome.coffee
invoke    scss
create      app/assets/stylesheets/welcome.scss
```
This command does the following
- **app/controllers/welcome_controller.rb** file is created
- A route is added to **config/routes.rb**
- A view file is created at **app/views/welcome/index.erb.html
- A style sheet in **app/assets/stylesheets/welcome.scss**

The changes look like the following
```ruby
#The New controller that inherits from ApplicationController
class WelcomeController < ApplicationController
  def index
  end
end

#The change  made to route.rb
Rails.application.routes.draw do
  get 'welcome/index'
end

```

To set the home page of the application you can set the **root** property

```ruby 
Rails.application.routes.draw do
  get 'welcome/index'
  root 'welcome#index' #without the # rails will complain with the following error
  #Missing :controller key on routes definition, please check your routes.
end
```

To create all the basic REST routes you can use **resource**
```ruby
Rails.application.routes.draw do
  get 'welcome/index'
  resource :articles #A symbol is used to define a resource
  root 'welcome#index' 
end
```
