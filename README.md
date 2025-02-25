[![Build Status](https://jenkins-terraform.mesosphere.com/service/dcos-terraform-jenkins/buildStatus/icon?job=dcos-terraform%2Fterraform-azurerm-instance%2Fsupport%252F0.2.x)](https://jenkins-terraform.mesosphere.com/service/dcos-terraform-jenkins/job/dcos-terraform/job/terraform-azurerm-instance/job/support%252F0.2.x/)

Azure Instance
============
The module creates AzureRM virtual machine instances

EXAMPLE
-------

```hcl
module "dcos-master-instances" {
  source  = "dcos-terraform/instance/azurerm"
  version = "~> 0.2.0"

  num                          = "${var.num}"
  location                     = "${var.location}"
  dcos_instance_os             = "${var.dcos_instance_os}"
  ssh_private_key_filename     = "${var.ssh_private_key_filename}"
  image                        = "${var.image}"
  resource_group_name          = "${var.resource_group_name}"
  ...
}
```

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| cluster\_name | Name of the DC/OS cluster | string | n/a | yes |
| dcos\_instance\_os | Operating system to use. Instead of using your own AMI you could use a provided OS. | string | n/a | yes |
| disk\_size | Disk Size in GB | string | n/a | yes |
| location | Azure Region | string | n/a | yes |
| name\_prefix | Name Prefix | string | n/a | yes |
| num | How many instances should be created | string | n/a | yes |
| resource\_group\_name | Name of the azure resource group | string | n/a | yes |
| subnet\_id | Subnet ID | string | n/a | yes |
| vm\_size | Azure virtual machine size | string | n/a | yes |
| admin\_username | SSH User | string | `""` | no |
| avset\_platform\_fault\_domain\_count | Availability set platform fault domain count, differs from location to location | string | `"3"` | no |
| custom\_data | User data to be used on these instances (cloud-init) | string | `""` | no |
| disk\_type | Disk Type to Leverage | string | `"Standard_LRS"` | no |
| hostname\_format | Format the hostname inputs are index+1, region, cluster_name | string | `"instance-%[1]d-%[2]s"` | no |
| image | Source image to boot from | map | `<map>` | no |
| network\_security\_group\_id | Security Group Id | string | `""` | no |
| private\_backend\_address\_pool | Private backend address pool | list | `<list>` | no |
| public\_backend\_address\_pool | Public backend address pool | list | `<list>` | no |
| public\_ssh\_key | SSH Public Key | string | `""` | no |
| ssh\_private\_key\_filename | Path to the SSH private key | string | `"/dev/null"` | no |
| tags | Add custom tags to all resources | map | `<map>` | no |

## Outputs

| Name | Description |
|------|-------------|
| admin\_username | SSH User |
| instance\_nic\_ids | List of instance nic ids created by this module |
| private\_ips | List of private ip addresses created by this module |
| public\_ips | List of public ip addresses created by this module |

