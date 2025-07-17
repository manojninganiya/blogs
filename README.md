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


## 🔍 🆚 .NET Core vs .NET Framework Comparison

| **Aspect**                       | **.NET Core / .NET (5+)**                                                | **.NET Framework**                              |
| -------------------------------- | ------------------------------------------------------------------------ | ----------------------------------------------- |
| **Cross-platform apps**          | ✅ Yes – Windows, Linux, macOS                                            | ❌ No – Windows only                             |
| **Web Development**              | ASP.NET Core (MVC, Razor Pages, Blazor)                                  | ASP.NET (System.Web, Web Forms, MVC)            |
| **Desktop Apps**                 | ✅ WPF & WinForms (Windows only since .NET Core 3.0)                      | ✅ WPF & WinForms (Windows only)                 |
| **Microservices**                | ✅ Excellent – lightweight, container-friendly                            | ❌ Not suitable – heavy, monolithic              |
| **Cloud Support**                | ✅ First-class Azure support, ideal for containers & serverless           | ⚠️ Limited, older integration                   |
| **CLI Tools**                    | ✅ Modern unified CLI (`dotnet`)                                          | ❌ Legacy MSBuild/Visual Studio-only             |
| **Side-by-side Versioning**      | ✅ Supported – apps can run different versions on the same machine        | ❌ Global install affects all apps               |
| **Package Management**           | ✅ NuGet + better dependency resolution                                   | ✅ NuGet                                         |
| **Third-party Support**          | ✅ Growing and modern (e.g., gRPC, Minimal APIs)                          | ⚠️ Mature but stagnating                        |
| **Long-term Viability**          | ✅ Active development (.NET 8+ and beyond)                                | ❌ Maintenance mode (only .NET Framework 4.8+)   |
| **Performance for Static Sites** | ✅ Lightweight and fast for generating static sites pre-deployment        | ❌ Not suitable – too heavy for static workflows |
| **Deployment Style**             | ✅ Self-contained, cross-platform publishing                              | ❌ Requires Windows IIS hosting                  |
| **Open Source**                  | ✅ Fully open-source under .NET Foundation                                | ⚠️ Partially open-source (limited components)   |
| **Learning Curve (Modern Dev)**  | ✅ Aligned with modern dev practices (DevOps, containers, CI/CD)          | ❌ More legacy concepts and tooling              |


## 🔍 🆚 Difference Between `String` and `StringBuilder`

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

## What is the difference between == and .Equals() in C#?

Trick: Many think they're the same.

== checks reference equality for reference types (unless overridden).

.Equals() checks value equality (can be overridden for custom logic).


string a = "hello";
string b = String.Copy(a);
Console.WriteLine(a == b);       // True
Console.WriteLine(a.Equals(b));  // True
Console.WriteLine(ReferenceEquals(a, b)); // False

## What will this output?

class A
{
    public A() { Print(); }
    public virtual void Print() => Console.WriteLine("A");
}

class B : A
{
    private string message = "B";
    public B() { }
    public override void Print() => Console.WriteLine(message);
}

new B();
Trick: Base constructor runs before derived fields initialize.

Output:

null
Because Print() is called from base constructor, and message is not yet set.

## Can a constructor be virtual in C#?
Answer:
No. Constructors cannot be virtual, abstract, or override.

## Can you override a static method in C#?
Answer:
No. Static methods belong to the type, not an instance — hence, they cannot be overridden.

## What is the output of this code?

int a = 5;
object o = a;
a = 10;
Console.WriteLine(o);
Answer:
5 — Because o is boxed with value 5, and a is modified afterward.

## What's the difference between ref, out, and in parameters?
Keyword	Must be initialized before passing?	Can be modified inside method?	Must be assigned in method?
ref	Yes	Yes	No
out	No	Yes	Yes
in	Yes	No	No

## Is string a reference type or value type? Can it behave like a value type?
Answer:

string is a reference type.

But it behaves like a value type due to immutability (any change creates a new object).

## What is the difference between abstract class and interface in C# 8+?
Trick: Interfaces can now have default implementations.

Abstract classes can have fields, constructors.

Interfaces (C# 8+) can have default implementations, but no state (no instance fields).

## Can finally block be skipped in any case?
Answer:
Yes, if:

The process is terminated (Environment.Exit or a crash).

Hardware failure/power off.

Infinite loop or Thread.Abort() in legacy code.

## What's the output?

string x = null;
Console.WriteLine(x?.Length ?? -1);
Answer:
-1 — Safe navigation ?. avoids exception, and null-coalescing operator provides a fallback.


#⚡ Tricky LINQ Questions
## What will this output?

var numbers = new List<int> { 1, 2, 3, 4, 5 };
var query = numbers.Where(n => n % 2 == 0);

numbers.Add(6);

foreach (var n in query)
{
    Console.WriteLine(n);
}
Answer:

2
4
6
Why?
Because LINQ uses deferred execution. The Where clause is not executed until the enumeration (foreach) happens.

## Difference between First() and FirstOrDefault()? What happens if the sequence is empty?
First() throws InvalidOperationException if no elements.

FirstOrDefault() returns default value (null for reference types, 0 for int, etc.).

3. Can you write a LINQ query that groups items and projects a custom result per group?
Yes (Example):


var people = new[]
{
    new { Name = "Alice", Age = 30 },
    new { Name = "Bob", Age = 40 },
    new { Name = "Charlie", Age = 30 }
};

var grouped = people.GroupBy(p => p.Age)
                    .Select(g => new { Age = g.Key, Count = g.Count() });

foreach (var group in grouped)
    Console.WriteLine($"{group.Age}: {group.Count}");
4. What's wrong with this LINQ code?

var result = someList.Select(async item => await SomeAsyncMethod(item)).ToList();
Trick: Looks fine, but it doesn't do what people expect.

Answer:
This gives a List<Task<T>>, not List<T>. You must await them:


var result = await Task.WhenAll(someList.Select(item => SomeAsyncMethod(item)));
🚀 Tricky async/await Questions
1. What will this output?

async Task<int> GetNumber() => 42;

void Main()
{
    var result = GetNumber();
    Console.WriteLine(result.Result);
}
Trick: Looks safe, but...

Answer:
This can cause a deadlock in UI environments like WinForms/WPF due to sync context. Safer to use:


await GetNumber(); // inside an async method
2. What’s the difference between Task, Task<T>, and async void?
Type	Return Value	Awaitable	Exception Handling	Use Case
Task	No	✅	✅ (catchable)	Async methods with no result
Task<T>	Yes	✅	✅ (catchable)	Async methods with a result
async void	No	❌	❌ (hard to catch errors)	Event handlers only

3. What happens if you await the same task twice?

Task<int> t = SomeAsyncMethod();
int a = await t;
int b = await t;
Answer:
This is fine — a completed task can be awaited multiple times. The result is reused.

4. Is this async method truly asynchronous?

public async Task<int> FakeAsync()
{
    return 42;
}
Answer:
No. It's marked async, but doesn’t actually await anything — it executes synchronously.

Better to write:


public Task<int> FakeAsync() => Task.FromResult(42);
5. What does ConfigureAwait(false) do? Why use it?
Answer:
It tells the await to not capture the current synchronization context (like UI thread).

Use in library code to avoid deadlocks and unnecessary context switching.

Not needed in ASP.NET Core (no sync context), but still good practice in libraries.

Would you like a few multiple-choice or real-world case-based questions too (e.g., LINQ performance traps or async in APIs)?




You said:
yes


ChatGPT said:
Awesome! Below are real-world, multiple-choice, and performance-based tricky questions for C# LINQ and async/await. These are the kinds of questions interviewers use to test beyond textbook knowledge.

🎯 Multiple-Choice LINQ Questions (Real-World)
Q1. What will be the output?
csharp
Copy
Edit
var list = new List<string> { "apple", "banana", "apricot", "blueberry" };
var result = list.Where(s => s.StartsWith("a")).OrderByDescending(s => s.Length).FirstOrDefault();
Console.WriteLine(result);
A. apple
B. apricot
C. banana
D. blueberry

✅ Correct Answer: B. apricot
Why: Starts with "a", and OrderByDescending(s.Length) makes "apricot" first.

Q2. Which statement about Select() vs SelectMany() is TRUE?
A. Both return the same structure always
B. Select() flattens nested sequences
C. SelectMany() flattens nested sequences
D. SelectMany() is slower than Select()

✅ Correct Answer: C. SelectMany() flattens nested sequences

Q3. Which LINQ method is best for avoiding multiple enumerations in a performance-critical loop?
A. ToList()
B. Select()
C. Where()
D. Aggregate()

✅ Correct Answer: A. ToList()

Why: Materializing once into a list avoids repeated enumeration (especially if the query is expensive or side-effect-prone).

🚀 Async/Await Multiple-Choice Questions
Q4. Which of the following can cause a deadlock in async code?
A. Using ConfigureAwait(false)
B. Calling .Result or .Wait() on a Task in the main thread
C. Using await in a background thread
D. Using async void for non-event methods

✅ Correct Answer: B and D

.Result / .Wait() in UI thread waits forever if task tries to resume on that UI thread.

async void swallows exceptions and can crash unexpectedly.

Q5. What does this code print?
csharp
Copy
Edit
async Task<int> GetValueAsync() => 42;

async Task PrintValueAsync()
{
    var task = GetValueAsync();
    Console.WriteLine("Before await");
    var value = await task;
    Console.WriteLine($"Value: {value}");
}

await PrintValueAsync();
A. Before await → Value: 42
B. Value: 42 → Before await
C. It throws an exception
D. The order is non-deterministic

✅ Correct Answer: A.

Because await is scheduled after "Before await" is printed.

🧠 Real-World Tricky Cases
🔥 Q6. Which LINQ pattern is dangerous in real-world codebases?
csharp
Copy
Edit
var items = GetItems();
foreach (var item in items.Where(x => SomeExpensiveCheck(x))) {
    Process(item);
}
What's the trap?

Answer:
Where() with expensive predicate executes on every iteration unless materialized. Use:

csharp
Copy
Edit
var filtered = items.Where(...).ToList(); // Materialize once
🔥 Q7. Why should you be cautious with async lambda in foreach like this?
csharp
Copy
Edit
foreach (var item in list)
{
    await Task.Run(async () => await DoSomethingAsync(item));
}
Answer:
You're firing and awaiting one-by-one, but each loop iteration creates a new async closure. It’s less readable and slower. Better:

csharp
Copy
Edit
foreach (var item in list)
{
    await DoSomethingAsync(item); // directly
}
OR in parallel (carefully):

csharp
Copy
Edit
await Task.WhenAll(list.Select(item => DoSomethingAsync(item)));



OOPs Concepts in C# (Short Summary - Ordered)
Here's a quick mnemonic to remember the 4 main OOP concepts in C# in order:

A PIE (Abstraction, Polymorphism, Inheritance, Encapsulation)

1. Abstraction
Hiding complex details, showing only essentials

Achieved through abstract classes/interfaces

2. Polymorphism
"Many forms" - same method behaves differently

Method overloading (compile-time)

Method overriding (runtime)

3. Inheritance
Base class → Derived class relationship

Code reusability through "is-a" relationship

4. Encapsulation
Bundling data + methods that operate on data

Access control via private/protected/public

Properties (getters/setters) for controlled access

Bonus: Some add a 5th concept - Association (objects relate to each other)

Would you like me to expand on any of these concepts?

trickey question for interview in C#
Tricky C# Interview Questions (With Explanations)
Here are some challenging C# questions that often trip up candidates:

1. Null Reference vs Null Object
Q: What's the difference between null and a NullReferenceException?

Tricky Part: Many think they're the same thing.

Answer:

null is a valid value indicating no object reference

NullReferenceException occurs when you try to access members of a null reference

2. String Immutability
Q: Why does string.Replace() not modify the original string?

Tricky Part: Many expect it to work like array manipulation.

Answer: Strings are immutable - all string methods return new strings rather than modifying the original.

3. Boxing/Unboxing Performance
Q: Why is this code inefficient?

csharp
int x = 10;
object o = x;  // Boxing
int y = (int)o; // Unboxing
Tricky Part: Hidden performance cost of value-type conversions.

4. Async/Await Misconception
Q: Does await make the calling thread wait?

Tricky Part: Async/await is often misunderstood as synchronous.

Answer: No, await releases the thread while waiting, then resumes execution.

5. Delegate vs Event
Q: Can you explain why we need events when we have delegates?

Tricky Part: Many don't understand the encapsulation benefit.

Answer: Events add encapsulation - only the declaring class can invoke them, while delegates can be invoked by anyone with access.

6. Garbage Collection Gotcha
Q: Will this object be garbage collected?

csharp
class Test {
    static void Main() {
        var obj = new LargeObject();
        obj = null;
        GC.Collect();
        // Is obj collected here?
    }
}
Tricky Part: GC isn't guaranteed to run immediately.

7. Value Type in Heap
Q: Can value types ever be allocated on the heap?

Tricky Part: Common misconception that value types always go on stack.

Answer: Yes, when they're boxed or fields of reference types.

8. Multiple Inheritance
Q: How does C# implement multiple inheritance?

Tricky Part: C# doesn't support it directly but has alternatives.

Answer: Through interface inheritance - a class can implement multiple interfaces but inherit only one class.

Would you like me to provide answers to any of these or add more tricky questions?

yes
Here are detailed answers to the tricky C# questions, along with some additional challenging questions:

Detailed Answers to Previous Questions
1. Null Reference vs Null Object
csharp
string s = null;
Console.WriteLine(s.Length); // NullReferenceException
null means "no object."

NullReferenceException occurs when you try to access a member (method/property) of a null object.

2. String Immutability
csharp
string s1 = "Hello";
string s2 = s1.Replace("H", "J"); // Returns new string "Jello"
Console.WriteLine(s1); // Still "Hello" (original unchanged)
Strings cannot be modified after creation.

Methods like Replace(), ToUpper(), etc., return new strings.

3. Boxing/Unboxing Performance
csharp
int num = 10;
object boxed = num; // Boxing (heap allocation)
int unboxed = (int)boxed; // Unboxing (type check + copy)
Boxing converts a value type to object (heap allocation).

Unboxing converts back (type check + copy).

Performance impact: Extra memory and CPU overhead.

4. Async/Await Misconception
csharp
async Task DoWorkAsync()
{
    await Task.Delay(1000); // Thread released, not blocked
    Console.WriteLine("Done"); // Continuation
}
await does not block the thread—it yields control.

The calling thread is free to do other work.

5. Delegate vs Event
csharp
public delegate void Notify();
public event Notify OnCompleted; // Safer than a public delegate
Delegates: Can be invoked by anyone (myDelegate()).

Events: Only the declaring class can invoke (OnCompleted?.Invoke()).

6. Garbage Collection Gotcha
csharp
var obj = new LargeObject();
obj = null;
GC.Collect(); // Suggestion, not guaranteed
GC.WaitForPendingFinalizers(); // Ensures finalizers run
GC is non-deterministic—calling GC.Collect() doesn’t guarantee immediate collection.

Use using or IDisposable for deterministic cleanup.

7. Value Type in Heap
csharp
int x = 10; // Stack (usually)
object boxed = x; // Heap (boxing)
class MyClass { public int Y; } // Y is on heap when MyClass is instantiated
Value types usually live on the stack (local variables).

But can be on the heap if:

Boxed (object o = 5).

A field in a reference type (class A { int B; }).

8. Multiple Inheritance
csharp
interface IA { void Foo(); }
interface IB { void Bar(); }
class C : IA, IB { ... } // Legal
class D : A, B { ... } // Illegal if A and B are classes
C# allows multiple interface inheritance but only single class inheritance.

Additional Tricky C# Questions
9. readonly vs const
Q: When would you use readonly instead of const?

csharp
const int X = 10; // Compile-time constant
readonly int Y = DateTime.Now.Second; // Runtime value
const: Value fixed at compile-time (must be a literal).

readonly: Value set at runtime (can be in constructor).

10. Task vs ValueTask
Q: Why would you use ValueTask instead of Task?

csharp
public ValueTask<int> ComputeAsync()
{
    if (cache.TryGetValue(key, out var result))
        return new ValueTask<int>(result); // No heap allocation
    else
        return new ValueTask<int>(SlowOperationAsync());
}
ValueTask avoids heap allocation for synchronous results (performance optimization).

11. IEnumerable vs IQueryable
Q: Why does this LINQ query hit the database twice?

csharp
var query = dbContext.Users.Where(u => u.Age > 20);
int count = query.Count(); // DB Query 1
var list = query.ToList(); // DB Query 2
IQueryable is lazy—executes when enumerated (ToList(), Count()).

Solution: Materialize once (var list = query.ToList(); then list.Count).

12. struct Default Constructor
Q: Why can’t you define a parameterless constructor in a struct?

csharp
struct Point
{
    public int X, Y;
    // public Point() { X = 1; Y = 1; } // Illegal before C# 10
}
Before C# 10: Structs couldn’t have explicit parameterless constructors (always zero-initialized).

C# 10+: Now allowed, but rarely needed.

13. volatile Keyword
Q: When should you use volatile?

csharp
private volatile bool _flag;
Ensures read/write operations are not reordered by the compiler/CPU.

Used in multithreading (but lock or Interlocked are often better).

14. yield return Under the Hood
Q: How does yield return work?

csharp
IEnumerable<int> GetNumbers()
{
    yield return 1; // Compiler generates a state machine
    yield return 2;
}
The compiler creates a state machine to handle lazy enumeration.

No collection is built upfront—values are generated on-demand.

Final Thoughts
These questions test deep understanding of:
✔ Memory management (stack vs heap, GC)
✔ Asynchronous programming (async/await, Task)
✔ Type system (value vs reference, boxing, struct vs class)
✔ Design decisions (why C# restricts multiple inheritance)

Would you like me to cover more advanced topics like dependency injection, ref structs, or pattern matching?

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

