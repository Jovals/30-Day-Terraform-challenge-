# Day 11: Terraform Conditionals

### Name: Josephat Kene

### Date: 15/12/24

### Time: 5:16am

### Terraform Conditionals

### Task Completed: Day 11:

I read the conditionals part of chapter 5 where i learnt how to use the count parameter for conditional resources with the format "<condition> ? <true_val> : <fale_val>" which will evaluate a boolean logic in condition and if the result is true, returns the true_val, if false, returns the false_val.
I also learnt about conditionals with the for_each and for expression using the dynamic block. Also onditionals with if string directive. 

I also read the zero time deployment by using the name parameter for ASG to depend on the name of the launch configuration, set the `create_before_destroy` parameter to true and the `min_elb_capacity` parameter to the minimum size of the cluster.

I also learnt about the limitations of count parameter and for_each parameter as well as the limitations of the zero time deployment used. 

I also watched the udemy videos on variable collection and structure types, Working with data blocks and also terraform built in functions. Here i learnt how to use list and maps for variables and how to reference them on my resources, query existing resources using a data block and export attributes from a data lookup and Functions that are available for actions on numeric values, string values, collections, date and time, filesystem, and many others.