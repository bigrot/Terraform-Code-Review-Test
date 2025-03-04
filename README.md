# Terraform-Code-Review-Test
Terraform code for an AWS infrastructure
## Deliverables
### General Observations: 
1. Code is not reusable as resources were not modularized.
2. security group to the ECS allows all trafiic ["0.0.0.0/0"] and on all ports  opening up the application to all kinds of vulnerabilities. 
3. Load balancers are required for fault tolerance and traffic distribution. 
4. Assuming multiple developers are working on the .tf state file, there will have  to be a remote state file set up with an object stored in an s3 bucket and DynanoDB state locking. 
5. No output variable explicitly defined in cases where one needs to see key resource attributes like public IP, vpc id, cluster name, etc...

## Issues Identified: A list of specific issues or areas for improvement, with explanations.
###	Suggested Improvements:
1. Modularize resources for reusability( suggested modules)
~~~
├── modules
│   ├── vpc
│   ├── ecs
│   ├── asg
│   ├── security
├── main.tf
├── variables.tf`
├── outputs.tf
├── terraform.tfvars
~~~
2. Enforce IAM for authentication 
##	Annotate the code (e.g., with comments or inline suggestions) to demonstrate your analysis.
code comment line 80
