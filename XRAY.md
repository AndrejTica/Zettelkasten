---
date: 2025-08-01
tags:
  - devops
  - testing
---
Xray gives 3 basic tools:
1. Test repository 
2. Test sets
3. Test plans

### Repository 
Provides a traditional way of managing the test cases. We can create folders like for functional tests
and for user scenario tests. 
Limitation: We can create only one folder structure and therefore organize our folder structure in one way. Its also a project level feature, so it can only contain tests from that project. 

### Test set
Is just a group of tests. Its more flexible because a set can contain test cases from multiple projects. Also, a single test case can live in multiple test sets. 
That means we can organize them by feature, by phase, or release. Think of it more as a tagging feature, more than a folder feature. We can use test sets together with test repositories.

### Test plan
This is used for planning our testing activities or testing event, like for example testing at the end of each sprint, so one test plan for each sprint or release testing. 
We can create a test plan when we create a new issue, we just select the test plan.
It starts of empty so we need to add tests to it. We can then add tests from a test set.
The test plan has a view "testing board". There, we can also organize the tests into a folder structure, rather than just a flat list of tests.
Like for example we can do a folder for E2E tests or regressions tests that the team has identified as high value regression tests.
Next, we can create one or more executions for these tests. 
After the tests and test executions have been planned, they can be approved using any third party signature app. Once it has been approved, its ready for execution . 


### References

