# Day 9: Continuing Reuse of Infrastructure with Modules

### Name: Josephat Kene

### Date: 12/12/24

### Time: 5:16am

### Module Gotchas and Module Versioning

### Task Completed: Day 8:

I leant about Module gotchas which is about the file paths for our user data templatefile for any scripting file you reference in your terraform code and also using seperate resources as opposed to using inline blocks to avoid using both and also because seperate resources can be added anywhere and it makes your module more flexible and configurable.

i also learnt about module versioning which enables you to one version of a terraform module in eg the staging environment and another version in the production environment so it can be easy to test changes to your terraform configuration. 

I also watched the videos on module scope where i learnt how to seperate the root modules and child module into seperate files. i.e main.tf, outputs.tf and variables.tf for better structure and readability
I watched the video on terraform sources and terraform registry where i learnt that you can get a module from different sources eg the local source (code in your local machine), github, terraform public registry and also even an S3 bucket are all examples of sources on the terraform module
