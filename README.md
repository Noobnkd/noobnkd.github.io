# My Private Cloud Project

## Introduction
In today’s digital world, cloud computing is an important way to provide IT systems that are flexible, scalable, and cost-effective. Among the different types of cloud deployment, Private Cloud is a good choice for organizations that need dedicated resources. It offers full control over the system, allows more customization, and gives stronger security. This makes it suitable for businesses with strict rules or sensitive data.

A Private Cloud can be set up in a company’s own location or in a dedicated data center. This lets the organization manage performance, storage, and data security more directly. Unlike the public cloud, where many users share the same resources, a private setup gives more stable performance and settings that match the company’s own policies.

OpenStack is one of the most popular open-source platforms for building a Private Cloud. It helps manage computing, storage, and networking in one system, creating what is known as Infrastructure-as-a-Service (IaaS). OpenStack is flexible and can be used for both small test environments and large enterprise systems.

In this project, a Private Cloud will be deployed using OpenStack to test its features, see how it works in real operations, and explore how it can grow in the future.

## Objectives:
In this project, a Private Cloud system will be deployed on Ubuntu 22.04 with a scale of 1–2 nodes, ensuring the following core capabilities:
- Manage, create, delete, and modify virtual machines (VMs).
- Create, delete, modify, and configure virtual networking.
- Integrate and operate a Block Storage system within the OpenStack environment.

## Infrastructure:
<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/7d89445e-f1ec-4a69-8aee-2c3d29b216ff" />

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
