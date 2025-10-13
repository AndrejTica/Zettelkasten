---
date: 2025-03-05
tags:
  - architecture
---
A programming paradigm that aims to increase modularity, by allowing the separation of [[Cross-cutting-concern|cross-cutting-concerns]]. It does so by adding additional behavior to the code without modifying the code, instead separately specifying which code is modified via [[Pointcut|pointcuts]]. This could be for example to log all function calls when the functions name begins with "set". With this we can add stuff that is not central to the business logic (such as logging) without cluttering the code that has core functions. 

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

This method has transactions, security and logging as [[Cross-cutting-concern|cross cutting concerns]].
We would need to duplicate the security across multiple similar methods. Or in the best case modify the transfer method when we change for example the isUserAuthorised method. 
With AOC we can just define a a standalone module called [[Aspect|Aspect]]. It contains one or more [[Advice|advices]] that have [[Pointcut|pointcuts]] defined as to at what time to execute the [[Advice|advices]]. 
A good [[Pointcut|pointcut]] can anticipate later program changes, so if a new developer creates a new method to access the bank account, the advice will still apply to the new method. 

### The bad
Can make the code hard to understand. 


### References

