---
title: AppArmor 3.0.8 released
date: 2022-11-21
---

AppArmor 3.0.8 was released 2022-11-21.

# Introduction

AppArmor 3.0.8 fixes a couple errors discovered in AppArmor 3.0.7 after release. It is a maintenance release of the user space components of the AppArmor security project. The kernel portion of the project is maintained and pushed separately.

This version of the userspace should work with all kernel versions from
2.6.15 and later (some earlier version of the kernel if they have the
apparmor patches applied).

The kernel portion of the project is maintained and pushed separately.


# Obtaining the Release

There are two ways to obtain this release either through gitlab or a tarball in launchpad. 

**Important note:** the gitlab release tarballs differ from the launchpad release tarballs. The launchpad release tarball has a couple processing steps already performed:

* libapparmor `autogen.sh` is already done, meaning distros only need to use ./configure in their build setup
* the docs for everything but libapparmor have already been built

### gitlab
- https://gitlab.com/apparmor/apparmor/-/releases/v3.0.8

### Launchpad

  -   <https://launchpad.net/apparmor/3.0/3.0.8/+download/apparmor-3.0.8.tar.gz>
  -   sha256sum: dfa0083d62bb469be7125da590f46ad1a2831e3a7beeffaaeadfc2fee8460e5c
  -   signature: <https://launchpad.net/apparmor/3.0/3.0.8/+download/apparmor-3.0.8.tar.gz.asc>

# Changes in this Release

These release notes cover all changes between 3.0.7 (0ead606d9e608801f45e13a34358036135470729) and 3.0.8 (474a12ebe86bb9314e482f918c589b484fd9ec2a) on [apparmor-3.0 branch](https://gitlab.com/apparmor/apparmor/tree/apparmor-3.0).


## libapparmor

- Hardcode and check the expected libapparmor.so name/number ([MR:915](https://gitlab.com/apparmor/apparmor/-/merge_requests/915), [AABUG:266](https://gitlab.com/apparmor/apparmor/-/issues/266))
- allow parsing of logs with 0x1d + uppercase items ([MR:940](https://gitlab.com/apparmor/apparmor/-/merge_requests/940), [AABUG:271](https://gitlab.com/apparmor/apparmor/-/issues/271))

## Policy Compiler (a.k.a apparmor_parser)
- fix DISTRO variable in Makefile ([MR:928](https://gitlab.com/apparmor/apparmor/-/merge_requests/928))

## Utils
- Use `open` instead of `codecs.open` to fix line breaks ([MR:945](https://gitlab.com/apparmor/apparmor/-/merge_requests/945))
- prevent crash in mergeprof by Using string startswith() and endswith() methods ([MR:931](https://gitlab.com/apparmor/apparmor/-/merge_requests/931))


## Policy

#### abstractions
- base
  - Allow access to possible cpus for glibc-2.36 ([AABUG:267](https://gitlab.com/apparmor/apparmor/-/issues/267), [LP:1989073](https://bugs.launchpad.net/bugs/1989073))
- nameservice
  - Adds WSL programmatic management of /etc/resolv.conf ([MR:935](https://gitlab.com/apparmor/apparmor/-/merge_requests/935)) 
- kde
  - update for kwinrc, kdedefaults/* files ([MR:936](https://gitlab.com/apparmor/apparmor/-/merge_requests/936))

#### profiles
- dnsmasq
  - Add missing r permissions for libvirt_leaseshelper ([MR:905](https://gitlab.com/apparmor/apparmor/-/merge_requests/905), [BOO:1202161](https://bugzilla.opensuse.org/show_bug.cgi?id=1202161))
  - allow paths for podman dnsname plugin in rootless mode ([MR:909](https://gitlab.com/apparmor/apparmor/-/merge_requests/909))
  - Allow reading /sys/devices/system/cpu/possible ([MR:917](https://gitlab.com/apparmor/apparmor/-/merge_requests/917), [BOO:1202849](https://bugzilla.opensuse.org/show_bug.cgi?id=1202849)) 
- php
  - permit php-fpm pid files directly under run/ ([MR:914](https://gitlab.com/apparmor/apparmor/-/merge_requests/914), [AABUG:267](https://gitlab.com/apparmor/apparmor/-/issues/267))
- samba
  - allow mkdir /var/cache/samba/printing/ ([MR:937](https://gitlab.com/apparmor/apparmor/-/merge_requests/937), [LP:1993572](https://bugs.launchpad.net/bugs/1993572))
  - Update to support latest version ([MR:926](https://gitlab.com/apparmor/apparmor/-/merge_requests/926), [LP:1990692](https://bugs.launchpad.net/bugs/1990692))
- syslog-ng
  - allow reading *.journal in flatter directory structure ([MR:932](https://gitlab.com/apparmor/apparmor/-/merge_requests/932))


## Tests
- Fix utils testing of parser. Set (instead of compare) exresult ([MR:907](https://gitlab.com/apparmor/apparmor/-/merge_requests/907))
