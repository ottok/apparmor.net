---
title: AppArmor 2.10.6 released
date: 2020-12-08
---

AppArmor 2.10.6 is a maintenance release of the user space components
of the AppArmor security project. The kernel portion of the project
is maintained and pushed separately.

This version of the userspace should work with all kernel versions from
2.6.15 and later (some earlier version of the kernel if they have the
apparmor patches applied).

The kernel portion of the project is maintained and pushed separately.


# Important Note
- This is the last release in the 2.10 series.

# Obtaining the Release

There are two ways to obtain this release either through gitlab or a tarball in launchpad. Important note: the gitlab release tarballs: Differ from the launchpad release tarballs. The launchpad release tarball has a couple processing steps already performed:

* libapparmor `autogen.sh` is already done, meaning distros only need to use ./configure in their build setup

### gitlab
- https://gitlab.com/apparmor/apparmor/-/releases/v2.10.6

### Launchpad

  -   <https://launchpad.net/apparmor/2.10/2.10.6/+download/apparmor-2.10.6.tar.gz>
  -   sha256sum: 751b8df8f8526167d6f3164c6b6d73f2b1398c96458412e6b87058220789f257
  -   signature: <https://launchpad.net/apparmor/2.0/2.10.6/+download/apparmor-2.10.6.tar.gz.asc>

See [Full Release Notes](https://gitlab.com/apparmor/apparmor/-/wikis/Release_Notes_2.10.6) for additional information.
