# terraform-gcp

## Create a VPC
### terraform code
```
resource "google_compute_network" "vpc_network" {
  name = "terraform-network"
}
```

### terraform apply
```
❯ terraform apply

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # google_compute_network.vpc_network will be created
  + resource "google_compute_network" "vpc_network" {
      + auto_create_subnetworks         = true
      + delete_default_routes_on_create = false
      + gateway_ipv4                    = (known after apply)
      + id                              = (known after apply)
      + ipv4_range                      = (known after apply)
      + name                            = "terraform-network"
      + project                         = (known after apply)
      + routing_mode                    = (known after apply)
      + self_link                       = (known after apply)
    }

Plan: 1 to add, 0 to change, 0 to destroy.

Do you want to perform these actions?
  Terraform will perform the actions described above.
  Only 'yes' will be accepted to approve.

  Enter a value: yes

google_compute_network.vpc_network: Creating...
google_compute_network.vpc_network: Still creating... [10s elapsed]
google_compute_network.vpc_network: Still creating... [20s elapsed]
google_compute_network.vpc_network: Still creating... [30s elapsed]
google_compute_network.vpc_network: Creation complete after 38s [id=projects/test-project-352904/global/networks/terraform-network]

Apply complete! Resources: 1 added, 0 changed, 0 destroyed.
```

### check terraform status
```
❯ terraform show
# google_compute_network.vpc_network:
resource "google_compute_network" "vpc_network" {
    auto_create_subnetworks         = true
    delete_default_routes_on_create = false
    id                              = "projects/test-project-352904/global/networks/terraform-network"
    name                            = "terraform-network"
    project                         = "test-project-352904"
    routing_mode                    = "REGIONAL"
    self_link                       = "https://www.googleapis.com/compute/v1/projects/test-project-352904/global/networks/terraform-network"
}
```

### check from GCP
```
❯ gcloud compute networks list
NAME               SUBNET_MODE  BGP_ROUTING_MODE  IPV4_RANGE  GATEWAY_IPV4
default            AUTO         REGIONAL
terraform-network  AUTO         REGIONAL
```