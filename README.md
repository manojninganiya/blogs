# Dot Net Full Stack Developer Interview Questions



## Table of contents
- [C# Programming](#c-programming)
- [ASP.NET & ASP.NET MVC](#aspnet--aspnet-mvc)
- [ASP.NET Core & .NET Core](#aspnet-core--net-core)
- [Web Services (REST & SOAP)](#web-services-rest--soap)
- [WCF Services](#wcf-services)
- [Entity Framework Core (EF Core)](#entity-framework-core-ef-core)
- [LINQ (Language Integrated Query)](#linq-language-integrated-query)
- [Angular (Frontend)](#angular-frontend)
- [MS SQL Server](#ms-sql-server)
- [MySQL](#mysql)

# C# Programming

## 4 Pillars of Object-Oriented Programming (OOP) in C#
Here's a quick mnemonic to remember the 4 main OOP concepts in C# in order:

**_A PIE_** (Abstraction, Polymorphism, Inheritance, Encapsulation)

---

### 1. **Abstraction**
- Hides complex implementation details
- Shows only the **essential features**
- Achieved through:
  - **Abstract classes**
  - **Interfaces**

---

### 2. **Polymorphism**
- "Many forms" – same method behaves differently
- Types:
  - **Method Overloading** (Compile-time polymorphism)
  - **Method Overriding** (Runtime polymorphism)

---

### 3. **Inheritance**
- Defines a **base class → derived class** relationship
- Promotes **code reusability**
- Based on **"is-a"** relationship

---

### 4. **Encapsulation**
- Bundles **data** and **methods** that operate on it
- Controls access using:
  - `private`, `protected`, `public` modifiers
  - **Properties** (`get`/`set`) for controlled access

---


### What's the difference between `null` and a `NullReferenceException` ?
Many people think they’re the same — but they’re not.

`null`: A **valid value** in C# that means **"no object reference."**  
It’s often used to indicate the absence of a value or an uninitialized object.

`NullReferenceException`: A runtime exception that occurs when you try to access a member (property, method, etc.) on a null reference.

```
string s = null;        // null means "s" doesn't refer to any object
Console.WriteLine(s.Length); // ❌ Throws NullReferenceException
```

Here, `s` is `null`, so trying to access `s.Length` triggers a `NullReferenceException`.

---
### Why does `string.Replace()` not modify the original string?

Many developers expect it to behave like array or list operations, which modify data in-place. But strings in C# don’t work that way.

**Strings are immutable** in C# — meaning once a string is created, its value **cannot be changed**.

Methods like `.Replace()`, `.ToUpper()`, `.Trim()`, etc., always return a **new string** and leave the original string unchanged.

```
string s1 = "Hello";
string s2 = s1.Replace("H", "J"); // Creates a new string "Jello"

Console.WriteLine(s1); // Output: Hello (original unchanged)
Console.WriteLine(s2); // Output: Jello (new string)
```
---
### Why is this code inefficient?

```
int num = 10;
object boxed = num;            // Boxing (heap allocation)
int unboxed = (int)boxed;      // Unboxing (type check + copy)
```
Boxing converts a value type to object (heap allocation).

Unboxing converts back (type check + copy).

Performance impact: Extra memory and CPU overhead.

---
### Does `await` make the calling thread wait?

Many developers think `await` blocks the thread, like synchronous code — but that's a misunderstanding.

**No, `await` does not block the calling thread.**

When an `await` is encountered, the current method:
- **Yields control** back to the calling context
- **Releases the thread** to do other work
- **Resumes** the continuation when the awaited task completes

```
async Task DoWorkAsync()
{
    await Task.Delay(1000); // Thread is released during this delay
    Console.WriteLine("Done"); // Resumes here after delay
}
```
---

# ASP.NET & ASP.NET MVC
MVC here — covering routing, controllers, views, model binding, filters, and Razor syntax for dynamic web applications.

# ASP.NET Core & .NET Core
Cross-platform framework for building modern, cloud-enabled, internet-connected applications. Learn about middleware, dependency injection, configuration, and environment setup.

# Web Services (REST & SOAP)
Details on creating and consuming RESTful and SOAP-based web services using ASP.NET Web API, HttpClient, Swagger, and WSDL.

# WCF Services
Explore Windows Communication Foundation (WCF) for service-oriented applications, including bindings, contracts, endpoints, and hosting strategies.

# Entity Framework Core (EF Core)
Learn about the modern ORM for .NET Core applications. Topics include DbContext, migrations, LINQ queries, eager/lazy loading, and database-first vs code-first approaches.

# LINQ (Language Integrated Query)
Master querying collections in C# using LINQ, including filtering, projections, joins, grouping, and deferred execution.

# Angular (Frontend)
Frontend development with Angular, covering components, services, routing, modules, and integration with APIs using HttpClient.

# MS SQL Server
Working with Microsoft SQL Server — schema design, stored procedures, triggers, indexing, views, and performance optimization.



# MySQL
Using MySQL with .NET applications. Topics include database creation, querying, relationships, foreign keys, and connection from C#.

