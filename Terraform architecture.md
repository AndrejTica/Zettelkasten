---
date: 2025-03-28
tags:
  - "#terraform"
  - "#infrastructure"
---
Instead of having one state file per environment, with "Terraservices" architecture we have one state file per component. 
This can help us with the problem of trying to change one thing, but that one thing influences also unrelated parts of the infrastructure. 

Todolist:
- Create parent repo that stores all the terraform components. It contains the pipeline that pushes the modules to the gitlab terraform registry. 
- For each project, create a cloud infrastructure repo. First, it contains the folders of the individual servies, then the folders for the environments of these services, and finally folders of each of the component that contains its own statefile. 
- Bonus: create bash scripts that creates a merge request in the azure sandbox repo. 
### References

