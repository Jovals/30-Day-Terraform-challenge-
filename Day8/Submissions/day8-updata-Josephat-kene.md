# Day 8: Terraform Modules

### Name: Josephat Kene

### Task Completed: Day 8: Reusing Infrastructure with Modules

### Date: 12/12/24

### Time: 5:16am

### Module Basics", "Inputs", and "Outputs

I understood what a terraform module is, which is a terraform configuration that is not in your present working directory. It also aids reuability within your terraform code,

I also learnt about module inputs and outputs. How you have to create an output block in the terraform child module to be able to use it in the root or parent module. and to reference the module outputs in the root module, the syntax "module.<module-name>.<output-name>" is used.

Also variables defined in the child modules that aren't given a default value are required when referncing that child module in the root/parent module, and so must be set whenever the module is used.
