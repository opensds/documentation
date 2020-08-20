---
title: Quick Start Guide
description: "The quickstart guide is for users and new contributors to get familiar with SODA Foundation, by installing a simple containerized local cluster. It also gives the installation steps for old OpenSDS versions"
weight: 20
---

This is a quickstart guide for users and new contributors to get familiar with [SODA Foundation Releases](https://github.com/sodafoundation/releases) and its [projects](https://github.com/sodafoundation). It will help to try out the SODA Releases using the binaries with minimum configurations.

***Note**: *At present, this document also provides the installation steps to try out older OpenSDS releases. Soon, the support for old opensds releases shall be removed.**

To have more magement control on the installaton cofigurations, or to try out various configurations refer to the detailed installation guide [here](/soda-gettingstarted/installation)

## Quick Installation
### Install SODA v1.0.0 Faroe Release Jun 2020
Quick installation from SODA Faroe Release:

 - **Prerequisite**
	 - OS: Ubuntu 16.04 or Ubuntu 18.04
	 - `root` user rights is REQUIRED 
    -   Make sure the following packages are installed or use the steps to install them.
    - Install Basic Dependency:
	    - apt-get update && apt-get install -y git make curl wget libltdl7 libseccomp2 libffi-dev gawk
	    
   - Install Docker
   	 - For Ubuntu 16.04:
	    - wget **[https://download.docker.com/linux/ubuntu/dists/xenial/pool/stable/amd64/docker-ce_18.06.1~ce~3-0~ubuntu_amd64.deb](https://download.docker.com/linux/ubuntu/dists/xenial/pool/stable/amd64/docker-ce_18.06.1~ce~3-0~ubuntu_amd64.deb)**
	
	 - For Ubuntu 18.04:
	    - wget **[https://download.docker.com/linux/ubuntu/dists/bionic/pool/stable/amd64/docker-ce_18.06.1~ce~3-0~ubuntu_amd64.deb](https://download.docker.com/linux/ubuntu/dists/bionic/pool/stable/amd64/docker-ce_18.06.1~ce~3-0~ubuntu_amd64.deb)**
	    
    - dpkg -i docker-ce_18.06.1~ce~3-0~ubuntu_amd64.deb
    - Install docker-compose:
	    -   curl -L https://github.com/docker/compose/releases/download/1.23.1/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose
		-   chmod +x /usr/local/bin/docker-compose
    -   Required golang version: 1.13.x
	    -   Run following command `go version` and check the version
	    -   If the required version is not installed on the system, install golang,1.13.9 using:
		   - wget **[https://storage.googleapis.com/golang/go1.13.9.linux-amd64.tar.gz](https://storage.googleapis.com/golang/go1.13.9.linux-amd64.tar.gz)**
		- tar -C /usr/local -xzf go1.13.9.linux-amd64.tar.gz
		- echo export PATH=$PATH:/usr/local/go/bin >> /etc/profile
		- echo export GOPATH=$HOME/gopath >> /etc/profile
		- source /etc/profile

 - **Get and Install Release Binaries**
	 - wget  **[https://github.com/sodafoundation/installer/releases/download/v1.0.0/installer-v1.0.0.tar.gz](https://github.com/sodafoundation/installer/releases/download/v1.0.0/installer-v1.0.0.tar.gz)**
 **OR** Download the installer binaries from  
 [https://github.com/sodafoundation/installer/releases/tag/v1.0.0](https://github.com/sodafoundation/installer/releases/tag/v1.0.0)

	 - tar xvzf installer-v1.0.0.tar.gz
	 - cd installer-v1.0.0/ansible/
	 - chmod +x ./install_ansible.sh && ./install_ansible.sh
	 - ansible --version # Ansible version 2.4.x is required
	 - The HOST_IP need to be set to the real_host_ip of your host (ex: 192.168.1.10 or 127.0.0.1 for localhost)
		 - export HOST_IP = <your_real_host_ip>
		 - vim group_vars/common.yml # Modify `host_ip` address if needed

 - **Run the installer**
	 - ansible-playbook site.yml -i local.hosts
	 - Note: If you want to clean up and test again, run
		 - ansible-playbook clean.yml -i local.hosts -vvv
	 - and then run:
		 - ansible-playbook site.yml -i local.hosts
 -   **How to do a quick test**
		- Open Your Browser and use the http://< actual host ip>:8088 to access the SODA Dashboard
    (This IP should be the IP Address of the host if you have updated the config file) Ex: [http://127.0.0.1:8088](http://127.0.0.1:8088)
  
	 - Use admin/opensds@123 credentials to login
     -   You will login to the UI Dashboard and you can verify the features through various menu options



### Install SODA v0.20.0 Elba Release Apr 2020
 - Elba Release (First Release of SODA) : Refer the "How to use the Release" section of [Elba Release Notes](https://github.com/sodafoundation/releases/releases/tag/v0.20.0)
 

ATTN: We are currently not supporting the older versions before Elba. However, if you have specific reasons to use older versions, please contact at #general  slack channel of [soda foundation slack](https://sodafoundation.io/slack)

