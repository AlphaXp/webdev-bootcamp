---
layout: lesson
title: "Authentication and authorization"
description: ""
category: rails
tags: []
---
{% include JB/setup %}

Authentication
--------------

### Demonstration

-   Watch [Authentication from
    scratch](http://railscasts.com/episodes/250-authentication-from-scratch-revised)

### Exercise

-   Add users (login+signup and everything) to PizzaBurger

Devise (authentication gem)
---------------------------

### Demonstration

-   Watch [Introducing
    Devise](http://railscasts.com/episodes/209-introducing-devise)
-   Watch [Customizing
    Devise](http://railscasts.com/episodes/210-customizing-devise)

-   Create two types of users:

    -   Client - use the existing class (either combine Client and
        User).
    -   Employee

CanCan
------

### Demonstration

-   Watch [Authorization with
    CanCan](http://railscasts.com/episodes/192-authorization-with-cancan)

### Exercise

-   Implement the following roles:

    -   Client

        -   Can create orders and edit its own orders

    -   Employee - allowed to view all orders and add clients

        -   Can do anything