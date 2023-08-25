# AnsibleAKSOrchestrate
AnsibleAKSOrchestrate is a project that demonstrates how to use Ansible to orchestrate the creation of an Azure Kubernetes Service (AKS) cluster and deploy an application to it. This project provides a clear structure for setting up the cluster and deploying the app, enhancing modularity and maintainability.
## Table of Contents

- [Project Overview](#project-overview)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Directory Structure](#directory-structure)
- [Contributing](#contributing)
## Project Overview

AnsibleAKSOrchestrate showcases how Ansible can be utilized to streamline the process of creating an AKS cluster and deploying an application to it. The project is organized into separate roles for cluster creation and app deployment, ensuring clear separation of concerns. The roles are designed for modularity, making it easy to customize and extend the project.

## Getting Started

To get started with AnsibleAKSOrchestrate, follow these steps:

1. Clone this repository:
   ```sh
   git clone https://github.com/C0M-M4ND0/AnsibleAKSOrchestrate.git
   cd AnsibleAKSOrchestrate
2. Install Ansible:
   ```sh
   pip3 install ansible
3. Customize the vars.yaml file to match your environment and requirements.
4. Login to Azure Cloud:
   
   Before setting up the AKS cluster, make sure you're logged into your Azure account using the Azure CLI:
   ```sh
   az login
   ```
6. Install kubectl:

   To interact with the AKS cluster, you'll need kubectl installed. You can install it using the Azure CLI:
   ```sh
   az aks install-cli
7. Install Azure collection:
   ```sh
   ansible-galaxy collection install azure.azcollection
8. Install dependencies required by the collection:
   ```sh
   pip3 install -r ~/.ansible/collections/ansible_collections/azure/azcollection/requirements-azure.txt

# Usage
- Setup AKS Cluster and Deploy App:
  Run the following command to set up the AKS cluster and deploy the app:
  ```sh
  ansible-playbook ansible/setup-k8s-environment.yaml
- Tear Down AKS Environment:
  To tear down the AKS environment and associated resources:
  ```sh
  ansible-playbook ansible/destroy-k8s-environment.yaml
# Directory Structure
The project directory structure is organized as follows:
```sh
.
├── ansible/
│   ├── destroy-k8s-environment.yaml
│   ├── roles/
│   │   ├── create-cluster/
│   │   │   └── tasks/
│   │   │       └── main.yaml
│   │   ├── deploy-app/
│   │   │   └── tasks/
│   │   │       └── main.yaml
│   │   ├── ...
│   │   └── ...
│   ├── setup-k8s-environment.yaml
│   └── vars.yaml
└── kubernetes/
    └── app-deployment.yaml
```
# Contributing
Contributions are welcome! If you find any issues or have suggestions for improvements, feel free to open an issue or create a pull request.


