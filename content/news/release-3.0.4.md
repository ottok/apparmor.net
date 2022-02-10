---
title: AppArmor 3.0.4 released
date: 2022-02-09
---

AppArmor 3.0.4 fixes a build error in AppArmor 3.0.3 that could cause AppArmor builds to fail during tests in some build environments. It is a maintenance release of the user space components
of the AppArmor security project. The kernel portion of the project
is maintained and pushed separately.

This version of the userspace should work with all kernel versions from
2.6.15 and later (some earlier version of the kernel if they have the
apparmor patches applied).

The kernel portion of the project is maintained and pushed separately.

# Notes

* while Link Time Optimization (LTO) has been fixed for some systems there are still some known issues which may result in build failures on some systems. See https://gitlab.com/apparmor/apparmor/-/issues/214

# Obtaining the Release

There are two ways to obtain this release either through gitlab or a tarball in launchpad. 

**Important note:** the gitlab release tarballs differ from the launchpad release tarballs. The launchpad release tarball has a couple processing steps already performed:

* libapparmor `autogen.sh` is already done, meaning distros only need to use ./configure in their build setup
* the docs for everything but libapparmor have already been built

### gitlab
- https://gitlab.com/apparmor/apparmor/-/releases/v3.0.4

### Launchpad

  -   <https://launchpad.net/apparmor/3.0/3.0.4/+download/apparmor-3.0.4.tar.gz>
  -   sha256sum: 09bf48d7a171f9790c39a1404bad105a788934cfe77b7490c7f5c63c2576b725
  -   signature: <https://launchpad.net/apparmor/3.0/3.0.4/+download/apparmor-3.0.4.tar.gz.asc>

# Changes in this Release

These release notes cover all changes between 3.0.3 (1a6c042ac608a6fd2111bd3338d3dca1529a33f9) and 3.0.4 (939530b2b89ee26bef52ccfe3d271629f4da097d) [apparmor-3.0 branch](https://gitlab.com/apparmor/apparmor/tree/apparmor-3.0).


## Init
- make xargs invocation busybox-compatible ([MR:828](https://gitlab.com/apparmor/apparmor/-/merge_requests/828))

## Library
- fix log parsing for socklogd ([MR:799](https://gitlab.com/apparmor/apparmor/-/merge_requests/799), [AABUG:196](https://gitlab.com/apparmor/apparmor/-/issues/196))
- fix memory leaks in logparsing ([MR:799](https://gitlab.com/apparmor/apparmor/-/merge_requests/799))
- fix debug build of log parsing ([MR:799](https://gitlab.com/apparmor/apparmor/-/merge_requests/799))
- replace deprecated distutils with setuptools ([MR:813](https://gitlab.com/apparmor/apparmor/-/merge_requests/813), [AABUG:202](https://gitlab.com/apparmor/apparmor/-/issues/202))
- Fix ruby 3.1 interface build ([AABUG:206](https://gitlab.com/apparmor/apparmor/-/issues/206))
- fix some building with link time optimization failures (lto) ([MR:831](https://gitlab.com/apparmor/apparmor/-/merge_requests/831), [AABUG:214](https://gitlab.com/apparmor/apparmor/-/issues/214))

## Policy Compiler (a.k.a apparmor_parser)
- Fix unknown state condition in RLIMIT rule parsing ([MR:803](https://gitlab.com/apparmor/apparmor/-/merge_requests/803))
- Ensure new af_names are supported ([MR:808](https://gitlab.com/apparmor/apparmor/-/merge_requests/808), [AABUG:195](https://gitlab.com/apparmor/apparmor/-/issues/195))
- add support for ```mctp``` address family ([MR:832](https://gitlab.com/apparmor/apparmor/-/merge_requests/832))

## Utils
- add support for new and future python versions ([MR:795](https://gitlab.com/apparmor/apparmor/-/merge_requests/795), [AABUG:193](https://gitlab.com/apparmor/apparmor/-/issues/193))
- add support for ```mctp``` address family ([MR:832](https://gitlab.com/apparmor/apparmor/-/merge_requests/832))

- aa-notify
  - Avoid aa-notify crash on log events without operation= ([MR:797](https://gitlab.com/apparmor/apparmor/-/merge_requests/797), Fixes: [AABUG:194](https://gitlab.com/apparmor/apparmor/-/issues/194))
  - support reading s390x and aarch64 wtmp files ([MR:809](https://gitlab.com/apparmor/apparmor/-/merge_requests/809), [BOO:1181155](https://bugzilla.opensuse.org/show_bug.cgi?id=1181155))
- aa-unconfined
  - Improve fallback handling to attr/current ([MR:801](https://gitlab.com/apparmor/apparmor/-/merge_requests/801), [AABUG:199](https://gitlab.com/apparmor/apparmor/-/issues/199))
- aa-features-abi
  - Fix handling of -f option ([MR:804](https://gitlab.com/apparmor/apparmor/-/merge_requests/804))
  - Fix fd resource leak ([MR:804](https://gitlab.com/apparmor/apparmor/-/merge_requests/804))
- aa-status
  - fix crash due to \n in profile name ([MR:824](https://gitlab.com/apparmor/apparmor/-/merge_requests/824), [AABUG:211](https://gitlab.com/apparmor/apparmor/-/issues/211))

## Policy

#### abstractions
- Add GTK abstraction ([MR:825](https://gitlab.com/apparmor/apparmor/-/merge_requests/825), [AABUG:168](https://gitlab.com/apparmor/apparmor/-/issues/168), [AABUG:65](https://gitlab.com/apparmor/apparmor/-/issues/65))
- python
  - update to support python 3.10  ([MR:783](https://gitlab.com/apparmor/apparmor/-/merge_requests/783), [AABUG:187](https://gitlab.com/apparmor/apparmor/-/issues/187))
  - merge /usr/ and /usr/local rules ([MR:814](https://gitlab.com/apparmor/apparmor/-/merge_requests/814))
  - allow reading .so files ([MR:814](https://gitlab.com/apparmor/apparmor/-/merge_requests/814))
  - allow directory listings in .../site-packages/ ([MR:814](https://gitlab.com/apparmor/apparmor/-/merge_requests/814))
  - allow reading various metadata files ([MR:814](https://gitlab.com/apparmor/apparmor/-/merge_requests/814))

- samba
  - allow use of /run/lock/samba ([MR:805](https://gitlab.com/apparmor/apparmor/-/merge_requests/805))
- video
  - fix video4linux dir permission ([MR:791](https://gitlab.com/apparmor/apparmor/-/merge_requests/791))
  - allow ldb2 paths ([MR:821](https://gitlab.com/apparmor/apparmor/-/merge_requests/821), [BOO:1192684](https://bugzilla.opensuse.org/show_bug.cgi?id=1192684))
- ssl
  - allow access to /etc/ssl/{engdef,engines.d} ([MR:818](https://gitlab.com/apparmor/apparmor/-/merge_requests/818))


#### profiles
- avahi-daemon
  - Add missing /proc permissions ([MR:811](https://gitlab.com/apparmor/apparmor/-/merge_requests/811), [AABUG:203](https://gitlab.com/apparmor/apparmor/-/issues/203))
- chrome
  - fix opening links (https://gitlab.com/apparmor/apparmor/-/merge_requests/830)
- dnsmasq
  - add support for podman dnsname plugin ([MR:800](https://gitlab.com/apparmor/apparmor/-/merge_requests/800), [BOO:1190271](https://bugzilla.opensuse.org/show_bug.cgi?id=1190271))
- samba
  - Add profile for samba-bgqd ([BOO:1191532](https://bugzilla.opensuse.org/show_bug.cgi?id=1191532), [MR:807](https://gitlab.com/apparmor/apparmor/-/merge_requests/807))
- samba-bgqd
  - fix mmap violation ([MR:819](https://gitlab.com/apparmor/apparmor/-/merge_requests/819))


# Additional Note

There is a semantic change in the 4.8 kernel (commit
9f834ec18defc369d73ccf9e87a2790bfa05bf46) that affects apparmor policy
enforcement. Specifically it affects when the m permission bit is
checked for elf binary executables. Policy and tests within apparmor
2.12 and later have been updated to support running on pre 4.8 and 4.8+ kernels.
