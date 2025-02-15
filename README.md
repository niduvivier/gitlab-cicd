# CI/CD Templates

This repository contains a set of gitlab-ci templates.
These range from gitlab-ci services, to jobs, to job templates, to full pipelines, and some utilities.

## Index

Find a list of all available content beneath. Specific documenation and usage of any job, template, ... can be found in the docstring header of the implementation (cfr listed links)

### Jobs, Job Templates, Job Utilities

- [building/containers/kaniko](./jobs/building/containers/kaniko.gitlab-ci.yml)
  Job Template: Build Dockerfile projects and push to local registry
- [building/containers/kaniko-ecr](./jobs/building/containers/kaniko-ecr.gitlab-ci.yml)
  Job Template: Build Dockerfile projects and push to ECR registry
- [building/containers/kaniko-matrix](./building/containers/kaniko-matrix.gitlab-ci.yml)
  Job Template: Build Dockerfile projects parallel over a currated set of supported OSes
- [releasing/semantic-release](./jobs/releasing/semantic-release.gitlab-ci.yml)
  Job: Create a semantic versioned gitlab release + git tag based on conventional commits
- [testing/ansible/ansible-inventory](./testing/ansible/ansible-inventory.gitlab-ci.yml)
  Job Template: Run ansible-invetory and jq to check if an inventory file parses to a correct group structure
- [testing/ansible/ansible-lint](./testing/ansible/ansible-lint.gitlab-ci.yml)
  Job: Run ansible-lint and yamllint tool over ansible content
- [testing/ansible/ansible-molecule](./testing/ansible/ansible-molecule.gitlab-ci.yml)
  Job: Run Molecule tool over a list of scenario's to test an ansible role
- [testing/ansible/ansible-test](./jobs/testing/ansible/ansible-test.gitlab-ci.yml)
  Jobs: Run different steps using ansible-test tool
    - ansible-test sanity: linting basically (python, yaml, ...)
    - ansible-test unit: unit test your python based ansible modules/plugins/...
  WARN: due to recent issues it is not recommended to use this!!
- [testing/qa/sonarqube](./jobs/testing/qa/sonarqube.gitlab-ci.yml)
  Job: Run sonarqube against your project, ith easy to start filled in properties
    additional properties can be provided via a variable or sonar-project.properties file
- [utils/gitlab-http-access](./jobs/utils/gitlab-http-access.gitlab-ci.yml)
  Job Utility: Relay any gitlab url to an authenticated (default using CI_JOB_TOKEN) http url
- [utils/supported-os-matrix](./jobs/utils/supported-os-matrix.gitlab-ci.yml)
  Job Utility: Provides parallel parameters to run over a currated set of support OSes (centos7, rockylinux8 and 9 eg)
- [utils/aws/aws-assume-role](./jobs/utils/aws/aws-assume-role.gitlab-ci.yml)
  Job Utility: Provides a way of not storeing long lived credentials in Gitlab, though foresee jobs with short lived session credentials
- [utils/aws/aws-ecr-login](./jobs/utils/aws/aws-ecr-login.gitlab-ci.yml)
  Job Utility: Provides a way of retrieving ECR token to authenticate kaniko/docker


### Pipelines, Pipeline Templates

- [ansible](./pipelines/ansible.gitlab-ci.yml)
  Pipeline: Run all related steps to building, testing and releasing ansible content
  WARN: currently ansible-test include has been disabled
- [recommended-test-jobs](./pipelines/recommended-test-jobs.gitlab-ci.yml)
  Pipeline: Run recommended set of tests, mostly in regards to security and code quality


### Services

- [docker-dind](./services/docker-dind.gitlab-ci.yml)
  Service Template: Add to jobs to run docker as a service to use during eg test steps (testcontainers, ansible molecule, ...)
