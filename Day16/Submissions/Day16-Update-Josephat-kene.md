# Day 16: Building Production-Grade Infrastructure

## Participant Details

- **Name:** Josephat Kene
- **Task Completed:** Edited code to be production-grade ready
- **Date and Time:** 20th December, 2024 | 1:04 AM GMT+1

I read the Chapter 8 of the terraform up and running book and got a deeper knowledge on how to refactor code and write production grade ready terraform code.

I learnt about the questions or checklist to go through and consider when deploying an infrastructrue to production. Also learnt the importance of writing small modules tha do a single thing and do it well, how to make the modules composable and resuable with variables and outputs, and how to make modules testable by using validations for the variable block and also adding precondition and postcondition blocks to our resources. 

I also learnt on the importance of versioning the modules and also the module dependencies by using the terraform block to pin the required version of terraform and pinning the providers. 

i also learnt about using terraform provisioners, provisioners with null_resource ane external data source to execute scripts on a local machine or remotely when running terraform