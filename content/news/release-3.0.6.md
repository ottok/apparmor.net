---
title: AppArmor 3.0.6 released
date: 2022-08-01
---

AppArmor 3.0.6 fixes a couple errors discovered in AppArmor 3.0.5 after release. It is a maintenance release of the user space components of the AppArmor security project. The kernel portion of the project is maintained and pushed separately.

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
- https://gitlab.com/apparmor/apparmor/-/releases/v3.0.6

### Launchpad

  -   <https://launchpad.net/apparmor/3.0/3.0.6/+download/apparmor-3.0.6.tar.gz>
  -   sha256sum: 0f4c599ee4864e4e412e18133a3b5990f9f81ab6ba75f0f351f024bb722fa368
  -   signature: <https://launchpad.net/apparmor/3.0/3.0.6/+download/apparmor-3.0.6.tar.gz.asc>

# Changes in this Release

These release notes cover all changes between 3.0.6 (704c82c57414bcbf7d7b698605887fb515e5b427) and 3.0.6 (702c2823257e94bc926f2a4c69c66e613fd40d74) on [apparmor-3.0 branch](https://gitlab.com/apparmor/apparmor/tree/apparmor-3.0).


## Policy Compiler (a.k.a apparmor_parser)
- fix LTO build ([MR:901](https://gitlab.com/apparmor/apparmor/-/merge_requests/901), [AABUG:214](https://gitlab.com/apparmor/apparmor/-/issues/214))

## Policy

#### abstractions
- exo-open:
  - Remove dbus deny rule ([MR:884](https://gitlab.com/apparmor/apparmor/-/merge_requests/884))

## Tests
- dirtest.sh: don't rely on apparmor_parser -N's output sort order to be deterministic ([MR:900](https://gitlab.com/apparmor/apparmor/-/merge_requests/900))
