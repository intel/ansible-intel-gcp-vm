<p align="center">
  <img src="https://github.com/intel/terraform-intel-gcp-vm/blob/main/images/logo-classicblue-800px.png?raw=true" alt="Intel Logo" width="250"/>
</p>

## Intel® Optimized Cloud Modules for Ansible

© Copyright 2024, Intel Corporation

## GCP VM module
This module provides the functionality to ensure that you are utilizing Intel's latest generation processor in the creation of a virtual machine in GCP.

### Explained Ansible GCP VM collection
This collection included 3 roles and 4 playbooks.

**Role**:- Ansible roles are a way to reuse and organize your Ansible code. They are self-contained units that contain all the files and configuration needed to automate a specific task.
Roles are defined using a directory structure with specific directories for tasks, variables, files, templates, and other artifacts. This structure makes it easy to find and reuse code, and it also makes it easy to extend behaviour of roles.

To use a role in an Ansible playbook, you simply need to list it in the roles section of the playbook. Ansible will then automatically load the role and execute its tasks.

For this module, there are 3 roles.
1. <a name="gcp_linux_fastchat_simple"> gcp_linux_fastchat_simple</a> It creates GCP C3 4th Gen Xeon(code named Sapphire Rapids) & Intel® Optimized Cloud Recipe for FastChat
2. <a name="gcp_linux_stable_diffusion"> gcp_linux_stable_diffusion</a> It creates GCP C3 4th Gen Xeon(code named Sapphire Rapids) & Intel® Optimized Cloud Recipe for Stable Diffusion
3. <a name="gcp_rhel_vm"> gcp_rhel_vm</a> It creates a Red Hat Enterprise Linux (RHEL) VM on the Intel Sapphire Rapids CPU with  an Intel Sapphire Rapids c3-standard-4.

**
****Playbook**:- An Ansible playbook is a YAML file that describes the tasks, are composed of a series of plays, which are groups of tasks that are executed in a specific order. Each play defines a set of tasks that should be executed on a specific group of hosts.
         Playbooks can also include variables, which can be used to store data that is used by the tasks. This makes it easy to reuse playbooks for different environments and configurations.
         for this module.
For this module, there are 4 playbooks:
1. Playbook **intel_gcp_vm.yml** - Used to create an GCP VM, it uses Terraform module **terraform-intel-gcp-vm** and being called by Ansible module community.general.terraform
2. Playbook **intel_gcp_linux_fastchat_simple.yml** - It executes role called [gcp_linux_fastchat_simple](#gcp_linux_fastchat_simple)
3. Playbook **intel_gcp_linux_stable_diffusion.yml** - It executes role called [gcp_linux_stable_diffusion](#gcp_linux_stable_diffusion)
4. Playbook **intel_gcp_rhel_vm.yml** - It executes role called [gcp_rhel_vm](#gcp_rhel_vm)

```bash
.
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
├── galaxy.yml
├── hosts
├── playbooks
│   ├── intel_gcp_linux_fastchat_simple.yml
│   ├── intel_gcp_linux_stable_diffusion.yml
│   └── intel_gcp_rhel_vm.yml
├── README.md
├── requirements.txt
├── requirements.yml
├── roles
│   ├── gcp_linux_fastchat_simple
│   │   ├── defaults
│   │   │   └── main.yml
│   │   ├── handlers
│   │   │   └── main.yml
│   │   ├── meta
│   │   │   └── main.yml
│   │   ├── README.md
│   │   ├── tasks
│   │   │   ├── cloud_init_config.yml
│   │   │   ├── download_tf_module.yml
│   │   │   ├── fastchat.yml
│   │   │   ├── fw_security.yml
│   │   │   ├── main.yml
│   │   │   └── read_tfstate.yml
│   │   ├── tests
│   │   │   ├── inventory
│   │   │   └── test.yml
│   │   └── vars
│   │       └── main.yml
│   ├── gcp_linux_stable_diffusion
│   │   ├── defaults
│   │   │   └── main.yml
│   │   ├── files
│   │   ├── handlers
│   │   │   └── main.yml
│   │   ├── meta
│   │   │   └── main.yml
│   │   ├── README.md
│   │   ├── tasks
│   │   │   ├── cloud_init_config.yml
│   │   │   ├── download_tf_module.yml
│   │   │   ├── fw_security.yml
│   │   │   ├── main.yml
│   │   │   ├── read_tfstate.yml
│   │   │   └── stable_diffusion.yml
│   │   ├── templates
│   │   ├── tests
│   │   │   ├── inventory
│   │   │   └── test.yml
│   │   └── vars
│   │       └── main.yml
│   └── gcp_rhel_vm
│       ├── defaults
│       │   └── main.yml
│       ├── files
│       ├── handlers
│       │   └── main.yml
│       ├── meta
│       │   └── main.yml
│       ├── README.md
│       ├── tasks
│       │   ├── download_tf_module.yml
│       │   ├── main.yml
│       │   ├── output.yml
│       │   └── rhel_vm.yml
│       ├── templates
│       ├── tests
│       │   ├── inventory
│       │   └── test.yml
│       └── vars
│           └── main.yml
└── security.md

```

Requirements
------------
| Name                                                                                           | Version    |
|------------------------------------------------------------------------------------------------|------------|
| <a name="requirement_terraform"></a> [Terraform](#requirement\_terraform)                      | =1.5.7     |
| <a name="requirement_google_cloud_cli"></a> [Google Cloud CLI](#requirement\_google_cloud_cli) | ~> 455.0.0 |
| <a name="requirement_random"></a> [Random](#requirement\_random)                               | ~>3.4.3    |
| <a name="requirement_ansible_core"></a> [Ansible Core](#requirement\_ansible\_core)            | ~>2.14.2   |
| <a name="requirement_ansible"></a> [Ansible](#requirement\_ansible)                            | ~>7.2.0-1  |
| <a name="requirement_requests"></a> [Requests](#requirement\_requests)                         | ~> 2.18.4  |
| <a name="requirement_google_auth"></a> [Google-auth](#requirement\_google_auth)                | ~>1.3.0   |
| <a name="requirement_cryptography"></a> [Cryptography](#requirement\_cryptography)             | ~>41.0.5   |

Note:
1. Install requirements using `requirements.txt` and `requirements.yml`, Use below command:
    ```bash
    pip3 install -r requirements.txt
    ansible-galaxy install -r requirements.yml
    ```
2. Above role requires `Terraform` as we are executing terraform module [terraform-intel-gcp-vm](<https://github.com/intel/terraform-intel-gcp-vm/tree/main>) using Ansible module called [community.general.terraform](<https://docs.ansible.com/ansible/latest/collections/community/general/terraform_module.html>)


## Installation of collection

### Below are ways to install and use it:

1. **Case 1:-** When user's needs can be met with the default configuration, and they want to install a collection
   from Ansible Galaxy to the default location (as a third-party collection), it is recommended to use the following command:
    ```commandline
        ansible-galaxy  collection install <intel.ansible-intel-gcp-vm>
    ```

2. **Case 2:-** When user's needs cannot be met with the default configuration, wants to extend/modify existing configuration and flow, they can install collection using Ansible Galaxy in user's define location.
   Use below approaches:

   1.
       ```commandline
       ansible-galaxy  collection install -p <local path> <intel.ansible-intel-gcp-vm>
       ```
       Note: collection will download collection, you can remove as per need.

   2. Download source and copy role directory to your Ansible boilerplate  from GitHub (used to extended behavior of role)  
       ```commandline
       git clone https://github.com/OTCShare2/ansible-intel-gcp-vm.git
       cd ansible-intel-gcp-vm
       cp -r role/gcp_linux_fastchat_simple /<your project path>/
       ```

## Authenticate GCP
1. Download and Install Google Cloud CLI: https://cloud.google.com/sdk/docs/install
2. GCP account access configured: https://registry.terraform.io/providers/hashicorp/google/latest/docs/guides/provider_reference.html#running-terraform-on-your-workstation


## Usage
Use [playbook](playbooks/intel_gcp_vm.yml) to execute Terraform module [terraform-intel-gcp-vm](<https://github.com/intel/terraform-intel-gcp-vm>) using Ansible module [community.general.terraform](<https://docs.ansible.com/ansible/latest/collections/community/general/terraform_module.html>) as below

```yml
- hosts: localhost
  vars:
    terraform_source: https://github.com/intel/terraform-intel-gcp-vm.git
  tasks:
    - set_fact:
        terraform_module_download_path: '/home/{{ansible_env.USER}}/terraform/main/intel_gcp_vm/'

    - name: Clone a github repository
      git:
        repo: '{{ terraform_source }}'
        dest: '{{ terraform_module_download_path }}'
        clone: yes
        update: yes
        version: main

    - name: GCP VM Module
      community.general.terraform:
        project_path: '{{ terraform_module_download_path }}'
        state: absent
        force_init: true
        complex_vars: true
        # for additional variables
        # https://github.com/intel/terraform-intel-gcp-vm/blob/main/variables.tf
        variables:
          name: gcp-vm-playbook
          project: "fluid-tuner-405104"
          boot_image_project: "ubuntu-os-cloud"
          boot_image_family: "ubuntu-2204-lts"
          zone: "us-central1-a"
          machine_type: "e2-micro"
          allow_stopping_for_update: true
      register: vm_output

    - debug:
        var: vm_output
```
Use below Command:
```commandline
ansible-playbook intel_gcp_vm.yml
```

## Run Ansible with Different State
#### State - planned (terraform plan)
```yaml
- name: GCP VM Module
  community.general.terraform:
    project_path: '{{ terraform_module_download_path }}'
    state: planned
    force_init: true
    complex_vars: true
    # for additional variables
    # https://github.com/intel/terraform-intel-gcp-vm/blob/main/variables.tf
    variables:
      name: gcp-vm-playbook
```

#### State - present (terraform apply)
```yaml
- name: GCP VM Module
  community.general.terraform:
    project_path: '{{ terraform_module_download_path }}'
    state: present
    force_init: true
    complex_vars: true
    # for additional variables
    # https://github.com/intel/terraform-intel-gcp-vm/blob/main/variables.tf
    variables:
      name: gcp-vm-playbook
```


#### State - absent (terraform destroy)
```yaml
- name: GCP VM Module
  community.general.terraform:
    project_path: '{{ terraform_module_download_path }}'
    state: absent
    force_init: true
    complex_vars: true
    # for additional variables
    # https://github.com/intel/terraform-intel-gcp-vm/blob/main/variables.tf
    variables:
      name: gcp-vm-playbook
```
## See roles folder for complete examples

| Role Name                                                                                                                  |
|----------------------------------------------------------------------------------------------------------------------------|
| [gcp_linux_fastchat_simple](https://github.com/OTCShare2/ansible-intel-gcp-vm/tree/main/roles/gcp_linux_fastchat_simple)   |
| [gcp_linux_stable_diffusion](https://github.com/OTCShare2/ansible-intel-gcp-vm/tree/main/roles/gcp_linux_stable_diffusion) |
| [gcp_rhel_vm](https://github.com/OTCShare2/ansible-intel-gcp-vm/tree/main/roles/gcp_rhel_vm)                               |


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