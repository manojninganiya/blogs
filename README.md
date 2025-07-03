<!-- # Dot Net Full Stack Developer Interview Questions -->

> By [Manoj Kumar](https://in.linkedin.com/in/mansun7)

**🚀** Innovative Tech Lead | Fintech Architect | Cloud & Microservices Expert | .NET & Azure Specialist | .NET Core | Web API | SQL Server | Scalable Architecture

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
We are working on various aspects of C# including object-oriented principles, data types, collections, exception handling, async programming, and more.
## 🆚 Difference Between `String` and `StringBuilder`

| Feature                 | `String`                                           | `StringBuilder`                                    |
|-------------------------|----------------------------------------------------|----------------------------------------------------|
| **Namespace**           | `System`                                           | `System.Text`                                      |
| **Mutability**          | Immutable – every modification creates a new string | Mutable – changes the same object in memory        |
| **Performance (Concat)**| Slower for repeated modifications (e.g., in loops) | Faster for multiple string operations              |
| **Memory Usage**        | Higher (due to new string instances)               | Lower (reuses same memory buffer)                  |
| **Thread Safety**       | Thread-safe (immutable by nature)                  | Not thread-safe by default                         |
| **Use Case**            | Best for a small number of changes                 | Best for frequent or large string manipulations    |
| **Common Methods**      | `Replace()`, `Substring()`, `ToUpper()`            | `Append()`, `Insert()`, `Replace()`, `Remove()`    |
| **Declaration Example** | `string s = "Hello";`                              | `StringBuilder sb = new StringBuilder("Hello");`   |

---

### 🔤 Code Example: `String`
```csharp
string message = "Hello";
message += " World"; // Creates a new string in memory
Console.WriteLine(message); // Output: Hello World


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

