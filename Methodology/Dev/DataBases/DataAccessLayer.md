# Data Access Layer

## Libraries Type

- Raw clients
- Full-ORM (Object-relational-mapping)
- Micro-ORM

## Raw Clients

Pros:

- High performance

Cons:

- High rate of boiler plates
- High-risk coding like connection closing that has to be take care by the programmer.

## Full-ORM

Pros:

- Encapsulating connection and executing management
- Encapsulating transforming raw data to Object-Model
- Using programming language's native collection operation(e.g C# LINQ) and translate them into the language of the DB(e.g SQL)
- Watching returned data for modifications so committing DML will be easy and native.

Cons:

- Generated Queries are not tailor-made, thus sometimes, might be not efficient

## Micro ORM

- Encapsulating connection and executing management
- Encapsulating transforming raw data to Object-Model
- Not heavy like the Full-ORM

## General Best Practices

- SqlInjection - Make sure to use the libraries Query Parameters objects that can prevent a SQL Injection attack.

(?? Research more)
