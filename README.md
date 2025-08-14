# My Private Cloud Project

## Introduction
In the era of digital transformation, cloud computing has become a cornerstone for delivering flexible, scalable, and cost-efficient IT infrastructure. Among the various cloud deployment models, Private Cloud stands out as a solution that offers dedicated resources to a single organization. This approach provides complete control over infrastructure, greater customization, and enhanced security, making it particularly suitable for businesses with strict compliance requirements or sensitive workloads.

Private Cloud environments can be deployed on-premises or in dedicated data centers, enabling organizations to proactively manage performance, capacity, and data governance. Unlike public cloud, where resources are shared among multiple tenants, a private setup ensures predictable performance and tailored configurations aligned with organizational policies.

To build and operate such an environment efficiently, OpenStack has emerged as one of the most widely adopted open-source platforms. It enables the creation and management of Infrastructure-as-a-Service (IaaS) by orchestrating compute, storage, and networking resources through a unified control plane. OpenStack’s modular architecture, extensive API support, and active community development make it highly adaptable—supporting deployments that range from small laboratory setups to enterprise-scale cloud infrastructures.

With these advantages, deploying a Private Cloud using OpenStack provides both the flexibility of modern cloud computing and the security of dedicated infrastructure. This project aims to implement such a system in a controlled environment to explore its capabilities, operational workflows, and scalability potential.

## Objectives:
In this project, a Private Cloud system will be deployed on Ubuntu 22.04 with a scale of 1–2 nodes, ensuring the following core capabilities:
- Manage, create, delete, and modify virtual machines (VMs).
- Create, delete, modify, and configure virtual networking.
- Integrate and operate a Block Storage system within the OpenStack environment.

## Infrastructure:
<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/7d89445e-f1ec-4a69-8aee-2c3d29b216ff" />

## Openstack components:
### Controller Node:
Main management node that controls and coordinates all OpenStack services.
+ Keystone : Identity and access management.
+ Glance : Stores and provides VM images.
+ Placement : Tracks and allocates resources (CPU, RAM, Disk).
+ Nova Services : Includes API, scheduler, conductor, and compute service for running VMs.
+ Neutron Services : Manages virtual networking.
+ Horizon : Web dashboard for users and administrators.
+ Cinder Scheduler : Assigns block storage requests.
+ MariaDB : Database for service data.
+ Memcached : Cache for faster performance.
+ etcd : Stores configuration and service states.
+ Apache2 : Web server for dashboard and APIs.
+ RabbitMQ : Message broker for service communication.
+ Chrony : Time synchronization between nodes.
+ VMs : Can run virtual machines directly on the controller.
### Compute Node:
Runs virtual machines and handles workloads.
+ Nova Compute : Launches and manages VMs.
+ Neutron Open vSwitch Agent : Connects VMs to the virtual network.
### Storage Node:
Provides block storage for virtual machines.
+ Cinder Volume : Supplies block storage to VMs.
+ tgt : iSCSI target service for volume access.
+ lvm2 (Logical Volume Manager) : Manages physical and logical volumes.
