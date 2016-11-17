[C# Sharp Checklist](https://github.com/chuckconway/c-sharp-code-review-checklist)

**General**

*Does it meet the Business Requirements?*

- At a minimum understand the intent of the business requirements, this gives insight into what the code is trying to accomplish.

*Is the code easily understood?*

- A good rule of thumb is if you can't understand the code within 3 minutes, it's too complicated.

*Does it conform to the agreed coding conventions?*

- The coding conventions are posted here:

[C# Style Guide](https://github.com/chuckconway/c-sharp-style-guide/blob/master/README.markdown)

*Are the classes, methods and variables spelled correctly?*

Ensure all the names are spelled correctly.

*Are there any instances of Hungarian notation?*

Avoid pre-pending the type to the variable name.

    string strName = "Chuck";

*Is the Boy Scout rule applied (is the code better than before it was change)?*

Was the code left better than when it was found?

**Code**

*Is there redundant or duplicate code?*

Avoid copying and pasting code. When possible extract the common functionality into a shared method or service.

*Is the code as modular as it could be?*

Can this code be broken into smaller functional components? Is there a repeating pattern in the code?

*Is there any Dead Code?*

Is there any code that is no longer used, such as variables or methods?

*Is there any commented out code?*

Is there any commented code that should be removed?

*Can the code be simplified?*

A common simplification is used an if statement when a ternary operator can be used or using an if statement to set a boolean value. Are the methods long? A method more than 5 to 10 lines deserves extra scrutiny.

*Can any of the code be replaced with Library Functions?*

Are there functions that can be replaced with Library functions? i.e., using a for or a foreach when the same can be acomplished with LINQ.

*Does the code follow the SOLID principles?*

- Single Responsibility
- Open-Close Principle
- Liskov substitution principle
- Interface segregation principle
- Dependency Inversion Principle

[SOLID Principles](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design))

*Do the names the accurately describe the intent of the code?*

As code evolves, sometimes the intent of the variables changes.

*Is the code Thread safe?*

Is code setting the value of a static variable?

*Are resources disposed of properly?*

Is Dispose called on objects that implemented IDispose? What happens when an exception is thrown? Is Dispose still called?

*Are the exceptions being swallowed?*

This includes logging with in a catch statement and not throwing  the exception after the logging it. It also includes throwing "throw ex;" which overwrites the stack trace.

*Is there any deeply nested code? (more than 3 levels deep)*

Nesting more than 3 deep, whether it is a foreach statement or an if statement is a sign that there might be a simpler to accomplish the same thing.

*Is there code that could significantly impact performance?*

Is Select N+1 an issue when retrieving data from the database in a loop? Is the data model retrieving more data than needed?

**Security**

*Are all the data imports checked (for the correct type, length, format and range) and encoded?*

Is the data constraints check before it is accepted into the system? For example, if there is a start and end date, are we ensuring the start date occurs before the end date?

*Where third-party utilities/libraries are used, are returning errors caught?*

Are we allowing throwing party's internal exceptions to bubble up into our code?

*Are there any SQL Injection vulnerabilities?*

Are parameters used when calling stored procedures? Are parameters used when in-lining SQL in C# (not that we should be doing this either)?

*Do API Endpoints have proper authentication and authorization?*

Do our endpoints meet the security requirements?

*Are there any Cross Site Scripting (XSS) vulnerabilities?*

Is there unsanitized data accepted from the client that is returned to the client?

**Testing**

*Is the code testable?*

Can the code be mocked? Are there hidden dependencies?

*Do tests exist and are they comprehensive?*

Were unit tests created? Do they cover all the scenarios?
