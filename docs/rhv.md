# OpenShift Container Platform on RHV

## OCP on RHV

### Configuring manifest

Ansible inventory variables are used to dictate the configuration and management of an environment. The variables for a RHV install are broken up into 2 directories:

* `ocp4`: This contains all OpenShift 4 variables overall
* `ocp4-rhv`: This contains variables specific to RHV installations of OpenShift 4.X

An example inventory file has been created and can be found in `inventory/ocp4-rhv`. It should look something like this:

```
[ocp4:children]
ocp4-rhv

[ocp4-rhv]
localhost ansible_connection=local

[hosted_engine]
rhvm.domain.com
```

#### Variables to Configure

There are variables to configure in the following files:

```
inventory/group_vars/ocp4/vault/pullsecret.yml
inventory/group_vars/ocp4-rhv/ovirt.yml
inventory/group_vars/ocp4-rhv/cluster.yml
```
##### NOTE: Please update the install-config template with your CA (lines 53 onward to be replaced). The install config is in: `roles/ocp_deploy/templates/rhv-install-config.yaml.j2`. Eventually this will also be a variable that can be applied, but for now this is how it is added.

If using a json object for the `openshift_pull_secret` be sure to enclose the json in single quotes (`'`).

## Deploying

Execute the following command to execute the deployment process

```sh
$ ansible-playbook -i inventory/ocp4-rhv playbooks/deploy_ocp.yml
```

The above command assumes that the extra set of variable as described in the prerequisites section are stored in a file called `ocp-dev`.

## OCP on vSphere

###TODO
