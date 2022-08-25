---
title: AppArmor 3.0.7 released
date: 2022-08-09
---

AppArmor 3.0.7 fixes a build error in AppArmor 3.0.6. It is a maintenance release of the user space components of the AppArmor security project. The kernel portion of the project is maintained and pushed separately.

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
- https://gitlab.com/apparmor/apparmor/-/releases/v3.0.7

### Launchpad

  -   <https://launchpad.net/apparmor/3.0/3.0.7/+download/apparmor-3.0.7.tar.gz>
  -   sha256sum: f7063637d7523a28a59696f89e878d9942985bf828194d4c4bae594bec57e2d1
  -   signature: <https://launchpad.net/apparmor/3.0/3.0.7/+download/apparmor-3.0.7.tar.gz.asc>

# Changes in this Release

These release notes cover all changes between 3.0.6 (702c2823257e94bc926f2a4c69c66e613fd40d74) and 3.0.7 (0ead606d9e608801f45e13a34358036135470729) on [apparmor-3.0 branch](https://gitlab.com/apparmor/apparmor/tree/apparmor-3.0).


- Fix setuptools version detection in buildpath.py
    ([MR:904](https://gitlab.com/apparmor/apparmor/-/merge_requests/904),
    [AABUG:39](https://gitlab.com/apparmor/apparmor/-/issues/39),
    [AABUG:259](https://gitlab.com/apparmor/apparmor/-/issues/259))
