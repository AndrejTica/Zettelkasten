---
date: 2025-03-05
tags:
  - architecture
---
In [[Aspect-oriented-programming|AOC]], these are [[Aspect|aspects]] of a program that affect several modules, without the possibility encapsulated in any of them. They cannot be cleanly separated from the rest of the system, and can thus cause scattering (code duplication), tangling (dependencies between modules) or both.
[[Aspect-oriented-programming|AOC]] aims to encapsulate cross-cutting concerns into [[Aspect|aspects]] to retain modularity. 
Obvious example of an [[Aspect|aspect]] that crosscuts many different modules would be logging, as it needs to be included into many different parts.
### Examples:
- Data validation
- Logging
- Monitoring
- Persistance
- Caching
- Global config settings like env vars
- 


### References

