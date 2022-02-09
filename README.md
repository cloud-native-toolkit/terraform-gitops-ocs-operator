# OCS Module

This module will create GitOps deployment to deploy OpenShift Container Storage Operator into an OpenShift Cluster.



## Software dependencies

The module depends on the following software components:

### Command-line tools

- terraform - v15
- kubectl

### Terraform providers

- Helm provider >= 1.1.1 (provided by Terraform)

## Module dependencies

This module makes use of the output from other modules:

- GitOps Bootstrap - https://github.com/cloud-native-toolkit/terraform-util-gitops-bootstrap
- OCP Login - https://github.com/cloud-native-toolkit/terraform-ocp-login
- GitOps Namespace - https://github.com/cloud-native-toolkit/terraform-gitops-namespace

## Example usage

```hcl-terraform
module "ocs-operator" {
  source = "https://github.com/cloud-native-toolkit/terraform-gitops-ocs-operator.git"

  gitops_config = module.gitops.gitops_config
  git_credentials = module.gitops.git_credentials
  server_name = module.gitops.server_name
  namespace = module.gitops_namespace.name
  kubeseal_cert = module.gitops.sealed_secrets_cert
}

```
