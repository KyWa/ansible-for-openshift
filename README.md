# Ansible Automation for OpenShift Container Platform 4.X

[OpenShift](https://www.redhat.com/en/technologies/cloud-computing/openshift) can be installed using the `openshift-install` binary obtained directly from Red Hat, however it is considered cumbersome by some and requires getting all of your information at once if used in the "manual" way. This Ansible Automation repo seeks to change that and provide a templated and variabalized way of deploying OpenShift Container Platform 4.X. 

> **_NOTE:_** This Ansible role should also work for [OKD](https://www.okd.io/) as well. 
> The variables `openshift_client_base_url` and `openshift_install_url` will need to be updated to target OKD correctly. 
> For more information, see https://github.com/openshift/okd#getting-started

* OCP on RHV: [docs](docs/rhv.md)
* OCP on vSphere: [docs](docs/vsphere.md) ##TODO
* OCP on OpenStack: [docs](docs/openstack.md) ##TODO
