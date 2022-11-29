---
title: AppArmor 3.1.2 released
date: 2022-11-07
---

AppArmor 3.1.2 was released 2022-11-07.

# Introduction

AppArmor 3.1.2 is a bug fix release of the user space components of the AppArmor security project. The kernel portion of the project is maintained and pushed separately.

This version of the userspace should work with all kernel versions from
2.6.15 and later (some earlier version of the kernel if they have the
apparmor patches applied).


# Obtaining the Release

There are two ways to obtain this release either through gitlab or a tarball in launchpad. 

**Important note:** the gitlab release tarballs differ from the launchpad release tarballs. The launchpad release tarball has a couple processing steps already performed:

* libapparmor `autogen.sh` is already done, meaning distros only need to use ./configure in their build setup
* the docs for everything but libapparmor have already been built

### gitlab
- https://gitlab.com/apparmor/apparmor/-/releases/v3.1.2

### Launchpad
  -   <https://launchpad.net/apparmor/3.1/3.1.2/+download/apparmor-3.1.2.tar.gz>
  -   sha256sum: 7cbd0b2f6393abf57acaf25dc2b32b2ae197c0b5b0d661e14be46127df93a5eb
  -   signature: <https://launchpad.net/apparmor/3.1/3.1.2/+download/apparmor-3.1.2.tar.gz.asc>
  -   signature sha256sum: 7cd2a44a695caf906f3328d1b654c65a454737f6

# Changes in this Release

These release notes cover all changes between 3.1.1 (ea127f13cd2c58ae883fb7c87a3ad91317a55c2d) ) and 3.1.2 (1fe80c0f85db4a67771ea506b1ae6d5626d474b1) on the [apparmor-3.1 branch](https://gitlab.com/apparmor/apparmor/tree/apparmor-3.1.


## Library

- Hardcode and check the expected libapparmor.so name/number ([MR:915](https://gitlab.com/apparmor/apparmor/-/merge_requests/915), [AABUG:266](https://gitlab.com/apparmor/apparmor/-/issues/266))
- allow parsing of logs with 0x1d + uppercase OUID, FSUID ([MR:940](https://gitlab.com/apparmor/apparmor/-/merge_requests/940), [AABUG:271](https://gitlab.com/apparmor/apparmor/-/issues/271))


## Policy Compiler (a.k.a apparmor_parser)

- fix DISTRO variable in Makefile ([MR:928](https://gitlab.com/apparmor/apparmor/-/merge_requests/928))


## Utils

- Prevent crash on log entries for non-existing profile ([MR:919](https://gitlab.com/apparmor/apparmor/-/merge_requests/919))


## Policy

#### abstractions

- kde
  - update for kwinrc, kdedefaults/* files ([MR:936](https://gitlab.com/apparmor/apparmor/-/merge_requests/936))


#### profiles

- syslog-ng
  - allow reading *.journal in flatter directory structure ([MR:932](https://gitlab.com/apparmor/apparmor/-/merge_requests/932))
- samba
  - Update to support latest version ([MR:926](https://gitlab.com/apparmor/apparmor/-/merge_requests/926), [LP:1990692](https://bugs.launchpad.net/bugs/1990692))
  - allow mkdir /var/cache/samba/printing/ ([MR:937](https://gitlab.com/apparmor/apparmor/-/merge_requests/937), [LP:1993572](https://bugs.launchpad.net/bugs/1993572))
