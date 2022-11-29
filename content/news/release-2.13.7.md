---
title: AppArmor 2.13.7 released
date: 2022-11-21
---

AppArmor 2.13.7 was released 2022-11-21.

# Introduction

AppArmor 2.13.7 is a maintenance release of the user space components
of the AppArmor security project. The kernel portion of the project
is maintained and pushed separately.

This version of the userspace should work with all kernel versions from
2.6.15 and later (some earlier version of the kernel if they have the
apparmor patches applied). And supports features released in the 4.18
kernel and ubuntu 18.04 kernel with the apparmor 3 development patches.

# Obtaining the Release

There are two ways to obtain this release either through gitlab or a tarball in launchpad. Important note: the gitlab release tarballs: Differ from the launchpad release tarballs. The launchpad release tarball has a couple processing steps already performed:
  - libapparmor ```autogen.sh``` is already done, meaning distros only need to use ./configure in their build setup
  - the docs for everything but libapparmor have already been built

### gitlab release
- https://gitlab.com/apparmor/apparmor/-/releases/v2.13.7

### Launchpad Tarball
-   <https://launchpad.net/apparmor/2.13/2.13.7/+download/apparmor-2.13.7.tar.gz>
-   sha256sum: 8c6d19ffb8ba13b776f7922a144a7bd7f221592dacec44e51485a784ddd20e09
-   signature: <https://launchpad.net/apparmor/2.13/2.13.7/+download/apparmor-2.13.7.tar.gz.asc>

# Changes in this Release

These release notes cover all changes between 2.13.6 (c16fff8cb487cf150e3e5ad536b7ff2d4cb4f784) and 2.137 (b51a2d271d489763909cfbbb18d7f5826b16e11a) on the [apparmor-2.13 branch](https://gitlab.com/apparmor/apparmor/tree/apparmor-2.13).


## Libapparmor

- Support setuptools >= 61.2 ([MR:910](https://gitlab.com/apparmor/apparmor/-/merge_requests/910), [HUBMR:3258](https://github.com/pypa/setuptools/pull/3258)/commits/1c23f5e1e4b18b50081cbabb2dea22bf345f5894)
- remove deprecation warning for distutils ([MR:908](https://gitlab.com/apparmor/apparmor/-/merge_requests/908))
- fix building with link time optimization (lto) ([MR:831](https://gitlab.com/apparmor/apparmor/-/merge_requests/831), [AABUG:214](https://gitlab.com/apparmor/apparmor/-/issues/214))
- look up python-config using AC_PATH_TOOL ([MR:729](https://gitlab.com/apparmor/apparmor/-/merge_requests/729), [debug984582](https://bugs.debian.org/984582))
- Do not abuse AC_CHECK_FILE ([MR:728](https://gitlab.com/apparmor/apparmor/-/merge_requests/728), [debug984582](https://bugs.debian.org/984582))


## Policy Compiler (a.k.a apparmor\_parser)

- fix rlimit parsing ([MR:803](https://gitlab.com/apparmor/apparmor/-/merge_requests/803))
- fix cache time stamp check to include dir time stamps ([MR:760](https://gitlab.com/apparmor/apparmor/-/merge_requests/760))
- fix filter slashes for link targets ([MR:723](https://gitlab.com/apparmor/apparmor/-/merge_requests/723), [AABUG:153](https://gitlab.com/apparmor/apparmor/-/issues/153))
- fix rule downgrade for unix rules ([MR:700](https://gitlab.com/apparmor/apparmor/-/merge_requests/700), [BOO:1180766](https://bugzilla.opensuse.org/show_bug.cgi?id=1180766))
- fix --jobs so job scaling is applied correctly ([MR:703](https://gitlab.com/apparmor/apparmor/-/merge_requests/703))


## Utils

- Add 'mctp' network domain keyword ([MR:911](https://gitlab.com/apparmor/apparmor/-/merge_requests/911))
- Support setuptools >= 61.2 ([MR:910](https://gitlab.com/apparmor/apparmor/-/merge_requests/910), [HUBMR:3258](https://github.com/pypa/setuptools/pull/3258)/commits/1c23f5e1e4b18b50081cbabb2dea22bf345f5894)
- Use string startswith() and endswith() methods ([MR:931](https://gitlab.com/apparmor/apparmor/-/merge_requests/931))
- Set (instead of compare) exresult ([MR:907](https://gitlab.com/apparmor/apparmor/-/merge_requests/907))
- support new versions of python ([MR:795](https://gitlab.com/apparmor/apparmor/-/merge_requests/795), Fixes: [AABUG:193](https://gitlab.com/apparmor/apparmor/-/issues/193))
- aa-remove-unknown
  - abort on parser failure ([MR:859](https://gitlab.com/apparmor/apparmor/-/merge_requests/859))


## apparmor.vim
- add support for abi rules ([MR:690](https://gitlab.com/apparmor/apparmor/-/merge_requests/690))


## Policy

#### Abstractions
- avahi
  - Add missing /proc permissions ([MR:811](https://gitlab.com/apparmor/apparmor/-/merge_requests/811), [AABUG:203](https://gitlab.com/apparmor/apparmor/-/issues/203))
- base
  - Allow access to possible cpus for glibc-2.36 ([AABUG:267](https://gitlab.com/apparmor/apparmor/-/issues/267), [LP:1989073](https://bugs.launchpad.net/bugs/1989073))
- mesa
  - Update permissions ([MR:879](https://gitlab.com/apparmor/apparmor/-/merge_requests/879))
- openssl:
  - allow /etc/ssl/{engdef,engines}.d/ ([MR:818](https://gitlab.com/apparmor/apparmor/-/merge_requests/818))
- php
  - support PHP 8 ([MR:755](https://gitlab.com/apparmor/apparmor/-/merge_requests/755), [BOO:1186267](https://bugzilla.opensuse.org/show_bug.cgi?id=1186267))
- python
  - update for python 3.10 ([MR:783](https://gitlab.com/apparmor/apparmor/-/merge_requests/783), [AABUG:187](https://gitlab.com/apparmor/apparmor/-/issues/187))
- private-files-strict
  - add new deny path for kwallet (used in KDE 5) ([MR:704](https://gitlab.com/apparmor/apparmor/-/merge_requests/704))
- snap_browsers
  - new abstraction ([MR:863](https://gitlab.com/apparmor/apparmor/-/merge_requests/863))
  - update permissions ([MR:877](https://gitlab.com/apparmor/apparmor/-/merge_requests/877))
- ubuntu-helpers
  - Fix: Opening links with Chrome ([MR:830](https://gitlab.com/apparmor/apparmor/-/merge_requests/830))
- ubuntu-browsers.d/user-files
  - add new deny path for kwallet (used in KDE 5) ([MR:704](https://gitlab.com/apparmor/apparmor/-/merge_requests/704))
- video
  - fix sys rule for video4linux ([MR:791](https://gitlab.com/apparmor/apparmor/-/merge_requests/791))
- wutmp
  - Add missing rule in wutmp abstraction ([MR:724](https://gitlab.com/apparmor/apparmor/-/merge_requests/724), [AABUG:152](https://gitlab.com/apparmor/apparmor/-/issues/152))


#### Profiles
- dhclient: allow setting task comm name ([LP:1918410](https://bugs.launchpad.net/bugs/1918410))
- dhcpd
  - add rule for port_range ([MR:726](https://gitlab.com/apparmor/apparmor/-/merge_requests/726)), [LP:1901373](https://bugs.launchpad.net/bugs/1901373))
- dnsmasq
  - Add missing r permissions for libvirt_leaseshelper ([MR:905](https://gitlab.com/apparmor/apparmor/-/merge_requests/905), [BOO:1202161](https://bugzilla.opensuse.org/show_bug.cgi?id=1202161))
- dovecot
  - Allow use of all signals ([MR:865](https://gitlab.com/apparmor/apparmor/-/merge_requests/865))
  - allow Prometheus metrics end-point in dovecot/stats ([MR:776](https://gitlab.com/apparmor/apparmor/-/merge_requests/776))
- firefox
  - Add support for widevine DRM ([MR:684](https://gitlab.com/apparmor/apparmor/-/merge_requests/684))
- nscd
  - fix conflict with systemd-homed ([MR:707](https://gitlab.com/apparmor/apparmor/-/merge_requests/707), [AABUG:145](https://gitlab.com/apparmor/apparmor/-/issues/145))
- python
  - update for python 3.10 ([MR:783](https://gitlab.com/apparmor/apparmor/-/merge_requests/783), [AABUG:187](https://gitlab.com/apparmor/apparmor/-/issues/187))
- samba
  - allow reading openssl.cnf ([MR:862](https://gitlab.com/apparmor/apparmor/-/merge_requests/862), [BOO:1195463](https://bugzilla.opensuse.org/show_bug.cgi?id=1195463)#c10)
- syslog-ng
  - allow reading *.journal in flatter directory structure ([MR:932](https://gitlab.com/apparmor/apparmor/-/merge_requests/932))


## Tests

- fix i18n.sh regression test on arm64 ([MR:765](https://gitlab.com/apparmor/apparmor/-/merge_requests/765), [LP:1932331](https://bugs.launchpad.net/bugs/1932331))


## Documentation

- fix typos, punctuation, ..([MR:789](https://gitlab.com/apparmor/apparmor/-/merge_requests/789), [AABUG:192](https://gitlab.com/apparmor/apparmor/-/issues/192))
