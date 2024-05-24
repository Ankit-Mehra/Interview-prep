# General Technical Questions

**Can you tell us about your experience working with both front-end and back-end technologies in web applications? (Front-end and Back-end Experience)**

As a Software Developer Intern at CAAT Pension Plan, I've had the opportunity to work with both front-end and back-end technologies in web applications.

On the back end, I've been involved in refactoring code, ensuring its maintainability and readability. Additionally, I have written unit tests to enhance the reliability of existing code.  I worked actively  on implementing a Multifactor Authentication feature, enabling users to change their phone numbers from within the application.

For the front-end, I've been responsible for making various UI improvements, including removing a survey feature that is not needed anymore to optimize the user experience. I developed the UI for resetting the MFA authentication method for admin user in the app.

In my role as a Software Development Engineer at Ceridian, I was responsible for developing a search tool using C# and WPF. This tool allowed for efficient searching of specific strings within files in a directory, aiding in the cleanup of the codebase

Overall, my experience working on both front-end and back-end technologies has allowed me to contribute to the development and improvement of web applications while gaining a comprehensive understanding of the software development lifecycle.

**How familiar are you with C#, .NET Standard/Core, Web API, and MVC? Can you provide examples of projects where you have used these technologies? (C# and .NET Technologies)**

I am very familiar with C#, .NET Standard/Core, Web API, and MVC, and I have hands-on experience working with these technologies in various projects. In my previous internship with Ceridian, I developed a WPF application using C#. The application served as an internal tool to clean the unused SQL Files.

And in my current position we are using C#  for backend. I worked on building a RESTful Web API using C# and ASP.NET Web API. The API served as the backend for a web application. I designed and implemented the API endpoints, enabling the web app to interact with the database and retrieve data efficiently. Specifically, i worked on implementing a Multifactor Authentication feature, enabling users to change their phone numbers from within the application.

**Do you have experience with persistence storage and ORM (SQL/NoSQL)? Could you elaborate on the projects where you utilized these technologies? (Persistence and ORM)**

ORM frameworks allow developers to work with relational databases in an object-oriented manner, abstracting the complexities of database operations and enabling them to interact with the database using object-oriented programming concepts. I have been working with .Net framework in my current position as well as in my last internship and we use the Entity Framework which is Microsoft’s official ORM framework.

**Can you share your experience with Unit/Integration Testing and its importance in software development? (Unit/Integration Testing).**

Unit and Integration Testing play a pivotal role in the software development process, ensuring the quality and reliability of the codebase. In my current position, I have actively engaged in unit testing on existing code and recognized its significant impact on performance, maintainability, and bug prevention.

In my current position I have been doing unit testing on already developed code and I have come across many situations where I was able to do performance improvements by refactoring code. Also, I have also came across code that would have created bugs in the future that I was able to refactor thereby increasing maintainability.

Describe API in layman terms?

Imagine you are in a restaurant and you use menu to order food. The menu is like an API (Application Programming Interface)

In simple terms, the menu/API provides a list of dishes/services (functions) that the restaurant/system offers. You, as the customer, don't need to know how the chef prepares the dish or how the kitchen works. You just need to know what's on the menu (the options available) and how to order.

Similarly, an API allows different software systems to communicate with each other. It defines a set of rules (like a menu) that lets one software application request certain services or information from another application, without needing to understand the inner workings of that application. It's a way for different apps or systems to "talk" to each other and share data or functionality, just like you order food from a menu without knowing the details of how each dish is cooked in the kitchen.

What is web services . Explain with examples

Web services are a set of technologies and standards that allow different software applications to communicate and exchange data over the internet. They provide a way for disparate systems, often built on different programming languages and platforms, to interact with each other seamlessly. Web services enable the integration of diverse applications and facilitate the development of distributed, interoperable systems.

There are two main types of web services: SOAP (Simple Object Access Protocol) and REST (Representational State Transfer). Both types use standard web protocols like HTTP for communication.

1. **SOAP Web Services:**
    - **Description:** SOAP is a protocol for exchanging structured information in web services using XML. It defines a set of rules for structuring messages, which are typically sent over HTTP or SMTP.
    - **Example:** Consider a scenario where a company's e-commerce website needs to integrate with a third-party payment processing service. The e-commerce application can send a SOAP request to the payment service with details of the transaction, and the payment service responds with a SOAP message indicating the success or failure of the transaction.
2. **RESTful Web Services:**
    - **Description:** REST is an architectural style for designing networked applications. RESTful web services use standard HTTP methods (GET, POST, PUT, DELETE) to perform operations on resources identified by URLs. They often return data in a lightweight format like JSON or XML.
    - **Example:** An online weather service provides RESTful web services to deliver weather information. A client application can make an HTTP GET request to the service's endpoint, specifying the location as part of the URL. The service responds with the current weather data in a structured format, such as JSON.
3. **JSON-RPC and XML-RPC:**
    - **Description:** JSON-RPC and XML-RPC are remote procedure call (RPC) protocols encoded in JSON and XML, respectively. They enable the invocation of procedures or functions on a remote server using a simple syntax.
    - **Example:** A content management system (CMS) may use JSON-RPC to allow remote clients to create, update, or retrieve content on the server. The client sends a JSON-encoded request, and the server responds with a JSON-encoded result.
4. **GraphQL:**
    - **Description:** GraphQL is a query language for APIs and a runtime for executing those queries. It provides a more efficient, powerful, and flexible alternative to traditional REST APIs by allowing clients to request only the data they need.
    - **Example:** A social media platform may implement GraphQL to enable clients to retrieve specific details about a user's profile, posts, and comments in a single query, reducing over-fetching of data.

Web services are fundamental to the development of distributed and interconnected applications, allowing different systems to communicate and share information seamlessly. They play a crucial role in enabling the integration of diverse technologies and services across the web.

Given a scenario where an application is experiencing performance issues, what steps would you take to identify and resolve the problem?

**Define the Problem:**

- Gather specific information about the performance issue. Identify when the problem started, the affected features, and any recent changes to the application.

**Reproduce the Problem:**

- Attempt to recreate the performance issue under controlled conditions. This step is essential to ensure that you fully understand the problem's symptoms and can observe its impact on the application.

**Isolate the Issue:**

- Determine whether the performance problem is systemic or if it's specific to certain features, functionalities, or user interactions. Isolating the issue helps in targeting the troubleshooting efforts more effectively.

**Gather Detailed Data:**

- During the reproduction of the problem, collect detailed data and metrics. This may include performance logs, error messages, and any relevant information that can aid in the analysis. Tools like profiling and monitoring software can be valuable at this stage.

**Review Codebase:**

- Conduct a code review to identify inefficient algorithms, resource-intensive functions, or poorly optimized code. Tools like profilers can help identify performance bottlenecks within the code.

**Database Analysis:**

- If the application involves a database, analyze the database queries and their execution times. Optimize queries, add indexes, or restructure data where necessary to improve database performance.

**Caching Strategies:**

- Implement or review caching strategies to reduce the load on the server. Utilize appropriate caching mechanisms for static or infrequently changing data.

**Network Performance:**

- Evaluate the network performance between different components of the application. High latency or network issues can impact the overall performance.

**Scale Resources:**

- If the application is under heavy load, consider scaling resources, such as increasing server capacity, utilizing a Content Delivery Network (CDN), or optimizing server configurations.

What is meant by microservices. Explain with examples

Microservices is an architectural style that structures an application as a collection of small, independent services, each focused on a specific business capability. These services are developed, deployed, and scaled independently, allowing for greater flexibility, agility, and scalability in software development. Microservices promote the idea of breaking down a monolithic application into smaller, loosely coupled services that can be developed and maintained separately.

Key characteristics of microservices include:

1. **Independence:** Microservices are independent entities, meaning they can be developed, deployed, and scaled independently of each other. Each microservice typically has its own database and can be developed by a separate team.
2. **Decentralized Data Management:** Each microservice manages its own data, and there is no centralized database. This allows for better data autonomy and reduces dependencies between services.
3. **Communication via APIs:** Microservices communicate with each other through well-defined APIs (Application Programming Interfaces). This enables them to interact while remaining loosely coupled.
4. **Single Responsibility:** Each microservice is designed to perform a specific business function or service. It has a single responsibility and is focused on doing that task well.
5. **Scalability:** Microservices can be scaled independently based on the specific demands of each service. This allows for efficient resource allocation and better performance.

Now, let's look at an example to illustrate the concept of microservices:

**Example: E-commerce Platform**

Consider an e-commerce platform that traditionally would be built as a monolithic application. In a monolith, all functionality, such as user management, product catalog, shopping cart, and order processing, would be tightly integrated into a single application.

In a microservices architecture, this e-commerce platform could be broken down into individual microservices:

1. **User Service:**
    - Manages user registration, authentication, and profile information.
2. **Product Service:**
    - Handles product catalog, inventory, and details.
3. **Cart Service:**
    - Manages shopping cart functionality, including adding, updating, and removing items.
4. **Order Service:**
    - Handles order processing, payment, and order history.
5. **Review Service:**
    - Manages product reviews and ratings.

Each of these microservices is an independent entity with its own database and business logic. They communicate with each other through well-defined APIs. For example, when a user adds an item to the shopping cart, the Cart Service may communicate with the Product Service to get the latest product information.

Benefits of Microservices:

- **Scalability:** Each service can be scaled independently based on its specific needs.
- **Flexibility:** Teams can work on and deploy services independently, enabling faster development cycles.
- **Fault Isolation:** If one service fails, it doesn't necessarily affect the entire application.
- **Technology Diversity:** Different services can use different technologies that best fit their requirements.

However, it's important to note that while microservices offer numerous advantages, they also introduce challenges, such as increased complexity in managing distributed systems and ensuring proper communication between services. Organizations need to carefully consider their specific needs and circumstances when deciding whether to adopt a microservices architecture.

What are CSRF tokens ? Why and how is it used. Explain with examples

Cross-Site Request Forgery (CSRF) is a type of security vulnerability where an attacker tricks a user's browser into making an unintended request to a web application on which the user is authenticated. CSRF attacks typically exploit the trust that a website has in the user's browser by using the user's credentials to perform malicious actions without the user's knowledge.

CSRF tokens are a countermeasure to protect against CSRF attacks. They are random, unique values generated by the server and included in the HTML form or request. The token is then validated by the server when the form is submitted or the request is made, ensuring that it originated from the same site and was not forged by an attacker.

Here's why and how CSRF tokens are used:

### Why CSRF Tokens?

1. **Mitigating CSRF Attacks:**
    - CSRF tokens are an effective defense mechanism against CSRF attacks. By including a unique token in each request, the server can verify that the request is legitimate and originated from the same site.
2. **Preventing Unauthorized Actions:**
    - Without CSRF protection, an attacker could trick a user into unintentionally performing actions on a site where the user is authenticated. CSRF tokens help prevent such unauthorized actions.
3. **Protecting State-Changing Operations:**
    - CSRF tokens are particularly important for requests that result in state changes on the server, such as modifying user account details, making financial transactions, or updating settings.

### How CSRF Tokens Work:

1. **Token Generation:**
    - When a user logs in or accesses a page with a form, the server generates a CSRF token, which is then associated with the user's session.
    
    ```html
    <form action="/updateProfile" method="post">
        <input type="hidden" name="csrfToken" value="a8e4d7f6...">
        <!-- Other form fields -->
        <button type="submit">Update Profile</button>
    </form>
    ```
    
2. **Inclusion in Forms or Requests:**
    - The CSRF token is included as a hidden field in HTML forms or as a custom header in AJAX requests.
3. **Validation on the Server:**
    - When the form is submitted or the request is made, the server checks the CSRF token's validity. If the token is missing or incorrect, the server rejects the request.
    
    ```csharp
    [HttpPost]
    [ValidateAntiForgeryToken]
    public ActionResult UpdateProfile(ProfileViewModel model)
    {
        // Validate CSRF token
        // Process the request
        // ...
    }
    ```
    
    - In [ASP.NET](http://asp.net/) MVC, the `[ValidateAntiForgeryToken]` attribute is used to automatically validate the CSRF token.

### Example:

Consider a scenario where a user is authenticated on a banking website and wants to transfer funds between accounts. Without CSRF protection, an attacker could craft a malicious webpage that automatically submits a form to transfer funds when the user visits the page. With CSRF protection using tokens:

1. **Token Generation:**
    - When the user logs in, the server generates a unique CSRF token and associates it with the user's session.
2. **Form Submission:**
    - When the user initiates a fund transfer, the CSRF token is included in the form.
    
    ```html
    <form action="/transferFunds" method="post">
        <input type="hidden" name="csrfToken" value="a8e4d7f6...">
        <input type="text" name="amount" placeholder="Enter amount">
        <button type="submit">Transfer Funds</button>
    </form>
    ```
    
3. **Validation on the Server:**
    - When the form is submitted, the server checks the CSRF token's validity. If the token is missing or incorrect, the server rejects the request.
    
    ```csharp
    [HttpPost]
    [ValidateAntiForgeryToken]
    public ActionResult TransferFunds(TransferViewModel model)
    {
        // Validate CSRF token
        // Process the fund transfer
        // ...
    }
    ```
    

This way, even if an attacker tries to trick the user's browser into submitting a fund transfer form, the request will be rejected because the CSRF token is invalid.

In summary, CSRF tokens are a critical security measure to prevent unauthorized actions on a web application by ensuring that requests originate from the same site and are not forged by malicious actors. They are an important part of secure web application development, especially for operations that involve state changes or sensitive data.

If you have to do a calculation where would you do it in the database or in the application. Explain with different scenarios and examples.

The decision of whether to perform a calculation in the database or in the application depends on various factors, including the nature of the calculation, performance considerations, data retrieval needs, and architectural preferences. Here are some scenarios and examples to help guide this decision:

### Perform Calculation in the Database:

1. **Aggregations and Summary Calculations:**
    - **Scenario:** When calculating aggregates, summaries, or complex calculations involving large datasets.
    - **Example:** Calculating the total sales amount, average order value, or sum of quantities for a product category.
    
    ```sql
    SELECT Category, SUM(Quantity) AS TotalQuantity
    FROM Sales
    GROUP BY Category;
    ```
    
2. **Data Transformation and Cleansing:**
    - **Scenario:** When data transformation or cleansing is required before presenting the results to the application.
    - **Example:** Converting currency values, adjusting time zones, or cleaning up data inconsistencies.
    
    ```sql
    SELECT ProductName, CONVERT(VARCHAR, Price * 1.1) AS PriceWithTax
    FROM Products;
    
    ```
    
3. **Performance Optimization:**
    - **Scenario:** When offloading computations to the database can improve query performance, especially for complex calculations.
    - **Example:** Calculating running totals, cumulative sums, or weighted averages efficiently.
    
    ```sql
    SELECT Date, SalesAmount, SUM(SalesAmount) OVER (ORDER BY Date) AS CumulativeSales
    FROM Sales;
    
    ```
    

### Perform Calculation in the Application:

1. **Business Logic and Complex Algorithms:**
    - **Scenario:** When the calculation involves intricate business logic, domain-specific rules, or complex algorithms.
    - **Example:** Calculating a score based on multiple factors with intricate rules specific to the application's domain.
    
    ```csharp
    public decimal CalculateScore(int factor1, int factor2, int factor3)
    {
        // Complex business logic to calculate the score
        // ...
    }
    
    ```
    
2. **Real-Time User Interaction:**
    - **Scenario:** When the calculation is driven by real-time user interactions and responsiveness is crucial.
    - **Example:** Updating a live dashboard with real-time data, where calculations depend on user input or preferences.
    
    ```jsx
    // JavaScript code in the browser
    function updateDashboard(userPreferences) {
        // Perform calculations based on user preferences
        // Update the dashboard in real-time
        // ...
    }
    ```
    
3. **Dynamic Calculations or Customization:**
    - **Scenario:** When the calculation logic needs to be dynamically adjusted based on user preferences, settings, or customization.
    - **Example:** Allowing users to configure their own custom calculations or apply dynamic filters.
    
    ```csharp
    public decimal PerformDynamicCalculation(UserPreferences preferences, List<DataItem> data)
    {
        // Dynamic calculation based on user preferences
        // ...
    }
    ```
    

### Considerations for the Decision:

1. **Data Retrieval Overhead:**
    - If the calculated result requires additional data not present in the database, it may be more efficient to perform the calculation in the application after retrieving the necessary data.
2. **Maintainability and Separation of Concerns:**
    - Complex business logic and application-specific calculations are often better placed in the application layer to maintain a clean separation of concerns.
3. **Scalability:**
    - Consider the scalability of your system. Offloading computations to the database may be beneficial for large datasets, but it could introduce additional load on the database server.
4. **Development Flexibility:**
    - Performing calculations in the application provides more flexibility in terms of development, testing, and debugging. It allows for easier changes and updates to the calculation logic without affecting the database schema.

In summary, the decision of whether to perform a calculation in the database or in the application depends on factors such as the nature of the calculation, performance considerations, maintainability, and architectural preferences. It's often a trade-off between leveraging the capabilities of the database for data-related computations and the flexibility and control offered by performing calculations in the application layer.