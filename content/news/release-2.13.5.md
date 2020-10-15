---
title: AppArmor 2.13.5 released
date: 2020-10-15
---

AppArmor 2.13.5 is a maintenance release of the user space components
of the AppArmor security project. The kernel portion of the project
is maintained and pushed separately.

This version of the userspace should work with all kernel versions from
2.6.15 and later (some earlier version of the kernel if they have the
apparmor patches applied). And supports features released in the 4.18
kernel and ubuntu 18.04 kernel with the apparmor 3 development patches.

# Important Note

- gitlab release tarballs: Differ from the launchpad release tarballs. The both start from the same commit (tagged v2.13.5) however the launchpad release tarball has a couple processing steps already performed:
  - libapparmor ```autogen.sh``` is already done, meaning distros only need to use ./configure in their build setup
  - the docs for everything but libapparmor have already been built

# Obtaining the Release

There are two ways to obtain this release either through gitlab or a tarball in launchpad. Important note: the gitlab release tarballs: Differ from the launchpad release tarballs. The launchpad release tarball has a couple processing steps already performed:
  - libapparmor ```autogen.sh``` is already done, meaning distros only need to use ./configure in their build setup
  - the docs for everything but libapparmor have already been built

### gitlab release
- https://gitlab.com/apparmor/apparmor/-/releases/v2.13.5

### Launchpad Tarball
-   <https://launchpad.net/apparmor/2.13/2.13.5/+download/apparmor-2.13.5.tar.gz>
-   sha256sum: 637e2a14d844e53e0f0b31dc8fe8821f7bb36908c709ccc23e29033053caa717
-   signature: <https://launchpad.net/apparmor/2.13/2.13.5/+download/apparmor-2.13.5.tar.gz.asc>
