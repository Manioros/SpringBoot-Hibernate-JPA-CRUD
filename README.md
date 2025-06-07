# SpringBoot-Hibernate-JPA-CRUD Project

This project, "SpringBoot-Hibernate-JPA-CRUD", provides a basic demonstration of CRUD (Create, Read, Update, Delete) operations for managing student data. It utilizes Spring Data JPA for persistence and interaction with a relational database.

## Core Functionalities Implemented:

The application showcases the following fundamental database operations:

### Create (Save) Students:
* `createStudent`: Saves a single `Student` object to the database.
* `createMultipleStudents`: Saves three predefined `Student` objects to the database in a single execution.

### Read (Retrieve) Students:
* `readStudent`: Retrieves a `Student` by their generated ID after saving.
* `queryForStudents`: Retrieves and displays all `Student` records from the database.
* `queryForStudentsByLastName`: Retrieves and displays `Student` records filtered by a specific last name.

### Update Students:
* `updateStudent`: Retrieves a `Student` by ID, modifies their first name, and then updates the record in the database.

### Delete Students:
* `deleteStudent`: Deletes a `Student` record based on their ID.
* `deleteAllStudents`: Deletes all `Student` records from the database and reports the number of rows deleted.

## Project Structure and Components:

The project is structured with clear separation of concerns, typical for Spring Boot applications:

* **`CruddemoApplication.java`**: This is the main Spring Boot application class. It sets up the Spring context and defines a `CommandLineRunner` bean. The `CommandLineRunner` is used to execute various CRUD operations when the application starts, with most operations commented out to allow selective testing.
* **`Student.java`**: This is the JPA entity class representing the `Student` table in the database.
    * It's annotated with `@Entity` and `@Table(name="student")` to map it to a database table named "student".
    * `@Id` and `@GeneratedValue(strategy = GenerationType.IDENTITY)` configure the `id` field as the primary key with auto-incrementing capabilities.
    * `@Column` annotations map class fields to corresponding database columns (e.g., `firstName` to `first_name`).
    * It includes constructors, getters, setters, and a toString() method for object representation.
* **`StudentDAO.java`**: This is an interface that defines the Data Access Object (DAO) contract for `Student` operations. It declares methods for `save`, `findById`, `findAll`, `findByLastName`, `update`, `delete`, and `deleteAll`.
* **`StudentDAOImp.java`**: This is the implementation of the `StudentDAO` interface.
    * It's annotated with `@Repository` to mark it as a Spring repository component.
    * It uses `jakarta.persistence.EntityManager` for interacting with the database. The `EntityManager` is injected via constructor.
    * `@Transactional` annotation is used on methods that modify the database (e.g., `save`, `update`, `delete`, `deleteAll`) to ensure atomicity of operations.
    * It leverages `entityManager.persist()` for saving, `entityManager.find()` for finding by ID, `entityManager.merge()` for updating, and `entityManager.remove()` for deleting.
    * JPQL (Java Persistence Query Language) queries are used for `findAll()`, `findByLastName()`, and `deleteAll()`.

## Technologies Used:

* **Spring Boot**: Framework for building stand-alone, production-grade Spring applications.
* **Spring Data JPA**: Simplifies data access layer development by providing an abstraction over JPA.
* **Hibernate**: (underlying JPA implementation) Object-relational mapping (ORM) framework.
* **Maven**: Build automation tool.
* **MySQL**: A widely used open-source relational database management system.

## Overall Purpose:

The project serves as a clear and concise example of how to implement fundamental database interactions in a Spring Boot application using the Spring Data JPA paradigm, specifically configured to work with a MySQL database. It demonstrates best practices such as separating concerns (DAO layer), using annotations for configuration, and leveraging Spring's dependency injection.

---