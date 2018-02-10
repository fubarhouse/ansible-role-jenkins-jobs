Ansible Role: Jenkins Jobs
=========

[![Build Status](https://travis-ci.org/fubarhouse/ansible-role-jenkins-jobs.svg?branch=master)](https://travis-ci.org/fubarhouse/ansible-role-jenkins-jobs)
![stability-stable](https://img.shields.io/badge/stability-stable-green.svg)
[![Ansible Galaxy](https://img.shields.io/ansible/role/23791.svg)](https://galaxy.ansible.com/fubarhouse/jenkins-jobs)
[![MIT licensed](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/fubarhouse/ansible-role-jenkinsjobs/master/LICENSE)

An Ansible role for deploying Jenkins job configuration files!

* Clone a repository containing a set of configuration files.
* Copy the job configuration files from the job folders to their destination.
* Copy any arbitrary configuration files to their destination.
* Jobs have a desired state, either present or absent.
* Jobs affected by this role are explicitly stated, so you know what to expect.

Requirements
------------

* git

*Notes*:

* As this role does not communicate directly with Jenkins, Jenkins is not required.
* This role clones a repository and copies expected file paths to a destination, nothing more.

Role Variables
--------------

```yaml
# The path to the directory that stores Jenkins 'jobs' folder (the parent of the jobs folder).
jenkins_directory: /var/lib/jenkins
# The owner of the configured files
jenkins_job_owner: root
# The group of the configured files
jenkins_job_group: root
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
# A structured list of configuration files
jenkins_config_files:
  # The name of the file
  - filename: config.xml
  # The desired state of that file, either present or absent
    state: present
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
    - role: fubarhouse.jenkins-jobs
```

License
-------

MIT

Author Information
------------------

This role was conceived in 2017 and originally written in 2018 by [Karl Hepworth](https://twitter.com/fubarhouse).
