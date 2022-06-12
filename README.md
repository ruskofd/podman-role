<p><img src="https://podman.io/images/podman.svg" alt="podman-logo" title="podman" align="top" height=120 /></p>

***Podman** is a daemonless container engine for developing, managing, and running Open Container Initiative (OCI) containers and container images on your Linux System.*

### General informations

This Ansible role is designed to deploy and manage Podman on target servers. 

**Table of Contents**

  - [Roles variables](#role-variables)
  - [Examples](#examples)
  - [Install and use this role](#install-and-use-this-role)

**Supported Platforms**

  - Fedora 36

**References**

  -  Podman : https://podman.io/

### Role variables

The role variables are documented [HERE](docs/variables.md)

### Examples

You can find some configurations examples [HERE](docs/examples.md)

### Install and use this role

* Install the role using the command-line :

  ```shell
  $ ansible-galaxy role install git+https://github.com/ruskofd/podman-role.git
  ```

* Install the collection in your projects using a `requirements.yml` file and `ansible-galaxy` command-line :

  ```YAML
  $ cat requirements.yml
  ---
  roles:
    - name: podman
      src: https://github.com/ruskofd/podman-role.git
      scm: git
      version: '1.0.0'

  $ ansible-galaxy install-f -r requirements.yml
  ```

* Once the role is installed, you can use it in your playbooks :

  ```yaml
  - name: Install Podman
    hosts: podman
    roles:
      - role: podman
  ```
