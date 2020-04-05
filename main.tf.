# Using a single workspace:
terraform {

  backend "remote" {
    hostname = "app.terraform.io"
    organization = "marcdemo"

    workspaces {
      name = "tfe-ado-cli-run-example"
    }
  }

}

provider "aws" {
  version = "~> 2.0"
  region  = "us-east-1"
}

# Create a VPC
resource "aws_vpc" "example" {
  cidr_block = "10.0.0.0/16"
}

variable "name_length" {
  type    = "string"
  default = "2"
  description = "The number of words to put into the random name"
}

resource "random_pet" "server" {
  length = "${var.name_length}"
}

resource "local_file" "random" {                                                   
  content     = "${random_pet.server.id}"                                        
  filename = "${path.module}/random.txt"                                         
}

resource "null_resource" "cluster" {}

output "name" {
  value = "${random_pet.server.id}"
}





