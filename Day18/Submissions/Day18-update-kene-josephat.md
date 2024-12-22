### Name: Josephat Kene
### Task Completed: Day 18: Implemented unit tests, integration tests, and end-to-end tests for a Terraform project
### Date: 21/12/24
### Time: 4:16pm

### Automated Testing of Terraform Code

Finished the chapter 9 of the terraform up and running book.

I undertood that pure testing with terraform is hard. Considering HCL is not really a programming language. 
Automated tests fundamentally involve:
- Unit tests: Which is basically testing a single resuable module on terraform

- integration tests: This validates how several units (modules) work. That is testing multiple modules on terraform

- End-to-end tests: In terraform, this means deploying everything into an environment that mimics production and test it from the end user's perspective

An extern library buildt with Go is usually used to test terraform code to ensure it works as expected. It is called terratest.

I also learnt about the limitations of these types of testing.

Other testing approaches are: Static analysis which is same as running `terraform validate` command, Plan testing which is running the `terraform plan` command and Server testing.