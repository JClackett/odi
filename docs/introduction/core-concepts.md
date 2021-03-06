# Core Concepts

## **Overview**

Imagine that you have common CRUD server application. Or you can have huge server with non trivial logic. At least, you want to have clear code, that can be supported and updeted with less efforts and more fun. Next concepts can help with it: **Single Resposibility, Loosely Coupled Code, Segregation Principle** and **Substitution Principle.**

## Paradigm

**Odi** uses Object Oriented and Declarative paradigm. TypeScript provides syntactic structures for it. _Classes_, _Interfaces_, _Abstract Classes_, _Generics_ and etc. for **OOP**. And _Decorators_ for **Declarative.**

But functional programming also take a part in development.

## **Architecture**

Lets take a look on common **Odi** architecture, including database \([TypeORM](http://typeorm.io/#/) integration\):

![](../.gitbook/assets/untitled-diagram%20%281%29.png)

For responsibility, it can be divided into next layers:

* **Controller** - network layer
* **Service** - application \(logic\) layer
* **Repository** - database actions layer
* **Model** - data representation layer

There can be other components on every layer, but we are looking only on basic example.

### Controller

The main purpose of controllers is communication gateway for clients. There should be actions, that only connected with network or http responsibility. For example: sending different HTTP statuses, handling websocket events, preprocessing requests, body validation, user verification, cookies and etc.

As opposite example: Controller should not dirrectly interact database.

### Service

Business logic center. It is the place, where you should forget about HTTP statuses, cookies and etc. Only your application logic should appear here. But still no direct interaction with database. Different repositories can be combined for implementing required processes \(like transactions, calculations and etc.\).

### Repository

Definitely about database. Interact \(search, create, update and anything else\) with data in database. Custom or standard repositories can be used. One repository must reference to only one model. Associate it with database interaction only.

### Model

It's only about storing and linking data. Basic class for representation in database. Describe fields \(type, nullability, relation and etc\) for storing in database.

Opposite example: implementing business logic methods or validations.

## Environment

There is no special requirements for running applications based on Odi. It just Node.js. But there is few limitation about TypeScript configuration.

Enable the following settings in `tsconfig.json`

```javascript
 "emitDecoratorMetadata":  true, 
 "experimentalDecorators":  true
```

Those setting allows properly handle **Dependency Injection** and many other things, that connected with runtime types. Without this options enabled, the most part of core features will be disabled.

In future version there can be changes, as CLI tool will be released.

