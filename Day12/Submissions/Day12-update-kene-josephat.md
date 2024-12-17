# Day 12: Zero-Downtime Deployment with Terraform

## Participant Details

- **Name:** Kene Josephat
- **Task Completed:** Zero-Downtime Deployment with Terraform
- **Date and Time:** 15/12/2024 10:10PM

I read the zero time deployment by using the name parameter for ASG to depend on the name of the launch configuration, set the `create_before_destroy` parameter to true and the `min_elb_capacity` parameter to the minimum size of the cluster and also deployed the ASG.

I also understood the concept of blue/green deployment and canary releases

I watched the videos on udemy and got a better understanding of the Terraform workflow which has 3 main steps (write, plan and apply). 
I also got a deeper understanding of the Terraform main commands i.e: `terrform init`, `terraform plan`, `terraform validate` and `terraform destroy`