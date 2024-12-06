## Day 5 Activities

Name - Kene Josephat
Date and Time - Thursday 05, Dec, 2024. 10.15pm

## Udemy Videos
I watched the video on data block which shows us how we can use it to query or load data from other sources (eg aws console) into our code and use the value of the data in other parts of the code
The next video talked about the terraform configuration block which is how we can configure terraform to run on a particular version of terraform
The third video showed us how modules can be used either by using the modules in our local machine by saving it in a modules folder or loading it for the terraform modules registery or github which aids the resuablity of our codes.
The last video showed us how we can use the output block to get details or valuses of some details of our infrastrutures out in our CLI or use them somewhere else in our code. 

## Chapter: Complete Chapter 2 and start Chapter 3 how to manage Terraform state

Deploying a cluster of web servers with aws auto scaling group and load balancers. 

## main.tf 

```
provider "aws" {
region = "us-east-1"
}


resource "aws_launch_configuration" "example" {
image_id = data.aws_ami.ubuntu_22_04.id
instance_type = "t2.micro"
security_groups = [aws_security_group.instance.id]

user_data = <<-EOF
#!/bin/bash
echo "Hello, World" > index.html
nohup busybox httpd -f -p ${var.server_port} &
EOF

#Required when using a launch configuration with an auto scaling group
lifecycle {
  create_before_destroy = true
}

}
data "aws_subnets" "default" {
  filter {
    name = "vpc-id"
    values = [data.aws_vpc.default.id]
  }
  
}

data "aws_ami" "ubuntu_22_04" {
  most_recent = true

  filter {
    name   = "image_id"
    values = ["ubuntu/images/hvm-ssd/ubuntu-jammy-22.04-amd64-server-*"]
  }

  owners = ["099720109477"]
}
resource "aws_autoscaling_group" "example" {
  launch_configuration = aws_launch_configuration.example.name
  vpc_zone_identifier = data.aws_subnets.default.ids

  target_group_arns = [aws_lb_target_group.asg.arn]
  health_check_type = "ELB"

  min_size = 2
  max_size = 5
  
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

resource "aws_lb" "example" {
  name = "terraform-asg-example"
  load_balancer_type = "application"
  subnets = data.aws_subnets.default.ids
  security_groups = [aws_security_group.alb.id]
}

resource "aws_lb_listener" "HTTP" {
  load_balancer_arn = aws_lb.example.arn
  port = 80
  protocol = "HTTP"
  #by default, return a simple 404 page
  default_action {
    type = "fixed response"

    fixed_response {
      content_type = "text/plain"
      message_body = "404: page not found"
      status_code = 404
    }
    
  }
}

resource "aws_security_group" "alb" {
  name = "terraform-example-alb"

  #Allow inbound http request

ingress {
  from_port = 80
  to_port = 80
  protocol = "tcp"
  cidr_blocks = ["0.0.0.0/0"]

}

#Alllow all outbound request
egress {
  from_port = 0
  to_port = 0
  protocol = "-1"
  cidr_blocks = ["0.0.0.0/0"]
}
}
resource "aws_lb_target_group" "asg" {
  name = "terraform-asg-example"
  port = var.server_port
  protocol = "HTTP"
  vpc_id = data.aws_vpc.default.id

  health_check {
    path = "/"
    protocol = "HTTP"
    matcher = "200"
    interval = 15
    timeout = 3
    healthy_threshold = 2
    unhealthy_threshold = 2
  }
}

resource "aws_lb_listener_rule" "asg" {
  listener_arn = aws_lb_listener.HTTP.arn
  priority = 100

  condition {
    path_pattern {
      values = ["*"]
    }
  }
  action {
    type = "forward"
    target_group_arn = aws_lb_target_group.asg.arn 
  }
  
}
output "alb_dns_name" {
  value = aws_lb.example.dns_name
  description = "The domain name of the load balancer"
  
}

```

## variable.tf

```
variable "server_port" {
  description = "The port the server will use for HTTP requests"
  type = number
  default = 8080

}

```
