## Day 4 Task : Mastering Basic Infrastructure with Terraform

_Josephat kene | Wed, December 4 2024 | 11:12 pm - GMT+1_

## Activities

I understood the concept and use of variables. How using variables allows for reuseability and not having to hard code values in our main.tf as it would be pushed to github. And not having to repeat code in our terraform. Also learnt about the different types of variables in terraform like list, string, boolean, numbers, etc. And also learnt about local variables.

## main.tf

```
provider "aws" {
region = "us-east-1"
}


resource "aws_instance" "example" {
ami = "ami-04a81a99f5ec58529"
instance_type = "t2.micro"
vpc_security_group_ids = [aws_security_group.instance.id]
user_data = <<-EOF
#!/bin/bash
echo "Hello, World" > index.html
nohup busybox httpd -f -p ${var.server_port} &
EOF
user_data_replace_on_change = true

tags = {
  Name = "web-server"
}
}

resource "aws_security_group" "instance" {
name = "terraform-example-instance"
ingress {
from_port = var.server_port
to_port = var.server_port
protocol = "tcp"
cidr_blocks = ["0.0.0.0/0"]
}
}

```

## Variables.tf

```
variable "server_port" {
  description = "The port the server will use for HTTP requests"
  type = number
  default = 8080

}

```
