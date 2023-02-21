# terraform-test-tfcmodule
This is a test repository and it going to be used to test a TFC Module from the private registry of TFC

# Pre-requisites
- Terraform Cloud account
- Terraform

# How to use this repository

- Copy the repository
```shell
git clone git@github.com:dlavric/terraform-test-tfcmodule.git
```

- Go to the path of the repository
```shell
cd terraform-test-tfcmodule
```

- Open the terminal and login into TFC
```shell
terraform login
```

- Copy the token and paste it in your terminal and once the login is successful the following output can be seen
```shell
 Welcome to Terraform Cloud! 
```

- Initialize Terraform locally to download the module and other dependencies
```shell
terraform init

Initializing modules...
Downloading app.terraform.io/daniela-org/module/aws 1.0.1 for module...
- module in .terraform/modules/module
- module.daniela in .terraform/modules/module/module

Initializing the backend...

Initializing provider plugins...
- Finding latest version of hashicorp/null...
- Installing hashicorp/null v3.2.1...
- Installed hashicorp/null v3.2.1 (signed by HashiCorp)

Terraform has created a lock file .terraform.lock.hcl to record the provider
selections it made above. Include this file in your version control repository
so that Terraform can guarantee to make the same selections by default when
you run "terraform init" in the future.

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.
```

- Apply the code to test the module is working
```shell
terraform apply

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following
symbols:
  + create

Terraform will perform the following actions:

  # module.module.null_resource.daniela will be created
  + resource "null_resource" "daniela" {
      + id = (known after apply)
    }

  # module.module.module.daniela.null_resource.null will be created
  + resource "null_resource" "null" {
      + id = (known after apply)
    }

Plan: 2 to add, 0 to change, 0 to destroy.

Do you want to perform these actions?
  Terraform will perform the actions described above.
  Only 'yes' will be accepted to approve.

  Enter a value: yes

module.module.module.daniela.null_resource.null: Creating...
module.module.null_resource.daniela: Creating...
module.module.null_resource.daniela: Creation complete after 0s [id=1032640962496820422]
module.module.module.daniela.null_resource.null: Creation complete after 0s [id=1950173962350948689]

Apply complete! Resources: 2 added, 0 changed, 0 destroyed.
```

- Destroy the resources
```shell
terraform destroy
```