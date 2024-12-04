# Day 3: Deploying Basic Web Server Infrastructure with terraform

## Participant details

- Name: Kene Josephat
- Task: Basic web server
- Date: [4/12/2024 11:40am]

## main.tf

`main.tf` file carrying my aws provider, AWS EC2 instance reosurce block and security group resource block.

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
nohup busybox httpd -f -p 8080 &
EOF
user_data_replace_on_change = true

tags = {
  Name = "web-server"
}
}

resource "aws_security_group" "instance" {
name = "terraform-example-instance"
ingress {
from_port = 8080
to_port = 8080
protocol = "tcp"
cidr_blocks = ["0.0.0.0/0"]
}
}
```

`terrafrom.tf` file containing the latest version of terraform configurartion.

```
terraform {
  required_providers {
    aws = {
      source = "hashicorp/aws"
      version = "5.63.0"
    }
  }
}



```

## Details

I finished the Chapter 2 of the book and did the hands on above. I also watched the videos "Terraform Plug-in Based Architecture" (Video 11), "Provider Block" (Video 12) and "Resource Block" (Video 13) on udemy and learnt about provider block and resource block.
