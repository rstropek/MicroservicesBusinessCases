# Business Case: EverTech Financial Solutions

## Background

### The Company

*EverTech Financial Solutions* is a mid-sized financial technology company established in 1995. It specializes in offering a comprehensive banking platform for community banks and credit unions. Their flagship product is an all-in-one banking system called *BankComplete*, which handles everything from account management, loans processing, and customer relationship management to internal banking operations.

Over the years, *EverTech* has grown from a startup to a prominent software vendor in the financial tech industry. The company’s headquarters is located in London, with key regional offices in New York City and Bengaluru. Bengaluru is the tech hub of the company. *EverTech*'s largest R&D center is located here. It also comprises development teams, QA engineers, a dedicated innovation lab, and technical support staff. Since its founding, *EverTech* has established a significant presence in the global financial software sector and employs over 1,500 professionals across its locations.

### Market Position

*EverTech* enjoys a reputation as a reliable software vendor in the financial domain. Their solutions are known for stability and comprehensive coverage of financial operations. However, with the increasing shift towards digital transformation in banking, EverTech's leadership acknowledges the need to innovate and keep their products agile and scalable, ensuring they remain at the forefront of fintech evolution.

While *EverTech*'s vast customer base and established products provide a solid foundation, the fintech landscape is evolving rapidly. Newer entrants in the market, armed with modern technology stacks and agile methodologies, pose significant competition. The senior leadership, after extensive deliberations, recognizes the pressing need to modernize their primary solutions, starting with *BankComplete*.

*BankComplete*, EverTech Financial Solutions' flagship product, is exclusively offered as an on-premises software solution. This means that instead of being hosted in the cloud and provided as a service over the internet, *BankComplete* is installed, hosted, and run directly on the end customer's in-house servers and IT infrastructure. However, as the fintech landscape evolves, with increasing demand for cloud solutions and the advantages they bring in terms of scalability, cost-efficiency, reduced total-cost-of-ownership, and remote access capabilities, *EverTech* considers exploring SaaS or hybrid models for *BankComplete* or its other product offerings in the future.

## Current Architecture

### Overview

*BankComplete*'s current architecture embodies a [*Service-Oriented Architecture* (SOA)](https://en.wikipedia.org/wiki/Service-oriented_architecture) design philosophy. It emphasizes modular design where each module performs a set of distinct functions and communicates with other modules via an [*Enterprise Service Bus* (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus).

### System Components

- *Full-Client Application*: The primary interface for most administrative users is a Java-based full-client application. It offers a comprehensive suite of tools and options for managing and overseeing all bank operations. This client application requires installation on users' machines.
  
- *Web Solutions*: For end-customers and certain types of users, *BankComplete* offers web-based interfaces. These are also Java-driven, typically using the [*Jakarta Faces* (JSF)](https://en.wikipedia.org/wiki/Jakarta_Server_Faces) framework to deliver web content. They provide features like account management, transfers, statement views, and more, accessible via web browsers.

- *Modules*: Each module, built on the Java stack, encapsulates specific business logic. For instance, there are modules for account management, loans processing, customer relationship management, fraud detection, etc. These modules are built as separate services, each responsible for a distinct set of tasks within the system. They communicate and share data via the ESB and a central database.

- *Enterprise Service Bus (ESB)*: Serving as the communication backbone of *BankComplete*, the ESB facilitates interactions between the modules. It ensures that the right data reaches the right module at the right time, managing complex orchestration, routing, and transformation rules. The ESB also handles service invocations, fault tolerance, and various cross-cutting concerns like logging and security.
  
- *Central Database*: All modules rely on a single, centralized Oracle SQL database. This database stores all the transactional data, customer profiles, account details, loan information, and more. Given its centralized nature, there's a high degree of interdependency, meaning a change in one module could have implications on the data structures used by other modules. The database is typically optimized for ACID transactions and has been fine-tuned over the years for performance.

### Central Database

The centralized database architecture of *BankComplete*, while historically providing several benefits in terms of data consistency and integrity, is now becoming a barrier to innovation for EverTech. Here are some of the reasons why:

- *Single Point of Change*: Any new feature or change that requires a modification to the database schema or structure can potentially impact multiple modules or parts of the system. This makes changes riskier and requires extensive testing, slowing down the pace of development.

- *Vertical Limits*: The monolithic nature of the central database means that to handle more load or data, it often needs to be scaled up (adding more computational power to the existing server). There are physical and economic limits to how much a system can be scaled vertically.

- *Dependent Modules*: Because all modules interact with a single, centralized database, they are intricately linked. A change in one module's data requirements can have cascading effects on other modules. This tight coupling inhibits the ability to make rapid, isolated changes.

- *Downtime*: Implementing changes or updates to the central database might require downtime or at least reduced performance periods, which can be a significant disruption, especially for a banking system.
  
- *Rollbacks*: If a new feature or update causes issues, rolling back changes in a central database can be complex, especially if data migrations or schema changes were involved.

- *Diverse Data Needs*: Not all data fits neatly into the tabular structures of traditional relational databases. As *EverTech* considers innovative features, they might require more flexible data structures (like graphs or documents) or different data processing paradigms that a central SQL database might not efficiently support.

## Java Library Collection for Cross-cutting Concerns

### Overview

Over its nearly three decades of operations, *EverTech* has recognized the recurring challenges and patterns in software development. This led the company to invest in building a proprietary, closed-source collection of Java libraries and components. These tools were designed to address the various cross-cutting concerns that arise when developing large-scale software platforms like *BankComplete*. The aim was to ensure consistency, reduce redundancy, and increase the efficiency of their development processes.

- Data Access Library *EverDataAccess*:
    - Provides abstracted methods to interact with databases, reducing the boilerplate code needed for CRUD (Create, Read, Update, Delete) operations.
    - Incorporates optimized query generation and execution.
    - Includes connection pooling to manage and reuse database connections, reducing the overhead of establishing connections.

- Logging Framework *EverLog*:
    - A comprehensive logging solution tailored for the needs of financial applications.
    - Includes features like log rotation, archival, and configurable formatting.
    - Integration capabilities with *BankComplete*'s central monitoring and alerting, ensuring real-time awareness of any critical issues.

- Security Library *EverSecure*:
    - Handles authentication and authorization mechanisms, ensuring that users have appropriate permissions.
    - Provides encryption and decryption utilities, crucial for sensitive financial data.

- Configuration Management Component *EverConfig*:
    - A centralized solution to manage application configurations across different environments (development, testing, production).
    - Provides hierarchical configurations, letting specific modules or functionalities override global settings if required.

- Exception Handling Library *EverException*:
    - Standardizes the way exceptions are caught, processed, and reported.
    - Integrates with *EverLog* for detailed logging of exceptions.

- Communication Library *EverComm*:
    - Offers utilities to facilitate communication between modules, especially for asynchronous operations.
    - Provides support for various messaging patterns like Publish-Subscribe or Request-Reply.
    - Incorporates serialization and deserialization mechanisms for message payloads.

These libraries, coupled with rigorous documentation and internal training, have become the backbone of *EverTech*'s software development processes. By standardizing and optimizing these cross-cutting concerns, *EverTech* ensures that its products, especially platforms like BankComplete, are consistent, maintainable, and built upon proven solutions.

### Challenges

*EverTech* has traditionally adopted a centralized approach to the development and maintenance of their extensive collection of Java libraries, which address cross-cutting concerns in software development. This means that a single, core team is responsible for the design, development, updates, and troubleshooting of these libraries, ensuring they remain consistent and optimized for use across the company's software products, including the flagship product, BankComplete.

Challenges Faced by the Centralized Team:

- *Balancing Support and Innovation*: With the libraries being critical components used across many products, the team frequently receives support requests from various product teams. Handling these requests, while simultaneously driving innovation and adding new features to the libraries, becomes a demanding juggle. The balance skews more towards support than proactive development.

- *Resource Constraints*: With the vast number of products and features relying on these libraries, the volume of support requests, bug reports, and enhancement suggestions can be overwhelming for a centralized team. It strains their capacity and often leads to delays.

- *Dependency Bottlenecks*: Since updates or changes to the libraries can impact multiple products, the release cycles for library updates are lengthy. Product teams often wait for essential library enhancements, causing project delays.

- *Communication Gaps*: The centralized nature means that the team has to interact with multiple product teams, often leading to communication challenges. Feedback loops become longer, and there might be instances of misaligned priorities.

The senior management team at *EverTech* is aware of these challenges. They recognize that while the centralized approach ensured consistency and quality in the earlier stages of the company, it is now becoming a hindrance to agility and rapid innovation. The management believes that this centralized model, with its current challenges, is slowing down the pace of innovation for the company as a whole, potentially affecting *EverTech*'s market position and growth prospects.

## Java

For many years, Java has been the cornerstone of *EverTech* Financial Solutions' technology stack, powering *BankComplete* and other products. Java's portability, robustness, and mature ecosystem made it a prime choice for enterprise-level software solutions. However, as the digital landscape shifts and new challenges emerge, relying solely on Java may no longer be sufficient to cater to the diverse and evolving needs of modern banking and financial solutions.

Currently, two technology stacks are particularly interesting for *EverTech*. Other technologies might also be considered in the future.

- *Python* for Data Science and Machine Learning: Python's expressive and concise syntax makes it perfect for rapid prototyping and experimentation, vital for data science projects. Libraries like *TensorFlow*, *PyTorch*, *scikit-learn*, and *Pandas* make Python the de facto language for data manipulation, analytics, and machine learning.

- *Rust* for High-Performance, High-Secure Data Processing: Rust is designed with a focus on memory safety without compromising on performance. In an age where parallel processing and leveraging multi-core architectures are crucial for performance, Rust's concurrency model stands out, allowing for efficient and safe concurrent code. Rust's zero-cost abstractions mean that developers don't sacrifice performance for higher-level constructs. This makes Rust comparable to languages like C and C++ in terms of execution speed, but with modern syntax and safety guarantees.

## EverTech's Shift to Microservices - Your Tasks

*EverTech* has invited you as an external software architecture consultant to examine the feasibility and implications of transitioning their flagship product, *BankComplete*, from its current SOA-based monolithic structure to a microservices architecture. Your task is to delve into the potential changes this transition might bring on both the architectural and organizational fronts. Answer questions like:

- What are the high-level consequences of a shift to microservices for *BankComplete*'s architecture? Consider aspects such as:
    * Data management and databases
    * Service communication
    * Scalability and performance
    * Deployment and continuous integration
    * Error handling and resilience

- How can the granular, modular nature of microservices potentially catalyze and expedite the innovation cycle at *EverTech*? Consider aspects like faster testing, iterative development, and isolated risk.

- Currently, *BankComplete* operates on an on-premises model. How might a shift to microservices architecturally and operationally facilitate the evolution of *BankComplete* into a Software-as-a-Service (SaaS) offering?

- The shift to microservices isn’t just technical; it’s organizational. How might the company's structure and teams need to evolve to support a microservices architecture? Look at:
    * Team responsibilities and specializations
    * Cross-functional collaboration
    * Communication channels and decision-making hierarchies
    * Skill development and training needs

- What kind of cultural changes might *EverTech* face internally among its teams and employees as they shift to a microservices paradigm?
   
- How does fragmenting the system into multiple services impact the security paradigm? What new security challenges might arise, and how can they be preemptively addressed?
