# Ruby on Rails Cheat Sheet

## Install ruby
Activate gem executables after installing
 
    rbenv rehash

## REST
Preferred way to generate a model with controller etc and the usually CRUD actions

    rails g resource Person name:string

## Models and migrations

Create a new model with migration and test

    rails g model BankAccount iban bic

Create an empty migration file

    rails generate migration TransactionBelongsToBankAccount

Run the migrations

    rake db:migrate

## Tests
Activate rspec for application

    rails g rspec:install

Run rspec tests

    rspec

## routes
View all routes

    rake routes


## Devise
Create users e.g. for testing 

    User.create!({:email => "guy@gmail.com", :roles => ["admin"], :password => "111111", :password_confirmation => "111111" })

see: [http://stackoverflow.com/questions/4316940/create-a-devise-user-from-ruby-console](http://stackoverflow.com/questions/4316940/create-a-devise-user-from-ruby-console) 

