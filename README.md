Ansible Role: Jenkins Jobs
=========

[![Build Status](https://travis-ci.org/fubarhouse/ansible-role-jenkinsjobs.svg?branch=master)](https://travis-ci.org/fubarhouse/ansible-role-golang)
![stability-experimental](https://img.shields.io/badge/stability-experimental-orange.svg)
[![Ansible Galaxy](https://img.shields.io/ansible/role/0000.svg)](https://galaxy.ansible.com/fubarhouse/jenkinsjobs)
[![MIT licensed](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/fubarhouse/ansible-role-jenkinsjobs/master/LICENSE)

An Ansible role for deploying Jenkins job configuration files!

Requirements
------------

* git

*Note: As this role does not communicate with Jenkins, Jenkins is not required.*

Role Variables
--------------

```yaml
# The path to the directory that stores Jenkins jobs.
jenkins_jobs_directory: /var/lib/jenkins/jobs
# The repository that contains your Jenkins jobs
jenkins_repository: git@github.org/user/repo.git
# The path to where the repository should be cloned to
jenkins_tempdir: /tmp/jenkins_jobs
# All of your desired Jenkins jobs in a structured format
jenkins_jobs:
  # The name associated to the job.
  - name: Build site
    # The folder name where configuration files exist.
    folder: Build site
    # The state of the job, either present or absent.
    state: present
    # An index of all the files you need managed.
    files:
      - config.yml
```

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: all
  roles:
     - role: fubarhouse.jenkinsjobs
```

License
-------

MIT

Author Information
------------------


This role was created in 2017 by [Karl Hepworth](https://twitter.com/fubarhouse).
