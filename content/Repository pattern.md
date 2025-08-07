---
date: 2025-02-09
tags:
  - architecture
---
This design pattern allows to separate the data access operations from the domain layer (where the business logic resides). It does so in form of a class, that can take in Entities as generics, and then perform CRUD operations on these entities. 
Basically, repository implementations are classes that encapsulate the logic for accessing data.

### References
[Repository](https://martinfowler.com/eaaCatalog/repository.html)
