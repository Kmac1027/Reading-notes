# Read: Class 03

## The Repository Design Pattern

-[Link to Article](https://cubettech.com/resources/blog/introduction-to-repository-design-pattern/)

- design patterns do not depend on specific technology, framework or programming language. In Software Engineering a design pattern is a reusable solution to a general problem occurring in a given context in software design. A design pattern is not a design which is directly transferred into code
- A Repository mediates between the domain and data mapping layers, acting like an in-memory domain object collection. Client objects construct query specifications declaratively and submit them to Repository for satisfaction. Objects can be added to and removed from the Repository, as they can from a simple collection of objects, and the mapping code encapsulated by the Repository will carry out the appropriate operations behind the scenes.
- Repository pattern separates the data access logic and maps it to the business entities in the business logic. Communication between the data access logic and the business logic  is done through interfaces.
()[https://cubettech.com/wp-content/uploads/2015/07/Reposiory-Design-Pattern.png]

- Repository pattern is a kind of container where data access logic is stored. It hides the details of data access logic from business logic. In other words, we allow business logic to access the data object without having knowledge of underlying data access architecture.
- The separation of data access from business logic have many benefits. Some of them are:
  1. Centralization of the data access logic makes code easier to maintain
  1. Business and data access logic can be tested separately
  1. Reduces duplication of code
  1. A lower chance for making programming errors
- Repository design pattern is  fully stick onto interfaces. An interface acts like a contract which specify what an concrete class must implement. Let’s explore it a little bit. Suppose we have two data objects Uploader and Video, what are common set of operations that can be applied to these two data objects? In most situations we want to have the following operations:
  1. Get all records
  1. Get paginated set of records
  1. Create a new record
  1. Get record by it’s primary key
  1. Get record by some other attribute
  1. Update a record
  1. Delete a record

### Flexibility through Repositories

- In order to separate our Controllers from the database in right manner, we are going to abstract that interaction into repositories. A repository is simply an interface between two things.
- So instead of referencing Eloquent directly, we can reference UserRepository. We can then bind UserRepository to EloquentUserRepository so that Laravel knows that whenever we mention UserRepository we want an instance of EloquentUserRepository. Now that we have abstracted the database layer into repositories it makes it much easier to switch database ORM.
- For example, if you wanted to use Mongo instead, you would simply create a MongoUserRepository and bind UserRepository to it rather than EloquentUserRepository.
- Now, whenever Laravel wants a UserRepository it will return MongoUserRepository.
So you don’t have to change any of the code in your Controllers on a database technology change.

## In Memory Database Testing

- [Link t Article](https://dev.to/paulasantamaria/testing-node-js-mongoose-with-an-in-memory-database-32np)]

### In-memory database pros & cons

#### Pros

1. No need for mocks: Your code is directly executed using the in-memory database, exactly the same as using your regular database.
1. Faster development: Given that I don't need to build a mock for every operation and outcome but only test the query, I found the development process to be faster and more straightforward.
1. More reliable tests: You're testing the actual code that will be executed on production, instead of some mock that might be incorrect, incomplete or outdated.
1. Tests are easier to build: I'm not an expert in unit testing and the fact that I only need to seed the database and execute the code that I need to test made the whole process a lot easier to me.

#### Cons

1. The in-memory database probably needs seeding
1. More memory usage (dah)
1. Tests take longer to run (depending on your hardware).

- [mongo Memory Server](https://www.npmjs.com/package/mongodb-memory-server)


[Back to code 401 notes](../401-Javascript.md)