# InSpec Bootstrapping Profile
[![Project Release](https://img.shields.io/badge/release-v1.0.2-blue.svg)](https://github.com/bonusbits/inspec_bootstrap)
[![CircleCI](https://circleci.com/gh/bonusbits/inspec_bootstrap.svg?style=shield)](https://circleci.com/gh/bonusbits/inspec_bootstrap)
[![Join the chat at https://gitter.im/bonusbits](https://badges.gitter.im/bonusbits/bonusbits.svg)](https://gitter.im/bonusbits?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![GitHub issues](https://img.shields.io/github/issues/bonusbits/inspec_bootstrap.svg)](https://github.com/bonusbits/inspec_bootstrap/issues)

Used to check basic bootstrapping configurations.
These are usually items that come before a configuration manager is utilized.
Which could be specific packages installed such as cfn-init or verifying the version of the configuration manager such as Chef client.

## Standalone Usage

This Compliance Profile requires [InSpec](https://github.com/chef/inspec) for execution:

```
$ git clone https://github.com/bonusbits/inspec_bootstrap.git
$ inspec exec inspec_bootstrap
```

You can also execute the profile directly from Github:

```
$ inspec exec https://github.com/bonusbits/inspec_bootstrap
```

## Kitchen Usage
Add the InSpec Profile to your test suites in the Test Kitchen configuration. 
We only need to pass a chef_version if not the default version.

```yaml
verifier:
  name: inspec
  
suites:
  - name: default
    run_list:
      - recipe[blah]
    verifier:
      inspec_tests:
        - name: bootstrap
          git: https://github.com/bonusbits/inspec_bootstrap.git
      attributes:
        chef_version: 12.18.31
```

## Attributes
### Chef Client
| Attribute      | Type     | Default       |
| :------------- |:-------- | :------------ |
| inspec_chef    | Boolean  | true          |
| chef_version   | String   | 12.19.36      |
