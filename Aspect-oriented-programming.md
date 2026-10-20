---
date: 2025-03-05
tags:
  - architecture
  - spring
---
A programming paradigm that aims to increase modularity, by allowing the separation of [cross-cutting-concerns](#cross-cutting-concerns). It does so by adding additional behavior to the code without modifying the code, instead separately specifying which code is modified via [pointcuts](#pointcuts). This could be for example to log all function calls when the functions name begins with "set". With this we can add stuff that is not central to the business logic (such as logging) without cluttering the code that has core functions.

## Cross-cutting concerns

In [AOC](Aspect-oriented-programming.md), these are [aspects](#aspects) of a program that affect several modules, without the possibility encapsulated in any of them. They cannot be cleanly separated from the rest of the system, and can thus cause scattering (code duplication), tangling (dependencies between modules) or both.
[AOC](Aspect-oriented-programming.md) aims to encapsulate cross-cutting concerns into [aspects](#aspects) to retain modularity. 
Obvious example of an [aspect](#aspects) that crosscuts many different modules would be logging, as it needs to be included into many different parts.
### Examples:
- Data validation
- Logging
- Monitoring
- Persistance
- Caching
- Global config settings like env vars
-

## Aspects

With AOC we can just define a a standalone module called [Aspect](#aspects). It contains one or more [advices](#advice) that have [pointcuts](#pointcuts) defined as to at what time to execute the [advices](#advice). 

## Join points

Is a point in the control flow where the control flow can arrive via two different paths. In [AOC](Aspect-oriented-programming.md) a set of join points is called a pointcut. A join point is a point of execution in the code where the [advice](#advice) specified in a corresponding [pointcut](#pointcuts) is applied.

## Advice

In [ascpect](#aspects) and functional programming, advice describes a class of functions that modify other functions when the latter are run. Those get executed at a given [join point](#join-points) of a programm. Those join points can be method calls, field access or exceptions.


### Use
Generally to modify or extend the behavior of functions which cannot or should not be. Its similar to python decorators or java annotations, but advices don't require the actuall modification of the class that the method is in.
Careful: advices can introduce confusion as its not apparent from the method that gets modified, that its getting modified externally.

## Pointcuts

In [AOC](Aspect-oriented-programming.md) a pointcut is a set of [join points](#join-points). A pointcut specifies where exactly to apply an [advice](#advice). They are often specified using class names or method names. 
They solve the problem of modularizing [cross cutting concerns](#cross-cutting-concerns).
With them the programmer can basically weave (merge) different [aspects](#aspects) into a a complete application without touching the actual code, and thus facilitating separation of concerns.

## Example

Consider this method:
```
void transfer(Account fromAcc, Account toAcc, int amount, User user,
    Logger logger, Database database) throws Exception {
  logger.info("Transferring money...");
  
  if (!isUserAuthorised(user, fromAcc)) {
    logger.info("User has no permission.");
    throw new UnauthorisedUserException();
  }
  
  if (fromAcc.getBalance() < amount) {
    logger.info("Insufficient funds.");
    throw new InsufficientFundsException();
  }

  fromAcc.withdraw(amount);
  toAcc.deposit(amount);

  database.commitChanges();  // Atomic operation.

  logger.info("Transaction successful.");
}
```

This method has transactions, security and logging as [cross cutting concerns](#cross-cutting-concerns).
We would need to duplicate the security across multiple similar methods. Or in the best case modify the transfer method when we change for example the isUserAuthorised method. 
A good [pointcut](#pointcuts) can anticipate later program changes, so if a new developer creates a new method to access the bank account, the advice will still apply to the new method.

## Trade-offs

Can make the code hard to understand.
