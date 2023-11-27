<p align="center">
  <img src="https://github.com/intel/terraform-intel-aws-mysql/blob/main/images/logo-classicblue-800px.png?raw=true" alt="Intel Logo" width="250"/>
</p>

# Intel® Cloud Optimization Modules for Ansible

© Copyright 2023, Intel Corporation

## GCP C3 4th Gen Xeon(code named Sapphire Rapids) & Intel® Optimized Cloud Recipe for FastChat

This demo will showcase Large Language Model(LLM) CPU inference using 4th Gen Xeon Scalable Processors on GCP.

## gcp-linux-fastchat-simple Example

Configuration in this directory creates an  for gcp vm and creates a in the us-central1-a region. The instance is created on an Intel Icelake instance c3-standard-22 by default. The vm is pre-configured with google_compute_firewall within the vm that is optimized for Intel architecture. The goal of this module is to get you started with vm configured to run best on Intel architecture.

As you configure your application's environment, choose the configurations for your infrastructure that matches your application's requirements.

The MySQL Optimizations were based off [Intel Xeon Tunning guides](<https://www.intel.com/content/www/us/en/developer/articles/guide/open-source-database-tuning-guide-on-xeon-systems.html>)

## Installation of `gcp-linux-fastchat-simple` role
### Below are ways to `How to install and use it`
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
       cp -r role/gcp-linux-fastchat-simple on /<your project path>/
       ``` 

## Usage
Use playbook to run gcp_linux_fastchat_simple as below
```ansible
---
- name: Run gcp-linux-fastchat-simple role
  hosts: localhost
  tasks:
    - name: Running a role gcp-linux-fastchat-simple creation
      ansible.builtin.import_role:
        name: gcp-linux-fastchat-simple
      vars:
        project: <project_id>
        fastchat_state: present
```
Use below Command:
```commandline
ansible-playbook gcp_linux_fastchat_simple.yml
```
## Run Ansible with Different State
#### State - present (terraform apply)
```yaml
---
- name: Run gcp-linux-fastchat-simple role
  hosts: localhost
  tasks:
    - name: Running a role gcp-linux-fastchat-simple creation
      ansible.builtin.import_role:
        name: gcp-linux-fastchat-simple
      vars:
        project: <project_id>
        fastchat_state: present
      
```
Use below Command:
```commandline
ansible-playbook gcp-linux-fastchat-simple.yml
```
#### Step 1: Deleting gcp_linux_fastchat_simple 
```yaml
---
- name: Run gcp-linux-fastchat-simple role
  hosts: localhost
  tasks:
    - name: Running a role gcp-linux-fastchat-simple creation
      ansible.builtin.import_role:
        name: gcp-linux-fastchat-simple
      vars:
        project: <project-id>
        fastchat_state: absent
        
```
Use below Command:
```commandline
ansible-playbook gcp_linux_fastchat_simple.yml
