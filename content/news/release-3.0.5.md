---
title: AppArmor 3.0.5 released
date: 2022-07-25
---

AppArmor 3.0.5 fixes a build error in AppArmor 3.0.4 that could cause AppArmor builds to fail during tests in some build environments. It is a maintenance release of the user space components
of the AppArmor security project. The kernel portion of the project
is maintained and pushed separately.

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
- https://gitlab.com/apparmor/apparmor/-/releases/v3.0.5

### Launchpad

  -   <https://launchpad.net/apparmor/3.0/3.0.5/+download/apparmor-3.0.5.tar.gz>
  -   sha256sum: 
  -   signature: <https://launchpad.net/apparmor/3.0/3.0.5/+download/apparmor-3.0.5.tar.gz.asc>

# Changes in this Release

These release notes cover all changes between 3.0.4 (939530b2b89ee26bef52ccfe3d271629f4da097d) and 3.0.5 (704c82c57414bcbf7d7b698605887fb515e5b427) [apparmor-3.0 branch](https://gitlab.com/apparmor/apparmor/tree/apparmor-3.0).


## Init
- Make the systemd unit a no-op in containers with no internal policy ([MR:840](https://gitlab.com/apparmor/apparmor/-/merge_requests/840), [LP:978297](https://bugs.launchpad.net/bugs/978297))
- Import profile-load script from Debian ([MR:841](https://gitlab.com/apparmor/apparmor/-/merge_requests/841), [LP:1058356](https://bugs.launchpad.net/bugs/1058356))

## Library
- fix handling of failed symlink traversal ([MR:850](https://gitlab.com/apparmor/apparmor/-/merge_requests/850), [AABUG:215](https://gitlab.com/apparmor/apparmor/-/issues/215))

## Policy Compiler (a.k.a apparmor_parser)
- fix min length calculation for inverse character sets ([MR:872](https://gitlab.com/apparmor/apparmor/-/merge_requests/872))
- fix missing <cstdint> include dependency ([MR:882](https://gitlab.com/apparmor/apparmor/-/merge_requests/882))
- fix building with link time optimization (lto) ([MR:851](https://gitlab.com/apparmor/apparmor/-/merge_requests/851), [AABUG:214](https://gitlab.com/apparmor/apparmor/-/issues/214))

## Utils
- aa-remove-unknown: abort on parser failure ([MR:859](https://gitlab.com/apparmor/apparmor/-/merge_requests/859))
- aa-notify
  - Add .desktop file for aa-notify ([MR:839](https://gitlab.com/apparmor/apparmor/-/merge_requests/839))
  - Drop superfluous shebang from python module ([MR:846](https://gitlab.com/apparmor/apparmor/-/merge_requests/846))
 - Fix inconsistent return length in _run_tests() ([MR:891](https://gitlab.com/apparmor/apparmor/-/merge_requests/891))


## Policy

#### abstractions
- apache2-common
  - allow other processes to trace the hats that include the abstraction ([MR:852](https://gitlab.com/apparmor/apparmor/-/merge_requests/852), [debug1003153](https://bugs.debian.org/1003153))
- gtk
  - add support for gtk4. ([MR:857](https://gitlab.com/apparmor/apparmor/-/merge_requests/857))
- ibus
  - Allow access to socket directory used by recent ibus-daemon ([MR:837](https://gitlab.com/apparmor/apparmor/-/merge_requests/837))
- mesa
  - fix device query access ([MR:879](https://gitlab.com/apparmor/apparmor/-/merge_requests/879))
- nss-systemd
  - Allow access for systemd-machined names ([MR:861](https://gitlab.com/apparmor/apparmor/-/merge_requests/861), [LP:1964325](https://bugs.launchpad.net/bugs/1964325))
- php
  - add missing config accesses ([MR:876](https://gitlab.com/apparmor/apparmor/-/merge_requests/876), [AABUG:229](https://gitlab.com/apparmor/apparmor/-/issues/229), [BOO:1186267](https://bugzilla.opensuse.org/show_bug.cgi?id=1186267))
- samba
  - quiet noise setsockopt calls ([MR:867](https://gitlab.com/apparmor/apparmor/-/merge_requests/867))
- snap_browsers
  - add permissions required due to updates on snaps ([MR:877](https://gitlab.com/apparmor/apparmor/-/merge_requests/877))
- ssh_certs
  - extend pki/trust directories ([MR:864](https://gitlab.com/apparmor/apparmor/-/merge_requests/864))

#### profiles
- dovecot
  - add missing stat access ([MR:881](https://gitlab.com/apparmor/apparmor/-/merge_requests/881), [BOO:1199535](https://bugzilla.opensuse.org/show_bug.cgi?id=1199535))
  - Allow dovecot to use all signals ([MR:865](https://gitlab.com/apparmor/apparmor/-/merge_requests/865))
- samba
  - support paths used by Arch Linux ([MR:883](https://gitlab.com/apparmor/apparmor/-/merge_requests/883))
  - add missing mmaps for aarch64 ([MR:880](https://gitlab.com/apparmor/apparmor/-/merge_requests/880), [BOO:1198309](https://bugzilla.opensuse.org/show_bug.cgi?id=1198309))
  - add profiles to support samba-4.16 new dcerpc subsystem ([MR:871](https://gitlab.com/apparmor/apparmor/-/merge_requests/871))
  - Fix read access denied on /proc/*/fd ([MR:860](https://gitlab.com/apparmor/apparmor/-/merge_requests/860))
  - allow reading openssl.cnf ([MR:862](https://gitlab.com/apparmor/apparmor/-/merge_requests/862), [BOO:1195463](https://bugzilla.opensuse.org/show_bug.cgi?id=1195463))
  - allow reading under /usr/share/samba ([MR:853](https://gitlab.com/apparmor/apparmor/-/merge_requests/853))
  - include snippet generated at runtime on Debian and openSUSE ([MR:838](https://gitlab.com/apparmor/apparmor/-/merge_requests/838))
  - support paths used by Arch Linux ([MR:883](https://gitlab.com/apparmor/apparmor/-/merge_requests/883))
- statd
  - add missing config and hosts_access ([MR:866](https://gitlab.com/apparmor/apparmor/-/merge_requests/866))
- syslogd
  - update to support inetutils-syslogd ([MR:888](https://gitlab.com/apparmor/apparmor/-/merge_requests/888))

## Tests
- parser - error out on unexpected success ([MR:868](https://gitlab.com/apparmor/apparmor/-/merge_requests/868))
- make test-aa-notify test_help_contents () less strict ([MR:848](https://gitlab.com/apparmor/apparmor/-/merge_requests/848), [AABUG:220](https://gitlab.com/apparmor/apparmor/-/issues/220), [AABUG:220](https://gitlab.com/apparmor/apparmor/-/issues/220))
- python tests - Support setuptools >= 61.2 in Python  ([MR:899](https://gitlab.com/apparmor/apparmor/-/merge_requests/899), [HUBMR:3258](https://github.com/pypa/setuptools/pull/3258)/commits/1c23f5e1e4b18b50081cbabb2dea22bf345f5894)


# Additional Note

There is a semantic change in the 4.8 kernel (commit
9f834ec18defc369d73ccf9e87a2790bfa05bf46) that affects apparmor policy
enforcement. Specifically it affects when the m permission bit is
checked for elf binary executables. Policy and tests within apparmor
2.12 and later have been updated to support running on pre 4.8 and 4.8+ kernels.
