---
date: 2025-02-09
tags:
  - architecture
  - spring
---
This design pattern allows to separate the data access operations from the domain layer (where the business logic resides). It does so in form of a class, that can take in Entities as generics, and then perform CRUD operations on these entities. 
Basically, repository implementations are classes that encapsulate the logic for accessing data.

## Spring Data repositories

Springs implementation of the [Repository pattern](Repository%20pattern.md). 
The spring data repository abstraction is there to reduce the boilerplate required for CRUD operations through an ORM.
It relates to the [Controller-Service-Repository architecture](Controller-Service-Repository%20architecture.md) in spring boot apps and domain-driven-design.

Common operations that we want to do are for example getting the specific fields from an entity. Instead of implementing this same boilerplate over and over again, all we need to do instead is create an interface and extend the interfaces provided by spring boot. The methods for accessing those fields will already magically exist then. We only need to implement the special methods that we need. 
```
public inteface ApiUserRepository extends CrudRepository<ApiUser, Integer> {}
```
The second argument to the generic is the type of the primary key. 

There are multiple of these interfaces we can extend, another one is "JpaRepository".
The JpaRepository extends another interface "PagingAndSortingRepository" which in turn extends CrudRepository. This means that JpaRepository will also have some extra stuff to do pagination and sorting, as well as JPA-related methods like flushing the persistance context and deleting records in a batch.

### References

[Repository](https://martinfowler.com/eaaCatalog/repository.html)
