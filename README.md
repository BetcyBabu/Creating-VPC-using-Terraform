# Creating VPC using Terraform 

## Objective

- Write a tf file using [Data Sources](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/regions), [cidrsubnet](https://www.terraform.io/docs/language/functions/cidrsubnet.html) to use with Terraform to create VPC Infrastructure

## Prerequisites

- [AWS Access Key and Secret Key](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html)
- [Install Terraform](https://learn.hashicorp.com/tutorials/terraform/install-cli?in=terraform/aws-get-started)

## Usage

- [Install Git](https://github.com/git-guides/install-git)
- Clone the repo

```
git clone https://github.com/BetcyBabu/Creating-VPC-using-Terraform.git
cd Terraform-VPC-sample
terraform init
terraform apply
```

This creates a VPC with DNS-hostname enabled, Internet Gateway, Subnets 6 (3 public, 3 private), Elastic IP, NAT gateway, Route tables (Private 1, Public 1), and Subnet Association.

## Result

```
Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:     

  # aws_eip.eip will be created
  + resource "aws_eip" "eip" {
      + allocation_id        = (known after apply)
      + association_id       = (known after apply)
      + carrier_ip           = (known after apply)
      + customer_owned_ip    = (known after apply)
      + domain               = (known after apply)
      + id                   = (known after apply)
      + instance             = (known after apply)
      + network_border_group = (known after apply)
      + network_interface    = (known after apply)
      + private_dns          = (known after apply)
      + private_ip           = (known after apply)
      + public_dns           = (known after apply)
      + public_ip            = (known after apply)
      + public_ipv4_pool     = (known after apply)
      + tags_all             = (known after apply)
      + vpc                  = true
    }

  # aws_internet_gateway.gw will be created
  + resource "aws_internet_gateway" "gw" {
      + arn      = (known after apply)
      + id       = (known after apply)
      + owner_id = (known after apply)
      + tags     = {
          + "Name" = "zomato-gw"
        }
      + tags_all = {
          + "Name" = "zomato-gw"
        }
      + vpc_id   = (known after apply)
    }

  # aws_nat_gateway.natgw will be created
  + resource "aws_nat_gateway" "natgw" {
      + allocation_id        = (known after apply)
      + connectivity_type    = "public"
      + id                   = (known after apply)
      + network_interface_id = (known after apply)
      + private_ip           = (known after apply)
      + public_ip            = (known after apply)
      + subnet_id            = (known after apply)
      + tags                 = {
          + "Name" = "zomato-nat-gw"
        }
      + tags_all             = {
          + "Name" = "zomato-nat-gw"
        }
    }

  # aws_route_table.privrtbl will be created
  + resource "aws_route_table" "privrtbl" {
      + arn              = (known after apply)
      + id               = (known after apply)
      + owner_id         = (known after apply)
      + propagating_vgws = (known after apply)
      + route            = [
          + {
              + carrier_gateway_id         = ""
              + cidr_block                 = "0.0.0.0/0"
              + destination_prefix_list_id = ""
              + egress_only_gateway_id     = ""
              + gateway_id                 = (known after apply)
              + instance_id                = ""
              + ipv6_cidr_block            = ""
              + local_gateway_id           = ""
              + nat_gateway_id             = ""
              + network_interface_id       = ""
              + transit_gateway_id         = ""
              + vpc_endpoint_id            = ""
              + vpc_peering_connection_id  = ""
            },
        ]
      + tags             = {
          + "Name" = "zomato-privrtbl"
        }
      + tags_all         = {
          + "Name" = "zomato-privrtbl"
        }
      + vpc_id           = (known after apply)
    }

  # aws_route_table.pubrtbl will be created
  + resource "aws_route_table" "pubrtbl" {
      + arn              = (known after apply)
      + id               = (known after apply)
      + owner_id         = (known after apply)
      + propagating_vgws = (known after apply)
      + route            = [
          + {
              + carrier_gateway_id         = ""
              + cidr_block                 = "0.0.0.0/0"
              + destination_prefix_list_id = ""
              + egress_only_gateway_id     = ""
              + gateway_id                 = (known after apply)
              + instance_id                = ""
              + ipv6_cidr_block            = ""
              + local_gateway_id           = ""
              + nat_gateway_id             = ""
              + network_interface_id       = ""
              + transit_gateway_id         = ""
              + vpc_endpoint_id            = ""
              + vpc_peering_connection_id  = ""
            },
        ]
      + tags             = {
          + "Name" = "zomato-pubrtbl"
        }
      + tags_all         = {
          + "Name" = "zomato-pubrtbl"
        }
      + vpc_id           = (known after apply)
    }

  # aws_route_table_association.private01 will be created
  + resource "aws_route_table_association" "private01" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.private02 will be created
  + resource "aws_route_table_association" "private02" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.private03 will be created
  + resource "aws_route_table_association" "private03" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.public01 will be created
  + resource "aws_route_table_association" "public01" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.public02 will be created
  + resource "aws_route_table_association" "public02" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.public03 will be created
  + resource "aws_route_table_association" "public03" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_subnet.private01 will be created
  + resource "aws_subnet" "private01" {
      + arn                             = (known after apply)
      + assign_ipv6_address_on_creation = false
      + availability_zone               = "ap-south-1a"
      + availability_zone_id            = (known after apply)
      + cidr_block                      = "172.16.96.0/19"
      + id                              = (known after apply)
      + ipv6_cidr_block_association_id  = (known after apply)
      + map_public_ip_on_launch         = false
      + owner_id                        = (known after apply)
      + tags                            = {
          + "Name" = "zomato-private01"
        }
      + tags_all                        = {
          + "Name" = "zomato-private01"
        }
      + vpc_id                          = (known after apply)
    }

  # aws_subnet.private02 will be created
  + resource "aws_subnet" "private02" {
      + arn                             = (known after apply)
      + assign_ipv6_address_on_creation = false
      + availability_zone               = "ap-south-1b"
      + availability_zone_id            = (known after apply)
      + cidr_block                      = "172.16.128.0/19"
      + id                              = (known after apply)
      + ipv6_cidr_block_association_id  = (known after apply)
      + map_public_ip_on_launch         = false
      + owner_id                        = (known after apply)
      + tags                            = {
          + "Name" = "zomato-private02"
        }
      + tags_all                        = {
          + "Name" = "zomato-private02"
        }
      + vpc_id                          = (known after apply)
    }

  # aws_subnet.private03 will be created
  + resource "aws_subnet" "private03" {
      + arn                             = (known after apply)
      + assign_ipv6_address_on_creation = false
      + availability_zone               = "ap-south-1c"
      + availability_zone_id            = (known after apply)
      + cidr_block                      = "172.16.160.0/19"
      + id                              = (known after apply)
      + ipv6_cidr_block_association_id  = (known after apply)
      + map_public_ip_on_launch         = false
      + owner_id                        = (known after apply)
      + tags                            = {
          + "Name" = "zomato-private03"
        }
      + tags_all                        = {
          + "Name" = "zomato-private03"
        }
      + vpc_id                          = (known after apply)
    }

  # aws_subnet.public01 will be created
  + resource "aws_subnet" "public01" {
      + arn                             = (known after apply)
      + assign_ipv6_address_on_creation = false
      + availability_zone               = "ap-south-1a"
      + availability_zone_id            = (known after apply)
      + cidr_block                      = "172.16.0.0/19"
      + id                              = (known after apply)
      + ipv6_cidr_block_association_id  = (known after apply)
      + map_public_ip_on_launch         = true
      + owner_id                        = (known after apply)
      + tags                            = {
          + "Name" = "zomato-public01"
        }
      + tags_all                        = {
          + "Name" = "zomato-public01"
        }
      + vpc_id                          = (known after apply)
    }

  # aws_subnet.public02 will be created
  + resource "aws_subnet" "public02" {
      + arn                             = (known after apply)
      + assign_ipv6_address_on_creation = false
      + availability_zone               = "ap-south-1b"
      + availability_zone_id            = (known after apply)
      + cidr_block                      = "172.16.32.0/19"
      + id                              = (known after apply)
      + ipv6_cidr_block_association_id  = (known after apply)
      + map_public_ip_on_launch         = true
      + owner_id                        = (known after apply)
      + tags                            = {
          + "Name" = "zomato-public02"
        }
      + tags_all                        = {
          + "Name" = "zomato-public02"
        }
      + vpc_id                          = (known after apply)
    }

  # aws_subnet.public03 will be created
  + resource "aws_subnet" "public03" {
      + arn                             = (known after apply)
      + assign_ipv6_address_on_creation = false
      + availability_zone               = "ap-south-1c"
      + availability_zone_id            = (known after apply)
      + cidr_block                      = "172.16.64.0/19"
      + id                              = (known after apply)
      + ipv6_cidr_block_association_id  = (known after apply)
      + map_public_ip_on_launch         = true
      + owner_id                        = (known after apply)
      + tags                            = {
          + "Name" = "zomato-public03"
        }
      + tags_all                        = {
          + "Name" = "zomato-public03"
        }
      + vpc_id                          = (known after apply)
    }

  # aws_vpc.vpc will be created
  + resource "aws_vpc" "vpc" {
      + arn                            = (known after apply)
      + cidr_block                     = "172.16.0.0/16"
      + default_network_acl_id         = (known after apply)
      + default_route_table_id         = (known after apply)
      + default_security_group_id      = (known after apply)
      + dhcp_options_id                = (known after apply)
      + enable_classiclink             = (known after apply)
      + enable_classiclink_dns_support = (known after apply)
      + enable_dns_hostnames           = true
      + enable_dns_support             = true
      + id                             = (known after apply)
      + instance_tenancy               = "default"
      + ipv6_association_id            = (known after apply)
      + ipv6_cidr_block                = (known after apply)
      + main_route_table_id            = (known after apply)
      + owner_id                       = (known after apply)
      + tags                           = {
          + "Name" = "zomato-vpc"
        }
      + tags_all                       = {
          + "Name" = "zomato-vpc"
        }
    }

Plan: 18 to add, 0 to change, 0 to destroy.

Do you want to perform these actions?
  Terraform will perform the actions described above.
  Only 'yes' will be accepted to approve.

  Enter a value: yes

aws_eip.eip: Creating...
aws_vpc.vpc: Creating...
aws_eip.eip: Creation complete after 0s [id=eipalloc-09ab7378f80122d98]
aws_vpc.vpc: Still creating... [10s elapsed]
aws_vpc.vpc: Creation complete after 13s [id=vpc-0f90ab37216386fa3]
aws_subnet.private03: Creating...
aws_subnet.private01: Creating...
aws_subnet.private02: Creating...
aws_subnet.public03: Creating...
aws_internet_gateway.gw: Creating...
aws_subnet.public02: Creating...
aws_subnet.public01: Creating...
aws_subnet.private01: Creation complete after 1s [id=subnet-0de41d4075e10a6ae]
aws_subnet.private03: Creation complete after 1s [id=subnet-0019f81887f680fa8]
aws_subnet.private02: Creation complete after 1s [id=subnet-0f4d7c6805aa4d043]
aws_internet_gateway.gw: Creation complete after 1s [id=igw-01686161fddcee707]
aws_route_table.pubrtbl: Creating...
aws_route_table.pubrtbl: Creation complete after 2s [id=rtb-0f569c1d0e8716303]
aws_subnet.public03: Still creating... [10s elapsed]
aws_subnet.public02: Still creating... [10s elapsed]
aws_subnet.public01: Still creating... [10s elapsed]
aws_subnet.public02: Creation complete after 12s [id=subnet-0655798398f71ffc0]
aws_route_table_association.public02: Creating...
aws_subnet.public01: Creation complete after 12s [id=subnet-054b9870688af0423]
aws_subnet.public03: Creation complete after 12s [id=subnet-056eacaf428562096]
aws_route_table_association.public01: Creating...
aws_route_table_association.public03: Creating...
aws_nat_gateway.natgw: Creating...
aws_route_table_association.public01: Creation complete after 1s [id=rtbassoc-0087356b7057a3829]
aws_route_table_association.public02: Creation complete after 1s [id=rtbassoc-0e9d8a731ead44daf]
aws_route_table_association.public03: Creation complete after 1s [id=rtbassoc-06c6dd40a583c9fd4]
aws_nat_gateway.natgw: Still creating... [10s elapsed]
aws_nat_gateway.natgw: Still creating... [20s elapsed]
aws_nat_gateway.natgw: Still creating... [30s elapsed]
aws_nat_gateway.natgw: Still creating... [40s elapsed]
aws_nat_gateway.natgw: Still creating... [50s elapsed]
aws_nat_gateway.natgw: Still creating... [1m0s elapsed]
aws_nat_gateway.natgw: Still creating... [1m10s elapsed]
aws_nat_gateway.natgw: Still creating... [1m20s elapsed]
aws_nat_gateway.natgw: Still creating... [1m30s elapsed]
aws_nat_gateway.natgw: Creation complete after 1m37s [id=nat-0c1022fd2ac7176a7]
aws_route_table.privrtbl: Creating...
aws_route_table.privrtbl: Creation complete after 2s [id=rtb-046558f0ab78bd4c2]
aws_route_table_association.private03: Creating...
aws_route_table_association.private02: Creating...
aws_route_table_association.private01: Creating...
aws_route_table_association.private03: Creation complete after 1s [id=rtbassoc-004ca8f013213d8e6]
aws_route_table_association.private01: Creation complete after 1s [id=rtbassoc-0d620e6d16db5939a]
aws_route_table_association.private02: Creation complete after 1s [id=rtbassoc-08465779bee059086]

Apply complete! Resources: 18 added, 0 changed, 0 destroyed.

```
