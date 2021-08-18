# OpenShift Container Platform on OpenStack

## THIS DOCUMENT IS NOT FINISHED AND NOT TO BE USED AS VALID DOCUMENTATION

## OCP on OpenStack

### Configuring manifest

Ansible inventory variables are used to dictate the configuration and management of an environment. The variables for a vSphere installation are broken up into 2 directories:

* `ocp4`: This contains all OpenShift 4 variables overall
* `ocp4-osp`: This contains variables specific to OpenStack installations of OpenShift 4.X

An example inventory file has been created and can be found in `inventory/ocp4-osp`. It should look something like this:

```
[ocp4:children]
ocp4-osp

[ocp4-osp]
localhost ansible_connection=local

[vcenter]
vcenter.domain.com
```

#### Variables to Configure

There are variables to configure in the following files:

```
inventory/group_vars/ocp4/vault/pullsecret.yml
inventory/group_vars/ocp4-osp/openstack.yml
inventory/group_vars/ocp4-osp/cluster.yml
```
##### NOTE: Please update the install-config template with your CA (lines XX onward to be replaced). The install config is in: `roles/ocp_deploy/templates/osp-install-config.yaml.j2`. Eventually this will also be a variable that can be applied, but for now this is how it is added.

If using a json object for the `openshift_pull_secret` be sure to enclose the json in single quotes (`'`).

## Deploying

Execute the following command to execute the deployment process

```sh
$ ansible-playbook -i inventory/ocp4-osp playbooks/deploy_ocp.yml
```
