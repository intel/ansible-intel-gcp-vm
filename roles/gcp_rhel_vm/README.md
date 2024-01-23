<p align="center">
  <img src="https://github.com/intel/terraform-intel-gcp-vm/blob/main/images/logo-classicblue-800px.png?raw=true" alt="Intel Logo" width="250"/>
</p>

# Intel Cloud Optimization Modules for Terraform

© Copyright 2022, Intel Corporation

## Intel Red Hat Enterprise Linux GCP VM Example

This module creates a Red Hat Enterprise Linux (RHEL) VM on the Intel Sapphire Rapids CPU. The virtual machine is created on an Intel Sapphire Rapids c3-standard-4 by default.

Update the project with a project id in GCP. It is located on the variables.tf file under this example folder for "GCP-Linux-VM".

For the list of publicly available images for compute engines see https://cloud.google.com/compute/docs/images OR run gcloud compute images list --project gce-uefi-images to see the name, project, family and status easily in the CLI


## Installation of `gcp_rhel_vm` role
### Below are ways to install and use it:
1. **Case 1:-** Install collection using Ansible Galaxy (Use as third party collection, installed in default location), Use below command to installed collection
    ```commandline
        ansible-galaxy  collection install <intel.ansible-intel-gcp-vm>
    ```
   
2. **Case 2:-** Install collection using Ansible Galaxy (Installed in given location), Use below command to installed collection
   
    1.
       ```commandline
       ansible-galaxy  collection install -p <local path> <intel.ansible-intel-gcp-vm>
       ```
       Note: collection will download collection, you can remove as per need

   2. Download source and Copy role directory to your Ansible  boilerplate  from GitHub (Used to extended behavior of role)  
       ```commandline
       git clone https://github.com/OTCShare2/ansible-intel-gcp-vm.git
       cd ansible-intel-gcp-vm
       cp -r role/gcp_rhel_vm on /<your project path>/
       ``` 

Requirements
------------
| Name                                                                                            | Version    |
|-------------------------------------------------------------------------------------------------|------------|
| <a name="requirement_terraform"></a> [Terraform](#requirement\_terraform)                       | =1.5.7     |
| <a name="requirement_google_cloud_cli"></a> [Google Cloud CLI](#requirement\_google_cloud_cli)  | ~> 455.0.0 |
| <a name="requirement_random"></a> [Random](#requirement\_random)                                | ~>3.4.3    |
| <a name="requirement_ansible_core"></a> [Ansible Core](#requirement\_ansible\_core)             | ~>2.14.2   |
| <a name="requirement_ansible"></a> [Ansible](#requirement\_ansible)                             | ~>7.2.0-1  |
| <a name="requirement_requests"></a> [Requests](#requirement\_requests)                          | ~> 2.18.4  |
| <a name="requirement_google_auth"></a> [Google-auth](#requirement\_google_auth)                 | ~>1.3.0    |
| <a name="requirement_cryptography"></a> [Cryptography](#requirement\_cryptography)              | ~>41.0.5   |

1. Install requirements using `requirements.txt` and `requirements.yml`, Use below command:
    ```bash
    pip3 install -r requirements.txt
    ansible-galaxy install -r requirements.yml
    ```
2. Above role requires `Terraform` as we are executing terraform module [terraform-intel-gcp-vm](<https://github.com/intel/terraform-intel-gcp-vm/tree/main>) using Ansible module called [community.general.terraform](<https://docs.ansible.com/ansible/latest/collections/community/general/terraform_module.html>)


## Usage

> [!WARNING]  
> Once a VM is created, refrain from updating its name. Any alterations to the name will result in the creation of a new VM. 

Use playbook to run intel_gcp_rhel_vm as below
```yml
---
- name: Run gcp_rhel_vm role
  hosts: localhost
  tasks:
    - name: Running a role gcp rhel vm
      ansible.builtin.import_role:
        name: gcp_rhel_vm
      vars:
        project: "<project>"
        gcp_rhel_vm_state: present
```
Use below Command:
```commandline
ansible-playbook intel_gcp_rhel_vm.yml
```

## Run Ansible with dfferent state
#### State - present (terraform apply)
```yaml
---
- name: Run gcp_rhel_vm role
  hosts: localhost
  tasks:
    - name: Running a role gcp rhel vm
      ansible.builtin.import_role:
        name: gcp_rhel_vm
      vars:
        project: "<project>"
        gcp_rhel_vm_state: present
```
Use below Command:
```commandline
ansible-playbook intel_gcp_rhel_vm.yml
```

#### State - absent (terraform destroy)
```yaml
---
- name: Run gcp_rhel_vm role
  hosts: localhost
  tasks:
    - name: Running a role gcp rhel vm
      ansible.builtin.import_role:
        name: gcp_rhel_vm
      vars:
        project: "<project>"
        gcp_rhel_vm_state: absent
```
Use below Command:
```commandline
ansible-playbook intel_gcp_rhel_vm.yml
```

### Terraform Modules
| Name                                                                                       |
|--------------------------------------------------------------------------------------------|
| [terraform-intel-gcp-vm](<https://github.com/intel/terraform-intel-gcp-vm/blob/main>)      |

# Ansible

## Module State Inputs

| Name                                                                                   | Description                                                                                  | Type     | Default   | Required |
|----------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------|----------|-----------|:--------:|
| <a name="gcp_rhel_vm_state"></a> [gcp_rhel_vm_state](#input\_gcp_rhel_vm_state) | It specifices vm state of given stage, choies: "planned", "present" ← (default), "absent" | `string` | `present` | no |


## GCP VM Exposed Inputs

| Name                                                                                           | Description                                                                                                                                                                                                                                                                                                      | Type                                                                                                                                                                             | Default                                                                | Required |
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|:--------:|
| <a name="input_project0"></a> [project](#input\_project0)                                      | The ID of the project in which the resource resides.                                                                                                                                                                                                                                                             | `string`                                                                                                                                                                         | ``                                                                     |   yes    |
| <a name="input_gcp_rhel_vm_name"></a> [gcp_rhel_vm_name](#input\_gcp_rhel_vm_name)             | A unique name for the resource, required by GCE. Changing this forces a new resource to be created.                                                                                                                                                                                                              | `string`                                                                                                                                                                         | `vm1`                                                                  |    no    |
| <a name="input_boot_image_family0"></a> [boot\_image\_family](#input\_boot\_image\_family0)    | The image from which to initialize this disk                                                                                                                                                                                                                                                                     | `string`                                                                                                                                                                         | `rhel-8`                                                               |    no    |
| <a name="input_boot_image_project0"></a> [boot\_image\_project](#input\_boot\_image\_project0) | The ID of the project in which the source image resides.                                                                                                                                                                                                                                                         | `string`                                                                                                                                                                         | `rhel-cloud`                                                           |    no    |
| <a name="input_access_config0"></a> [access\_config](#input\_access\_config0)                  | Access configurations, i.e. IPs via which this instance can be accessed via the Internet. Omit to ensure that the instance is not accessible from the Internet. If omitted, ssh provisioners will not work unless Terraform can send traffic to the instance's network. This can be represented as multiple maps | <pre>list(object({<br>    nat_ip                 = optional(string, null)<br>    public_ptr_domain_name = optional(string)<br>    network_tier = optional(string)<br>  }))</pre> | `[{"nat_ip":"","public_ptr_domain_name":"","network_tier":"PREMIUM"}]` |    no    |
| <a name="input_zone0"></a> [zone](#input\_zone0)                                               | Name the zone that machine should be created in. if it not provided, the provider zone is used                                                                                                                                                                                                                   | `string`                                                                                                                                                                         | `us-central1-a`                                                        |    no    |

## VM Terraform Extended Inputs
 Below Input variables can be used to extend variables in role, Add or update variable in vars/main.yml file
### Usage

roles/gcp_rhel_vm/vars/main.yml

```yaml
hostname: "gcp.vm.04122023"
```

roles/gcp_rhel_vm/tasks/rhel_vm.yml
```yaml
---
- name: Create GCP Linux VM with Rhel image
  community.general.terraform:
    project_path: '{{ gcp_vm_tf_module_path }}'
    state: '{{ gcp_rhel_vm_state }}'
    force_init: true
    complex_vars: true
    variables:
      project: '{{ project }}'
      boot_image_project: '{{ boot_image_project }}'
      boot_image_family: '{{ boot_image_family }}'
      name: '{{ gcp_rhel_vm_name }}'
      access_config: '{{ access_config }}'
      hostname: '{{ hostname }}'
  register: gcp_vm_output
```

Use `hostname` in playbook
```yaml
---
- name: Run gcp_rhel_vm role
  hosts: localhost
  tasks:
    - name: Running a role gcp rhel vm
      ansible.builtin.import_role:
        name: gcp_rhel_vm
      vars:
        project: "<project>"
        gcp_rhel_vm_state: present
        hostname: <hostname>
```

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_access_config"></a> [access\_config](#input\_access\_config) | Access configurations, i.e. IPs via which this instance can be accessed via the Internet. Omit to ensure that the instance is not accessible from the Internet. If omitted, ssh provisioners will not work unless Terraform can send traffic to the instance's network. This can be represented as multiple maps | <pre>list(object({<br>    nat_ip                 = optional(string, null)<br>    public_ptr_domain_name = optional(string)<br>    network_tier           = optional(string)<br>  }))</pre> | `[]` | no |
| <a name="input_allow_stopping_for_update"></a> [allow\_stopping\_for\_update](#input\_allow\_stopping\_for\_update) | If true, allows Terraform to stop the instance to update its properties | `bool` | `null` | no |
| <a name="input_automatic_restart"></a> [automatic\_restart](#input\_automatic\_restart) | Specifies if the instance should be restarted if it was terminated by Compute Engine (not a user). | `bool` | `true` | no |
| <a name="input_boot_disk_auto_delete"></a> [boot\_disk\_auto\_delete](#input\_boot\_disk\_auto\_delete) | Whether the disk will be auto-deleted when the instance is deleted. | `bool` | `true` | no |
| <a name="input_boot_disk_byo_encryption_key"></a> [boot\_disk\_byo\_encryption\_key](#input\_boot\_disk\_byo\_encryption\_key) | A 256-bit [customer-supplied encryption key] (https://cloud.google.com/compute/docs/disks/customer-supplied-encryption), encoded in RFC 4648 base64 to encrypt this disk. | `string` | `null` | no |
| <a name="input_boot_disk_labels"></a> [boot\_disk\_labels](#input\_boot\_disk\_labels) | A set of key/value label pairs assigned to the disk. This field is only applicable for persistent disks. | `map(string)` | `{}` | no |
| <a name="input_boot_disk_mode"></a> [boot\_disk\_mode](#input\_boot\_disk\_mode) | The mode in which to attach this disk, either READ\_WRITE or READ\_ONLY. | `string` | `"READ_WRITE"` | no |
| <a name="input_boot_disk_size"></a> [boot\_disk\_size](#input\_boot\_disk\_size) | Size of the OS disk | `number` | `100` | no |
| <a name="input_boot_disk_source"></a> [boot\_disk\_source](#input\_boot\_disk\_source) | The name or self\_link of the existing disk (such as those managed by google\_compute\_disk) or disk image. | `string` | `null` | no |
| <a name="input_boot_disk_type"></a> [boot\_disk\_type](#input\_boot\_disk\_type) | Disk type associated with the OS disk. Values can be either pd-ssd, local-ssd, or pd-standard | `string` | `"pd-ssd"` | no |
| <a name="input_boot_image_family"></a> [boot\_image\_family](#input\_boot\_image\_family) | The image from which to initialize this disk | `string` | `"ubuntu-2204-lts"` | no |
| <a name="input_boot_image_project"></a> [boot\_image\_project](#input\_boot\_image\_project) | The ID of the project in which the source image resides. | `string` | `"ubuntu-os-cloud"` | no |
| <a name="input_can_ip_forward"></a> [can\_ip\_forward](#input\_can\_ip\_forward) | Conditional that allows sending and receiving of packets with non-matching source or destination IPs. | `bool` | `false` | no |
| <a name="input_deletion_protection"></a> [deletion\_protection](#input\_deletion\_protection) | Enable deletion protection on this instance | `bool` | `false` | no |
| <a name="input_description"></a> [description](#input\_description) | A brief description of this resource | `string` | `"Intel accelerated virtual machine."` | no |
| <a name="input_desired_status"></a> [desired\_status](#input\_desired\_status) | Desired status of the instance. | `string` | `"RUNNING"` | no |
| <a name="input_enable_integrity_monitoring"></a> [enable\_integrity\_monitoring](#input\_enable\_integrity\_monitoring) | Compare the most recent boot measurements to the integrity policy baseline and return a pair of pass/fail results depending on whether they match or not. | `bool` | `true` | no |
| <a name="input_enable_nested_virtualization"></a> [enable\_nested\_virtualization](#input\_enable\_nested\_virtualization) | Boolean that specifies if nested virtualization should be enabled or disabled on the instance. | `bool` | `false` | no |
| <a name="input_enable_secure_boot"></a> [enable\_secure\_boot](#input\_enable\_secure\_boot) | Verify the digital signature of all boot components, and halt the boot process if signature verification fails. | `bool` | `false` | no |
| <a name="input_enable_vtpm"></a> [enable\_vtpm](#input\_enable\_vtpm) | Use a virtualized trusted platform module, which is a specialized computer chip you can use to encrypt objects like keys and certificates. | `bool` | `true` | no |
| <a name="input_hostname"></a> [hostname](#input\_hostname) | A custom hostname for the instance. Must be a fully qualified DNS name and RFC-1035-valid | `string` | `null` | no |
| <a name="input_ipv6_access_config"></a> [ipv6\_access\_config](#input\_ipv6\_access\_config) | Access configurations, i.e. IPs via which this instance can be accessed via the Internet. Omit to ensure that the instance is not accessible from the Internet. If omitted, ssh provisioners will not work unless Terraform can send traffic to the instance's network. This can be represented as multiple maps | <pre>list(object({<br>    public_ptr_domain_name = optional(string, null)<br>    network_tier           = optional(string, null)<br>  }))</pre> | `[]` | no |
| <a name="input_machine_type"></a> [machine\_type](#input\_machine\_type) | The machine type to create | `string` | `"c3-standard-4"` | no |
| <a name="input_name"></a> [name](#input\_name) | A unique name for the resource, required by GCE. Changing this forces a new resource to be created. | `string` | n/a | yes |
| <a name="input_network"></a> [network](#input\_network) | The name or self\_link of the network to attach this interface to. | `string` | `"default"` | no |
| <a name="input_network_ip"></a> [network\_ip](#input\_network\_ip) | The private IP address to assign to the instance. If empty, the address will be automatically assigned. | `string` | `""` | no |
| <a name="input_nic_type"></a> [nic\_type](#input\_nic\_type) | The type of vNIC to be used on this compute instance. | `string` | `null` | no |
| <a name="input_on_host_maintenance"></a> [on\_host\_maintenance](#input\_on\_host\_maintenance) | Describes maintenance behavior for the instance. Can be MIGRATE or TERMINATE | `string` | `"MIGRATE"` | no |
| <a name="input_preemptible"></a> [preemptible](#input\_preemptible) | Specifies if the instance is preemptible. If this field is set to true, then automatic\_restart must be set to false. | `bool` | `false` | no |
| <a name="input_project"></a> [project](#input\_project) | The ID of the project in which the resource resides. | `string` | `""` | no |
| <a name="input_provisioning_model"></a> [provisioning\_model](#input\_provisioning\_model) | Describe the type of preemptible VM. This field accepts the value STANDARD or SPOT | `string` | `"STANDARD"` | no |
| <a name="input_service_account"></a> [service\_account](#input\_service\_account) | Service account and scopes that will be associated with the GCE instance. | <pre>object({<br>    service_email = optional(string, null)<br>    scopes        = optional(set(string), [])<br>  })</pre> | `{}` | no |
| <a name="input_stack_type"></a> [stack\_type](#input\_stack\_type) | he stack type for this network interface to identify whether the IPv6 feature is enabled or not. | `string` | `"IPV4_ONLY"` | no |
| <a name="input_subnetwork"></a> [subnetwork](#input\_subnetwork) | The name or self\_link of the subnetwork to attach this interface to. Either network or subnetwork must be provided. | `string` | `null` | no |
| <a name="input_subnetwork_project"></a> [subnetwork\_project](#input\_subnetwork\_project) | The project in which the subnetwork belongs. If the subnetwork is a name and this field is not provided, the provider project is used. | `string` | `null` | no |
| <a name="input_tags"></a> [tags](#input\_tags) | A list of network tags to attach to the instance | `list(string)` | `[]` | no |
| <a name="input_termination_action"></a> [termination\_action](#input\_termination\_action) | The action that will be applied to the instance when it is terminated. | `string` | `null` | no |
| <a name="input_threads_per_core"></a> [threads\_per\_core](#input\_threads\_per\_core) | The action that will be applied to the instance when it is terminated. | `number` | `null` | no |
| <a name="input_user_data"></a> [user\_data](#input\_user\_data) | User data to be placed on the instance. Used to place cloud-init on VMs | `string` | `null` | no |
| <a name="input_visible_core_count"></a> [visible\_core\_count](#input\_visible\_core\_count) | The number of physical cores to expose to an instance. | `number` | `null` | no |
| <a name="input_zone"></a> [zone](#input\_zone) | The zone that the machine should be created in. If it is not provided, the provider zone is used. | `string` | `null` | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_boot_disk_size"></a> [boot\_disk\_size](#output\_boot\_disk\_size) | Size of the boot disk of the instance |
| <a name="output_cpu_platform"></a> [cpu\_platform](#output\_cpu\_platform) | The CPU platform of the VM instance |
| <a name="output_current_status"></a> [current\_status](#output\_current\_status) | Current status of the VM instance |
| <a name="output_id"></a> [id](#output\_id) | An identifier for the resource |
| <a name="output_instance_id"></a> [instance\_id](#output\_instance\_id) | The server-assigned unique identifier of this instance |
| <a name="output_machine_type"></a> [machine\_type](#output\_machine\_type) | Type of the machine created |
| <a name="output_min_cpu_platform"></a> [min\_cpu\_platform](#output\_min\_cpu\_platform) | Minimum CPU platform for the VM instance |
| <a name="output_name"></a> [name](#output\_name) | Unique name of the instance created |
| <a name="output_private_ip"></a> [private\_ip](#output\_private\_ip) | Internal IP address of the instance |
| <a name="output_public_ip"></a> [public\_ip](#output\_public\_ip) | Public IP address of the instance |
| <a name="output_self_link"></a> [self\_link](#output\_self\_link) | The URI of the created resource |
<!-- END_TF_DOCS -->
