+++
title = "Resume"
description = "Resume CV"
date = "2023-01-01"
aliases = ["resume", "cv"]
author = "Alknopfler"
+++

# **Alberto Morgante Medina**
### **Senior Telco Edge Software Engineer at Suse**
#### **alknopfler@gmail.com** - **Location: Madrid(Spain)**
#### **[My Blog](https://alknopfler.github.io) - [Linkedin](https://www.linkedin.com/in/albertomorgante/) - [Github](https://github.com/alknopfler)**
## **Summary**
- `Senior Telco Edge software Engineer at Suse` involve into the Telco Edge projects in order to develop the new Telco Edge Platform based on Suse Edge stack. Working with RKE2/K3S, Rancher, Cluster API (CAPI), Metal3, Metallb, Multus (Calico, cilium, flannel), SRIOV, DPDK, OVS, K8s, 5G Telco workloads like FlexRan, and many other technologies in order to develop and integrate the new Telco Edge Platform.

- `Principal Software Engineer at Red Hat` involved in several projects doing integrations tasks for AssistedInstaller, ACM and OCP sub-products. Developing with Golang and operator-sdk the latency k8s operator for Telco customers integrating the solution into ACM placementrules.
  Moreover, I've been working with Baremetal creating ZTPFW (Zero Touch Provisioning Factory Workflow) in order to deploy edge clusters without any manual interaction.

- `Software Architect Lead at Orange` defining the whole architecture as well as developing End2End solutions using event driven architectures with Kafka, golang microservices and Openshift/K8s. Moreover, the challenges for the project define the way to keep the operation and management fully automated in order to integrate new third parties to get the full End2End solution much more elastic and scalable than the Telco market has right now.

- `Cloud Architect Lead at BBVA Bank` working in the Global Platform Area. I’m developing Cloud Services on top of the Global Platform, leading the SWAT technical team in order to develop as fast as posible the Technical services which are cross to the Global Platform.

- `Cloud Computing & Innovation Engineer` I was involved in the deployment of the first banking private cloud based on Openstack and SDN (Nuage).

- `Cloud Computing & Security Engineer at Telefonica`  using security platforms and Cloud platform in order to define new cloud services based on Openstack and Amazon AWS.

### Specialities:

* **Architecture & Lead Skills**: Architecture Designs (from Infrastructure to Microservice architectures designs, cqrs, event sourcing, and development patterns),
* **Team Lead Player, Team building, Team Management (+40)**
* **Cloud Computing**: Openstack, Kubernetes, Openshift, RKE2, K3S, Docker, Rancher, CoreOS, VmWare vcloud, SDN, Google Cloud, AWS, Azure.
* **Devops**: Git, GH actions, Gitlab-ci, ArgoCD, Ansible, Terraform, Puppet.
* **Development**: Golang, Bash, Python, Monkey C, GRPC, RestAPI, ProfoBuffer, KAFKA, Testing ATDD-TDD-BDD, CQRS, Event sourcing.
* **Databases**: Mysql, PostgreSQL, MongoDB, Cassandra, ETCD, Apache Ignite Cache, Redis.
* **Networking**: Switching/Routing (Cisco, Enterasys, Juniper), VPN, SDN, NFV, CNFs/VNFs (Nuage, OpenContrail, OpenDaylight,OVN), 5G Ran, FlexRan, DPDK, SRIOV, PTP.
* **Security**: ISO27001, Peakflow DDoS, Fortinet Gateway, Bluecoat Proxy Chain, UTM Cisco.

## **Work Experiences**
### **Suse**
### Senior Telco Edge Software Engineer (Mar 2023 - Current) - Full Remote

- I'm working as a Senior Telco Edge Engineer working in Telco Edge projects to improve the customer experience using the Suse stack.
- I'm working with RKE2/K3S, Rancher, Cluster API (CAPI), Metal3, Metallb, Multus (Calico, cilium, flannel), SRIOV, DPDK, OVS, K8s, 5G Telco workloads like FlexRan, and many other technologies in order to develop and integrate the new Telco Edge Platform. The main idea is to automate the full deployment using zero touch provisioning and gitops flows.
- Working with Intel FlexRan to deploy the 5G workloads into the edge clusters using the new Telco Edge Platform, automating the workflow using metal3, metallb, sriov, dpdk and many other technologies. The main goal is to get the best performance and the best latency for the 5G workloads, optimizing things like cpu core isolation, cpu performance profiles, huge pages, numa nodes, cpu pinning and many other things.
- Working on the Telco profiles to define a way to define, configure and implement Telco specific profiles to optimize cpu, numa, core isolation and so on. 
- Contributing to upstream projects like ClusterAPI RKE2 (https://github.com/rancher-sandbox/cluster-api-provider-rke2)
- General Talks and conferences (MWC 24, Blogposts, Webinars) in order to share the knowledge and the new features available in the Telco Edge Platform.
- Working with partners to integrate the different use cases into our stack.

### **Red Hat**
### Principal Software Engineer (Mar 2021 - 2023) - Full Remote

- I'm working as a Principal Software Engineer at the Engineering team in several projects like Assisted Installer, Advanced Cluster Management into Openshift ecosystem to offer new products to Telco service providers and customers.
- K8s operator Integration project to join ACM policies with Latency Checks using a Kubernetes Operator in order to ckeck the latency between different locations in a workload (https://github.com/RHsyseng/ddosify-tooling)
- ZTPFW project in order to create a zero touch provisioning deployment of SNO (Edge) and Openshift clusters to make it available to be relocatable in the partner/customer site without any manual action (https://github.com/rh-ecosystem-edge/ztp-pipeline-relocatable)
- CLIZTPFW project to create a golang CLI in order to be used by the ZTPFW project directly
- LABIndex integration scenarios to make some internal integration reducing the time to tests the customer/partner use cases (https://github.com/alknopfler/labs-index)
- TidyMirror is a small tidy mirror featured for disconnected openshift environment to maximize the performance during the mirror step (https://github.com/alknopfler/tidy-mirror)
- Tasty project contribution to make it re-usable in a library way (https://github.com/karmab/tasty)
- Pull secret validator in order to validate some temporal internal development pull secrets
- GPU/DPU project to make it secure using SZTP implementation client/Server (https://github.com/opiproject/sztp)
- Small contributions to upstream projects like oc-mirror, microshift...

### **X by Orange**
### Cloud Architect Lead (Mar 2018 - Mar 2021) - Madrid (Spain)
- Defining the whole architecture as well as developing E2E solutions using a
  based event architectures with kafka, CQRS and event sourcing.
- Golang to get high concurrency and low latency solutions in order to be
  scalable and distributed in several cloud regions.
- Coaching with the excellence principal in different teams.
- Design the SDWAN E2E integration with the kafka and even architecture in
  order to generate the provision process fully automated.
- Architecture for the global notification system for the company in order to be
  scalable with a lot of channels available (sms, email, slack...).
- Amazon Alexa skill for the global XbyOrange application in order to get a new
  user experience and new ways to sell products and services.
- Design and implementation of high performance invoice system using all the
  concurrency power of golang.
- Design and implementation of high scalable architectures to reduce the time
  to market for customer services.
- Deploy software using continuos delivery, continuos integration and full
  automated pipelines
- The main challenge for the project will be define the operation and
  management fully automated in order to integrate new third parties to get the
  full End2End solution much more elastic and scalable than the Telco market
  has right now.

### **BBVA**
### Cloud Architect Lead (Jan 2017 - Mar 2018) - Madrid (Spain)

- Define the technical pieces needed inside the Global Platform which are
  cross for all services running on the platform.
- Lead the SWAT technical Team in order to develop the Technical services
  which are cross to the Global Platform as well as giving support to other teams
  to engage into the process.
- Define and collaborate in the pipeline process to deploy all the service
  automatically using Jenkins.
- Define the ATTD/TDD/BDD and the agile methodologies to develop the cross
  services.
- Architecture design (based on microservices, Availability Zones, Openshift
  deployment), Development (using TDD methodology) and Delivery (based on
  pipeline and CI/CD to build source code, compose and unit test, integration
  test, deployment in openshift) to Production of a "Distributed Cache Web
  Service" based on Golang, Java and Apache Ignite, RestAPI.
- Architecture design (based on microservices, Availability Zones, Openshift
  deployment), Development (using TDD methodology) and Delivery (based on
  pipeline and CI/CD to build source code, compose and unit test, integration
  test, deployment in openshift) to Production of a "Configuration Manager Web
  Service" based on Golang, ETCD, Mongodb, RestAPI.
- Architecture design (based on microservices, Availability Zones, Openshift
  deployment), Development (using TDD methodology) and Delivery (based on
  pipeline and CI/CD to build source code, compose and unit test, integration
  Page 3 of 7
  test, deployment in openshift) to Production of a "Cron Web Service" based on
  Java, Mongodb, RestAPI.
- Architecture design (based on microservices, Availability Zones, Openshift
  and AWS deployment), development (using TDD methodology) and Delivery
  (based on pipeline and CI/CD to build source code, compose and unit test,
  integration test, deployment in openshift and AWS) to Production of a "Global
  Notification Service" based on Java, Golang, Mongodb, RestAPI, GRPC,
  Protobuffer in order to reduce the proccessing time of notifications.

### Cloud Computing and Innovation Engineer (Jan 2014 - Jan 2017) - Madrid (Spain)

- Several Talks sharing our knowledge in the Openstack Mexican Day,
  Openstack Summit Barcelona.
- Technical Book Reviewer: SDN (Software-Defined-Networks) with Openstack
- Openstack and SDN (Nuage) Architecture design, implementation and
  deployment in the production environment for continuous delivery purposes.
  The most important key in the project was the automation of everything
  (Infrastructure as code including the HW deployment phase, networking
  automation with SDN, Continious Delivery/Integration)
- Several Openstack release upgrades plans and deployment made
  successfully in order to update the platform (SDN and Openstack) to new
  releases every 6 months.
- Nuage SDN architecture design, development and deployment as well as
  the integration with Openstack in order to automate the security policies to
  the different projects. The idea was deploy an auto-manage the Networking
  platform, provisioning everything that could be possible automatically.
- Openstack based on docker containers to deploy an openstack platform (with
  most of the Openstack services) using Kubernetes cluster. The idea was to
  improve the platform moving from VM to Docker containers as well as get the
  SDN for 2 Overlays (Infrastructure and end-user plane).
  The first part of the project was deploy the openstack modules based on
  containers. After that, the SDN integration was done based on 2 overlays.
  One of them, for the infrastructure plane instead of VLAN and physical switch/
  router. The second one, is the common SDN uses cases, the end-user plane.
- Sahara integration for Big Data purposes for different teams involved in the
  project. The main goal in this project was allow to the End-user Developers
  deploy Hadoop clusters running into Openstack automating the Big Data
  phases during the process.
- Trove for DBaaS integrated in the Openstack platform. The main goal in
  this project was integrate the Trove Module to offer Database as a service
  adapting the solution to the bank needs.

### **Telefonica**
### Cloud Computing & Security Engineer (apr 2010 - mar 2014) - Madrid (Spain)

* Full design the CLOUD architecture for pre-production environment (Vmware
  (vcenter, vStorage, vmotion), Orchestrator Cloud, OpenStack, HP Blade
  platforms, San Storage solutions, SDN/NaaS, MPLS, identity management)
* Virtual Data Center Project. Technical Manager services development
  within TGSolutions direction. Instant Server Cloud by Joyent/Openstack
  and T.Digital. Technical Manager services development within TGSolutions
  direction.
* Insight and consulting Fortinet solutions for Virtual Data Center and UTM
  (Fortiweb, Fortimail, Fortigate)
* Cloud Development based on Cloud Bluecoat (Thread Pulse based on Proxy
  Chain)
* CLOUD Project based on OPENSTACK infraestructure, VMWare ESXi 5.0
  and Amazon Web Services EC2 using the Joyent SmartOS.
* CDN Project (Backup and Security issues). Technical Manager services
  development within TGSolutions direction.
* Security Projects in order to develop new services using new technologies.
* Development DDoS Shield Service Project using PEAKFLOW technology as
  an international level security service.
* Integration Project NetApp Virtual Storage Console Plugin with VMWare ESX
  (deduplication, Multitenacy)
* Optimization Project using Balancers Cloud F5 as VDI (PCoIP as an
  alternative to RDesktop)
* Implementation of ITIL processes, ISO27001 in different corporate security
  projects.
* Project Manager “Security in network management center”.
* Project Management (Security Project Plan, Identity Management, Internal
  Security Audit using the standard Iso27001)
* Management and operation of the SGIS platform using different security
  infraestructure ARCSIGHT, OSSIM, BITÁCORA, PEAKFLOW, IDS, IPS.
* Security Incident Management (Spoofing identity politics, Malware, AV, DDoS
  attacks, PEAKFLOW, UTM, privilege escalation, etc...)

### IT & System Senior Engineer (apr 2009 - apr 2010) - Madrid (Spain)
* Administration and platform support in Solaris (8,9,10), Linux (debian, suse
  ES, redhat ES, Ubuntu Server) and Windows Server (2000, 2003, 2008)
* Administration in Solaris NetBackup (Veritas) platform
* Virtual Platform operation in VMWARE ESXi (Versión 4.1), Vcenter, VCloud
  Director and OPENNEBULA platform.
* SSL Certificates from Verisign and opensource platforms like OpenCA.
* Management Radius authentication platforms (Juniper, FreeRad, PSaX),
  openLdap, Identity Manager and Metadirectory solutions (Suse)
* Design and Management VPN Remote Access solutions (cisco, juniper)
* Support 2nd and 3rd level for User Management in different Network
  Management Centers.
* Management Infrastructure services like DNS, Mail Relay, HTTP, Proxy Web,
  SSH, SFTP, RADIUS, LDAP.
* Management and support service for Status Health Platform using NAGIOS,
  PANDORA, SOLARWIND.

### **Alcorce Telecomunicaciones**
### System Administrator (Jan 2007 - Apr 2009) - Madrid (Spain)
* Support and Administration in Solaris platforms.
* Consulting, design and implementation of a solution for High Availability SAN
  Storage.
* Consulting, design and implementation of a Radius (FREERADIUS) platform
  for high availability solution (HA).
* Consulting, design and implementation of LDAP platform for high availability
  solution (HA).
* Design and implementation of a Global Authentication System High
  Availability (HA) for the CES Felipe II University of Aranjuez (FreeRadius,
  Ldap, Samba, SMB-tools, Phpmyldapadmin, 802.1x clients).
* Design and implementation of a NAC solution to control network access on
  Enterasys Network.
* Corporate services operation Ftp, Http, Dhcp using SSL VPN tunnel (Juniper
  SA).
* Technical Support for Enterasys course in different Countries
* Trainer course on UNIX Advanced Administration.
* Network Audit Project at the center CES Felipe II as networking and security
  consultant.
* Security Hardening Project on Unix platform.
* Implementing security policies on Enterasys equipment.
* Support Projects in Enterasys, Cisco and Telefónica Soluciones.
* Operational tasks using Juniper Accelerator Wxc500 systems.

### **Atos**
### Open Source Developer (Jan 2006 - Jan 2007) - Madrid (Spain)
* Shell Programming scripting for different configuration process on Oracle DB.
* Software development using AWK, PYTHON, KSH for concurrent process
  optimization.
* Shell Programming script for automated translation work in the change
  process Amena to Orange.
* Programming different DataBase queries (MySQL and Oracle 9i)
* Management in version control server (ClearCase)


## **Education**
Universidad Politécnica de Madrid
Computer Science Engineering Degree, System Administration · (2003 - 2006)

## **Languages**
- English (Professional level)
- Spanish (native)

## **Certifications**
- Linux LPIC I & II
- ITIL v2 Foundation
- Cisco CCNA Certification
- VCP Certification
- Switching & Routing Enterasys Certification

## **Publications**
- [ACM operator to integrate with Latency Checks](https://medium.com/open-5g-hypercore/episode-xi-latency-driven-service-orchestration-183f41e6d879)
- [Remote debugging kubernetes](https://developers.redhat.com/articles/2021/12/13/remote-debugging-kubernetes-using-vs-code#)
- [Open source is a cultural change](https://bbvaopen4u.com/en/actualidad/open-source-cultural-change)
- [Alexa Skill - Noticias de Móstoles](https://www.amazon.es/alknopfler-Noticias-de-M%C3%B3stoles/dp/B07MPVTH1S)
- [BBVA Caso de éxito: Openstack Day Latam](https://www.linkedin.com/in/albertomorgante/detail/overlay-view/urn:li:fsd_profileTreasuryMedia:(ACoAABAi8N4B-_DrCZSAmVVSgSAsidg9YLC-UJQ,1500321618263)/?lipi=urn%3Ali%3Apage%3Ad_flagship3_profile_view_base%3BBt8XHI7BTeK%2FejnAVD2tLA%3D%3D&licu=urn%3Ali%3Acontrol%3Ad_flagship3_profile_view_base-featured_item_detail_view)
- [BBVA Openstack Summit Barcelona 2016](https://www.youtube.com/watch?v=QyGHZ2HCwqY)
- [Design your own Home Alarm System using Go](https://github.com/alknopfler/alkalarm/wiki)
- [Alexa Skill - Profesor Guitarra](https://www.amazon.es/alknopfler-Profesor-de-Guitarra/dp/B07MSBRRWR/ref=cm_cr_arp_d_product_top?ie=UTF8) 
