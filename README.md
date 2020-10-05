Role Name
=========

An Ansible role that creates a Docker strategy build and deployment.

Currently the role consumes Apache image `registry.redhat.io/rhscl/httpd-24-rhel7:latest` from a public or private registry. It creates a namespace, service, route an an image from a BuildConfig. When the app is deployed the playbook queries the route to confirm a successful deployment.

The goal is to demonstrate the ability of a successful build & deployment on OpenShiftv4.

Requirements
------------

Covered by depedencies.

Role Variables
--------------

**vars**:
```
apache_image: 'registry.redhat.io/rhscl/httpd-24-rhel7'
internal_image: "image-registry.openshift-image-registry.svc:5000/conformance-{{random_number}}/conformance-img:latest"
dns_zone: 'domain.us'
ocp_domain: 'ocp4'
```
Dependencies
------------
To deploy using pip

```
python3 -m pip install -r requirements.txt
```

If you're using RHEL 7 enable `rhel-7-server-ose-4.5-rpms` and `yum install python2-openshift`
For RHEL 8 you'll need to enable the [EPEL](https://fedoraproject.org/wiki/EPEL) repository to install `yum install python3-openshift`

Example Playbook
----------------

Ansible role can be run as follows:

```
ansible-playbook -vvv -pb_role_conformance_test.yaml
```
    ---
    - hosts: helper
      connection: local
      gather_facts: false
      roles:
      - role: role_conformance_test

License
-------

BSD

Author Information
------------------

@canit00
