# terraform-gcp

### Create a VPC
```
terraform {
  required_providers {
    google = {
      source  = "hashicorp/google"
      version = "3.5.0"
    }
  }
}

provider "google" {
  credentials = file("test-project.json")

  project = "test-project-352904"
  region  = "us-central1"
  zone    = "us-central1-a"
}

resource "google_compute_network" "vpc_network" {
  name = "terraform-network"
}
```

### check terraform status
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

❯ gcloud compute networks list
NAME               SUBNET_MODE  BGP_ROUTING_MODE  IPV4_RANGE  GATEWAY_IPV4
default            AUTO         REGIONAL
terraform-network  AUTO         REGIONAL
