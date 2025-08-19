<h1 align="center"> My Private Cloud Project </h1>
<p align="center">
<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/321accf7-4976-4db5-abb7-7047c999f613" />
</p>

## Introduction
In today’s digital world, cloud computing is an important way to provide IT systems that are flexible, scalable, and cost effective. Among the different types of cloud deployment, Private Cloud is a good choice for organizations that need dedicated resources. It offers full control over the system, allows more customization, and gives stronger security. This makes it suitable for businesses with strict rules or sensitive data.

A Private Cloud can be set up in a company’s own location or in a dedicated data center. This lets the organization manage performance, storage, and data security more directly. Unlike the public cloud, where many users share the same resources, a private setup gives more stable performance and settings that match the company’s own policies.

**OpenStack** is one of the most popular open-source platforms for building a Private Cloud. It helps manage computing, storage, and networking in one system, creating what is known as Infrastructure-as-a-Service (IaaS). OpenStack is flexible and can be used for both small test environments and large enterprise systems.

In this project, a Private Cloud will be deployed using OpenStack to test its features, see how it works in real operations, and explore how it can grow in the future.

## Objectives:
In this project, a Private Cloud system will be deployed on Ubuntu 22.04 with a scale of 1–2 nodes, ensuring the following core capabilities:
- Manage, create, delete, and modify virtual machines (VMs).
- Create, delete, modify, and configure virtual networking.
- Integrate and operate a Block Storage system within the OpenStack environment.

## Infrastructure and Components:
<p align="center">
<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/7d89445e-f1ec-4a69-8aee-2c3d29b216ff" />
</p>

### Controller Node
Main management node that controls and coordinates all OpenStack services.

- **Keystone**: Identity and access management.
- **Glance**: Stores and provides VM images.
- **Placement**: Tracks and allocates resources (CPU, RAM, Disk).
- **Nova Services**: Includes API, scheduler, conductor, and compute service for running VMs.
- **Neutron Services**: Manages virtual networking.
- **Horizon**: Web dashboard for users and administrators.
- **Cinder Scheduler**: Assigns block storage requests.
- **MariaDB**: Database for service data.
- **Memcached**: Cache for faster performance.
- **etcd**: Stores configuration and service states.
- **Apache2**: Web server for dashboard and APIs.
- **RabbitMQ**: Message broker for service communication.
- **Chrony**: Time synchronization between nodes.
- **VMs**: Can run virtual machines directly on the controller.

### Compute Node
Runs virtual machines and handles workloads.

- **Nova Compute**: Launches and manages VMs.
- **Neutron Open vSwitch Agent**: Connects VMs to the virtual network.

### Storage Node
Provides block storage for virtual machines.

- **Cinder Volume**: Supplies block storage to VMs.
- **tgt**: iSCSI target service for volume access.
- **lvm2 (Logical Volume Manager)**: Manages physical and logical volumes.

## Operating Mechanism
When a user accesses the system through Horizon, the request is sent to the Controller for authentication via Keystone. Once authentication is successful, if the request is to create a virtual machine, Nova on the Controller retrieves the required operating system image from Glance, then schedules and decides whether the VM will run on the Controller or a Compute node, along with its RAM size, number of CPUs, security groups, keypair, and network configuration, all based on the user’s request. 

Then, Neutron sets up the virtual network and assigns an IP address to the VM. If the VM requires additional block storage, the request is sent to Cinder, which allocates space from the Storage node (managed by LVM) and attaches it to the VM. Throughout this process, services exchange data over the internal network to ensure performance and security, while external access is provided through the External Network using a Floating IP. This demonstrates the power of OpenStack in seamlessly integrating multiple services to deliver an efficient and secure private cloud infrastructure.
<p align="center">
<img width="600" height="650" alt="openstack_operating_mechanism" src="https://github.com/user-attachments/assets/bf6fca5d-31d1-43df-aa12-acc11f7a41d6" />
</p>

### This is my demo
### [📹 Watch the demo on Google Drive](https://drive.google.com/drive/folders/1TvQmpNsVWiSDXN2HY7fO7q9rsVGQwPOO?usp=sharing)

### Conclusion
This project successfully deployed a three-node private cloud by using Openstack, with each node dedicated to computing, networking, or storage. Working on a setup like this gave me the chance to see how resources can be separated and managed efficiently. It also helped me gain a more practical view of private cloud architecture compared to just reading about it in theory.

Through this process, I learned not only how to install and configure the system but also how to troubleshoot and optimize it for better performance. Seeing the three nodes work together smoothly made me appreciate the importance of good planning and clear infrastructure design. It also confirmed that separating services across nodes can improve both stability and security.

Personally, I see this project as an important step toward my career goal in Cloud Computing and DevOps. In the future, I aim to expand the system with more nodes, integrate automation tools, and add monitoring solutions. This experience gives me the confidence to work on larger-scale systems and adapt to more complex real-world scenarios.
