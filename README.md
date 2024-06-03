# Deploy from Terraform to Azure Portal
# Prerequisites
  Azure Subscription: Ensure you have an active Azure subscription.
  Terraform: Install Terraform on our local machine. 
  Azure CLI: Install Azure CLI on our local machine. 
  Visual Studio Code on our local machine.
#  Configure Azure Provider
Ensure you are logged in to your Azure account via Azure CLI/ VS code.
# Create a Terraform Configuration File
Create a new file named main.tf,provider.tf files and add the following configuration.
# Create a Terraform configuration File
Create a new file eg.,vm-1.tf file and add the following configuration.
# written a code by using terraform to deploy in azure
 1.Creates an Azure Resource Group named "resa" in the "West Europe" region.
 2.Creates a Virtual Network  named "azure-network" in the resource group "resa" with an address space of "10.0.0.0/16".
 3.Creates a subnet named "internal" within the "azure-network" VNet, with an address prefix of "10.0.2.0/24".
 4.Creates a Windows VM scale set named "example-vmss" in the resource group "resa" with the following properties:
   sku: Specifies the VM size as "Standard_F2".
   instances: Sets the initial number of instances to 2.
   admin_password and admin_username: Sets the admin credentials.
   computer_name_prefix: Sets the prefix for VM names.
   source_image_reference: Specifies the image used to create VMs (Windows Server 2016 Datacenter Core).
   os_disk: Configures the OS disk with standard storage and read/write caching.
   network_interface: Configures the network interface with a primary IP configuration linked to the "internal" subnet.
# azurerm_monitor_autoscale_setting: Configures autoscaling for the VM scale set "example-vmss" with the following settings:
  name: Sets the name of the autoscale setting to "first-autoscale".
  resource_group_name: Links the autoscale setting to the resource group "resa".
  location: Sets the location to "West Europe".
  target_resource_id: Specifies the target VM scale set.
  profile: Defines the autoscaling profile with the following properties.
  capacity: Sets the minimum, maximum, and default number of instances.
  rule: Defines scaling rules based on CPU usage metrics.
  metric_trigger: Specifies the metric (CPU percentage) and conditions for scaling.
  scale_action: which Defines the scaling action (increase or decrease instance count) and cooldown period.
# Configure Azure CLI- az login
# configure by suing terraform commands
1.terraform init
2.terraform validate
3.terraform plan
4.terraform apply
# below is the link provided to view which i have deployed in portal by using terraform.
https://portal.azure.com/#@devimounika2196gmail.onmicrosoft.com/resource/subscriptions/aae6c661-a30b-4862-8204-cbb56fb51276/resourceGroups/example-resources/providers/Microsoft.Compute/virtualMachineScaleSets/example-vmss/overview
# To deploy from terraform to azure by using YAML Script that provided in below link.
https://github.com/Mounikadchitti/Terraform/blob/main/.github/workflows/terraform-1.yaml.
  
  
