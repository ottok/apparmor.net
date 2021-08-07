---
title: AppArmor 3.0.3 released
date: 2021-08-07
---

AppArmor 3.0.3 fixes a build error in AppArmor 3.0.2 that could cause AppArmor builds to fail during tests in some build environments. It is a maintenance release of the user space components
of the AppArmor security project. The kernel portion of the project
is maintained and pushed separately.

This version of the userspace should work with all kernel versions from
2.6.15 and later (some earlier version of the kernel if they have the
apparmor patches applied).

The kernel portion of the project is maintained and pushed separately.


# Obtaining the Release

There are two ways to obtain this release either through gitlab or a tarball in launchpad. Important note: the gitlab release tarballs differ from the launchpad release tarballs. The launchpad release tarball has a couple processing steps already performed:

* libapparmor `autogen.sh` is already done, meaning distros only need to use ./configure in their build setup
* the docs for everything but libapparmor have already been built

### gitlab
- https://gitlab.com/apparmor/apparmor/-/releases/v3.0.3

### Launchpad

  -   <https://launchpad.net/apparmor/3.0/3.0.3/+download/apparmor-3.0.3.tar.gz>
  -   sha256sum: 153db05d8f491e0596022663c19fb1166806cb473b3c6f0a7279feda2ec25a59
  -   signature: <https://launchpad.net/apparmor/3.0/3.0.3/+download/apparmor-3.0.3.tar.gz.asc>

# Changes in this Release

These release notes cover all changes between 3.0.2 (59ec31bcb3c3ce186de5c6d97c8928ac8878a8af) and 3.0.3 (1a6c042ac608a6fd2111bd3338d3dca1529a33f9) [apparmor-3.0 branch](https://gitlab.com/apparmor/apparmor/tree/apparmor-3.0).


## Tests
- parser
  - sort dir traversal to match how library traverses dirs. picked from ([MR:775](https://gitlab.com/apparmor/apparmor/-/merge_requests/775))

# Note

There is a semantic change in the 4.8 kernel (commit
9f834ec18defc369d73ccf9e87a2790bfa05bf46) that affects apparmor policy
enforcement. Specifically it affects when the m permission bit is
checked for elf binary executables. Policy and tests within apparmor
2.12 and later have been updated to support running on pre 4.8 and 4.8+ kernels.

