---
layout: lesson
title: "Active Record"
description: ""
category: database
tags: []
---
{% include JB/setup %}

Part 4 - Active Record
======================



Basics
------

### Demonstration

-   Database generation script

    -   Connect to database
    -   Create a migration
    -   Run migrations

-   Connect to database

    -   create a model
    -   add item
    -   remove item

-   Basic validations
-   Associations:

    -   has\_one / belongs\_to
    -   has\_many
    -   has\_many, :dependent =\> :destroy

-   Important notes:

    -   If you want to modify/create a table and then modify/create
        objects you must run `{Model}.reset_column_information` (from
        [stack
        overflow](http://stackoverflow.com/questions/8935350/rails-3-1-cant-write-to-column-in-same-migration-that-adds-it)).

    -   don't use attr\_accessor for model attributes (it will override
        active record's default implementation).

    -   beware of *mass assignment*: (quote from comment by steve3210)

        > This isn't actually a hole in rails.. If you use mass
        > assignment, you need to protect attributes you don't want
        > assigned with attr\_protected on your model.
        >
        > If you don't want people to do this:
        >
{% highlight ruby linenos%}
@user.update_attributes({ :favorite_color => 'blue', 
                          :password => 'hacked'})

        >
        > You need to do this:
        >
{% endhighlight%}
class User < ActiveRecord::Base
  attr_protected :password
end


-   [ActiveRecord demonstration
    code](https://github.com/elentok/ror-bootcamp/tree/gh-pages/exercises/active_record).

### Exercise

-   Create a file called \~/.pryrc and put these lines in the file:

{% highlight ruby linenos%}
require 'logger'
require 'active_record'
ActiveRecord::Base.logger = Logger.new(STDOUT)
{% endhighlight %}

    This will show you the SQL code of every query.

-   Read chapters 1-2 of [Association
    Basics](http://guides.rubyonrails.org/association_basics.html)

-   Modify PizzaBurger to store the orders to an SQLite database using
    ActiveRecord.

Validations
-----------

### Demonstration

-   custom validations (using :validate)
-   callbacks (before\_save, before\_validation)
-   Setting a variable during the before\_validation callback: Use
    `self` when accessing the attribute. (see [trying to set a variable
    in before\_validation but it isn't
    working](http://stackoverflow.com/questions/6065860/trying-to-set-a-variable-in-before-validation-but-it-isnt-working)).

### Exercise

-   Read chapters 1-4 of
    [Validations](http://guides.rubyonrails.org/active_record_validations_callbacks.html)

-   Add validations to the PizzaBurger models

### Extra Reading

-   Read the rest of
    [Validations](http://guides.rubyonrails.org/active_record_validations_callbacks.html)

Inheritance
-----------

### Demonstration

-   Single Table Inheritance
-   Multi-Table (sort-of)Inheritance

    -   Using composition
    -   Using polymorphic associations

### Exercise 1

-   Read the rest of [Association
    Basics](http://guides.rubyonrails.org/association_basics.html)

-   Use single table inheritance to implement `PizzaOrder` and
    `BurgerOrder`.

### Exercise 2

-   Now use polymorphic associations

What goes in Active Records
---------------------------

-   Watch [What goes in Active
    Records](https://www.destroyallsoftware.com/screencasts/catalog/what-goes-in-active-records)
-   Watch [What goes in Active Records Part
    2](https://www.destroyallsoftware.com/screencasts/catalog/what-goes-in-active-records-part-2)

