# 🛠️ Ansible Kubernetes HA Cluster

![Ansible](https://img.shields.io/badge/Ansible-Automation-red?logo=ansible\&style=flat-square)
![Kubernetes](https://img.shields.io/badge/Kubernetes-HA-blue?logo=kubernetes\&style=flat-square)
![Ubuntu](https://img.shields.io/badge/Ubuntu-22.04%2F24.04-E95420?logo=ubuntu\&style=flat-square)
![License: MIT](https://img.shields.io/badge/License-MIT-green.svg?style=flat-square)

Automated setup of a **Highly Available (HA) Kubernetes Cluster** using **Ansible**.
This project provisions a full HA cluster consisting of:

* Multiple control plane (master) nodes
* One or more worker nodes
* HAProxy as external load balancer
* Containerd as the container runtime

Ideal for learning or bootstrapping production-grade Kubernetes infrastructure.

---

## 📆 Project Structure

```bash
.
├── inventory/
│   └── hosts.ini               # Inventory file with group definitions
├── playbook.yml               # Main playbook to install and configure the cluster
├── reset-k8s.yml              # Playbook to reset the Kubernetes cluster
└── roles/
    ├── common/                # Common setup tasks (update, dependencies, etc.)
    ├── containerd/            # Container runtime setup
    ├── cri-tools/             # Installation of CRI tools
    ├── kubernetes/            # Kubernetes packages and settings
    ├── lb-haproxy/            # HAProxy load balancer setup
    ├── master-init/           # Initialize first control-plane node
    ├── master-join/           # Join control-plane nodes to cluster
    └── worker-join/           # Join worker nodes to cluster
```

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/masdikaaa/ansible-k8s-ha-cluster.git
cd ansible-k8s-ha-cluster
```

### 2. Customize Your Inventory

Edit the `inventory/hosts.ini` file with your server IP addresses:

```ini
[lb]
loadbalancer ansible_host=10.0.0.10

[masters]
master1 ansible_host=10.0.0.11
master2 ansible_host=10.0.0.12
master3 ansible_host=10.0.0.13

[workers]
worker1 ansible_host=10.0.0.14
```

Ensure SSH access is possible and root login or privilege escalation is configured.

### 3. Run the Playbook

```bash
ansible-playbook -i inventory/hosts.ini playbook.yml
```

---

## 🔄 Resetting the Cluster

To wipe and reset all nodes:

```bash
ansible-playbook -i inventory/hosts.ini reset-k8s.yml
```

---

## ⚙️ Requirements

* Ansible 2.11+
* Ubuntu 22.04 or 24.04 on all nodes
* Python 3.8+
* Root SSH access to all nodes

---

## 🧠 Key Features

* Full HA control plane setup
* Load balancing with HAProxy
* Containerd runtime
* Modular Ansible roles
* Clean reset playbook
* Designed for production or learning use

---

## 📜 License

MIT License. Feel free to use, modify, and contribute.

---

## 👤 Author

**Andika Ferdi Alvianto**
📧 [Email](mailto:me@masdika.biz.id) | 🌐 [LinkedIn](https://www.linkedin.com/in/masdika)
