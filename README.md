# AnsibleAKSOrchestrate
AnsibleAKSOrchestrate is a project that demonstrates how to use Ansible to orchestrate the creation of an Azure Kubernetes Service (AKS) cluster, deploy an application to it, and set up a monitoring using Prometheus. This project provides a clear structure for setting up the cluster, deploying the app, and enabling monitoring capabilities.
## Table of Contents

- [Project Overview](#project-overview)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Directory Structure](#directory-structure)
- [Contributing](#contributing)
## Project Overview

AnsibleAKSOrchestrate showcases how Ansible can be utilized to streamline the process of creating an AKS cluster, deploying an application, and implementing monitoring with Prometheus. The project is organized into separate roles for cluster creation, app deployment, and monitoring setup, ensuring clear separation of concerns and enhancing modularity.
## Getting Started

To get started with AnsibleAKSOrchestrate, follow these steps:

1. Clone this repository:
   ```sh
   git clone https://github.com/C0M-M4ND0/AnsibleAKSOrchestrate.git
   cd AnsibleAKSOrchestrate
2. Install Ansible:
   ```sh
   pip3 install ansible
3. Install Azure Modules for Ansible:
   To interact with Azure services using Ansible, you'll need to install the Azure modules. You can install them using the following command:
   ```sh
   pip3 install "ansible[azure]"

4. Customize the vars.yaml file to match your environment and requirements, you need to add `CLIENT_ID` and `CLIENT_SECRET` to your environment variable.
5. Login to Azure Cloud:
   
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
9. Install Helm:
    
    Helm is required to deploy Prometheus. Depending on your operating system, follow the installation instructions for Helm: [Helm Installation Guide](https://helm.sh/docs/intro/install/).

# Usage
- Setup AKS Cluster and Deploy App:
  Run the following command to set up the AKS cluster and deploy the app:
  ```sh
  ansible-playbook ansible/setup-k8s-environment.yaml
- Tear Down AKS Environment:
  To tear down the AKS environment and associated resources:
  ```sh
  ansible-playbook ansible/destroy-k8s-environment.yaml
- Access Grafana:
  
  After deploying the monitoring stack, you can access Grafana to visualize your metrics.
  
  Follow these steps:
  
  a. Start port forwarding to the Grafana service:
  ```sh
  kubectl port-forward -n monitoring service/prometheus-grafana 3000:80
  ```
  b. Open your web browser and navigate to http://localhost:3000.
  
  Use the following credentials to log in:
  
     - Username: `admin`
  
     - Password: `prom-operator`
  
  d. Once logged in, you can explore the monitoring dashboards and visualize your AKS cluster metrics.
# Directory Structure
The project directory structure is organized as follows:
```sh
.
├── ansible
│   ├── destroy-k8s-environment.yaml
│   ├── roles
│   │   ├── create-cluster
│   │   │   └── tasks
│   │   │       └── main.yaml
│   │   ├── deploy-app
│   │   │   └── tasks
│   │   │       └── main.yaml
│   │   ├── destroy-cluster
│   │   │   └── tasks
│   │   │       └── main.yaml
│   │   ├── destroy-resource-group
│   │   │   └── tasks
│   │   │       └── main.yaml
│   │   └── monitor-cluster
│   │       └── tasks
│   │           └── main.yaml
│   ├── setup-k8s-environment.yaml
│   └── vars.yaml
└── kubernetes
    └── app-deployment.yaml
```
# Contributing
Contributions are welcome! If you find any issues or have suggestions for improvements, feel free to open an issue or create a pull request.


