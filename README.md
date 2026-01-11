TASK 1 – Spring Boot Basics & First Web Application
📌 Project Overview

This project was created as Task 1 for the Spring Framework Apps course at Akademia Finansów i Biznesu Vistula.
The main goal of this task is to understand how a basic Spring Boot application works, how HTTP requests are handled, and how Spring MVC connects backend logic with a simple frontend view.

The application is a simple Spring Boot web application that:

starts an embedded server (Tomcat),

exposes HTTP endpoints using a Spring Controller,

returns plain text responses using @ResponseBody,

renders an HTML view using Thymeleaf,

follows the MVC (Model–View–Controller) design pattern.

This project was created from scratch using Spring Initializr and run locally on localhost:8080.

🛠 Technologies Used

Java (latest compatible version)

Spring Boot

Spring Web

Thymeleaf

Maven

Lombok

Project Creation (Spring Initializr)

The project was generated using https://start.spring.io/
 with the following configuration:

Project: Maven

Language: Java

Spring Boot Version: Latest (non-snapshot)

Packaging: Jar

Java Version: Latest compatible

Dependencies:

Spring Web

Thymeleaf

Lombok

After downloading, the project was unpacked and imported into the IDE (IntelliJ IDEA).

▶️ Running the Application

Open the project in your IDE

Make sure Maven dependencies are loaded

Right-click project → Maven → Reload Project

Run the main class:

Task1Application.java


The application starts on:

http://localhost:8080


Spring Boot automatically starts an embedded Tomcat server, so no external server is required.

🚀 Application Logic Explained
🔹 Main Class – Application Entry Point
@SpringBootApplication
public class Task1Application {
    public static void main(String[] args) {
        SpringApplication.run(Task1Application.class, args);
    }
}


What happens here?

@SpringBootApplication enables:

component scanning,

auto-configuration,

Spring Boot startup logic.

SpringApplication.run() starts the entire Spring context and embedded server.

🔹 Controller Layer
GreetingController
@Controller
public class GreetingController {


This class is responsible for:

handling HTTP requests,

returning responses (text or views),

acting as the Controller in MVC.

🧪 First Endpoint – Plain Text Response
@GetMapping("/")
@ResponseBody
public String hello() {
    return "Hello Spring Boot!";
}

Explanation:

@GetMapping("/")
Handles HTTP GET requests sent to /

@ResponseBody
Tells Spring to return raw text, not a view

The browser displays:

Hello Spring Boot!


📍 URL:

http://localhost:8080/

🔹 MVC Pattern Implementation

This project uses Spring MVC, which separates responsibilities:

Layer	Responsibility
Model	Data (not used yet in Task 1)
View	HTML template (Thymeleaf)
Controller	Handles requests and returns views
🧩 View-Based Endpoint
@GetMapping("/greeting")
public String greeting(Model model) {
    model.addAttribute("message", "Welcome to Spring Boot MVC!");
    return "greeting";
}

What happens step by step:

Client sends request to /greeting

Controller method is executed

Model object stores data (message)

"greeting" tells Spring to load:

resources/templates/greeting.html


Thymeleaf renders the HTML page

📍 URL:

http://localhost:8080/greeting

🎨 Thymeleaf Template – greeting.html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
    <title>Greeting Page</title>
</head>
<body>
    <h1 th:text="${message}"></h1>
    <img src="/vistula.png" alt="Vistula Logo" width="200">
</body>
</html>

Explanation:

th:text="${message}"
Inserts data from the controller model

Static image is loaded from:

src/main/resources/static/

🖼 Static Resources

Spring Boot automatically serves files from:

src/main/resources/static


Used in this project:

vistula.png – displayed on the HTML page

No additional configuration is required.

🌐 HTTP Methods Used
Method	Endpoint	Description
GET	/	Returns plain text
GET	/greeting	Returns HTML view
🧪 Testing the Application
Browser

Open:

http://localhost:8080/
http://localhost:8080/greeting

Postman

Method: GET

URL:

http://localhost:8080/


Response:

Hello Spring Boot!

📄 .gitignore

The project includes a .gitignore file to prevent committing:

compiled files,

IDE configuration files,

system-specific files.

This keeps the repository clean and professional.

✅ Task 1 Goals Achieved

✔ Created Spring Boot project from scratch
✔ Used Spring Initializr
✔ Implemented first controller
✔ Handled HTTP GET requests
✔ Used @ResponseBody correctly
✔ Implemented MVC pattern
✔ Rendered HTML using Thymeleaf
✔ Served static resources
✔ Tested application in browser

🧠 Conclusion

This project demonstrates a solid understanding of Spring Boot fundamentals, including:

project configuration,

request handling,

MVC architecture,

view rendering,

and application startup flow.

Task 1 serves as a foundation for more advanced concepts such as REST APIs, databases, and Swagger, which are implemented in Task 2.

Tests: 
<img width="1279" height="916" alt="image24" src="https://github.com/user-attachments/assets/f3bfab89-710d-477b-8d91-4a0d29464f1a" />
<img width="1279" height="915" alt="image67" src="https://github.com/user-attachments/assets/f6c5cc76-12dc-430d-96b1-5a27d28d18ad" />

