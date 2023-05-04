# CI/CD Templates

This repository contains a set of gitlab-ci templates.
These range from gitlab-ci services, to jobs, to job templates, to full pipelines, and some utilities.


## Index

Find a list of all available content beneath. Specific documenation and usage of any job, template, ... can be found in the docstring header of the implementation (cfr listed links)

### Jobs, Job Templates, Job Utilities

- [building/containers/kaniko](./jobs/building/containers/kaniko.gitlab-ci.yml)
  Job Template: Build Dockerfile projects and push to local registry
- [building/containers/kaniko-matrix](./building/containers/kaniko-matrix.gitlab-ci.yml)
  Job Template: Build Dockerfile projects parallel over a currated set of supported OSes
- [releasing/semantic-release](./jobs/releasing/semantic-release.gitlab-ci.yml)
  Job: Create a semantic versioned gitlab release + git tag based on conventional commits
- [testing/ansible/ansible-molecule](./testing/ansible/ansible-molecule.gitlab-ci.yml)
  Job: Run Molecule tool over a list of scenario's to test an ansible role
- [testing/ansible/ansible-test](./jobs/testing/ansible/ansible-test.gitlab-ci.yml)
  Jobs: Run different steps using ansible-test tool
    - ansible-test sanity: linting basically (python, yaml, ...)
    - ansible-test unit: unit test your python based ansible modules/plugins/...
- [utils/gitlab-http-access](./jobs/utils/gitlab-http-access.gitlab-ci.yml)
  Job Utility: Relay any gitlab url to an authenticated (default using CI_JOB_TOKEN) http url
- [utils/supported-os-matrix](./jobs/utils/supported-os-matrix.gitlab-ci.yml)
  Job Utility: Provides parallel parameters to run over a currated set of support OSes (centos7, rockylinux8 and 9 eg)


### Pipelines, Pipeline Templates

- [ansible](./pipelines/ansible.gitlab-ci.yml)
  Pipeline: Run all related steps to building, testing and releasing ansible content


### Services

- [docker-dind](./services/docker-dind.gitlab-ci.yml)
  Service Template: Add to jobs to run docker as a service to use during eg test steps (testcontainers, ansible molecule, ...)
