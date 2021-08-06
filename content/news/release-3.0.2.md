---
title: AppArmor 3.0.2 released
date: 2021-08-05
---

AppArmor 3.0.2 is a maintenance release of the user space components
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
- https://gitlab.com/apparmor/apparmor/-/releases/v3.0.2

### Launchpad

  -   <https://launchpad.net/apparmor/3.0/3.0.2/+download/apparmor-3.0.2.tar.gz>
  -   sha256sum: a3512681d7cef05b82f79f75359b77179d45d72ba343383eee20070dc57f683e
  -   signature: <https://launchpad.net/apparmor/3.0/3.0.2/+download/apparmor-3.0.2.tar.gz.asc>

# Changes in this Release

These release notes cover all changes between 3.0.1 (b0f08aa9d678197b8e3477c2fbff790f50a1de5e) and 3.0.2 (59ec31bcb3c3ce186de5c6d97c8928ac8878a8af) [apparmor-3.0 branch](https://gitlab.com/apparmor/apparmor/tree/apparmor-3.0).

## Build Infrastructure
- .gitignore: Add aa-features-abi and utils coverage files ([MR:748](https://gitlab.com/apparmor/apparmor/-/merge_requests/748))

## apparmor.vim:
- add support for abi rules ([MR:690](https://gitlab.com/apparmor/apparmor/-/merge_requests/690))

## Library
- Adjust stacking interface check ([MR:713](https://gitlab.com/apparmor/apparmor/-/merge_requests/713),
[AABUG:150](https://gitlab.com/apparmor/apparmor/-/issues/150))
- look up python-config using AC_PATH_TOOL to support cross building ([MR:729](https://gitlab.com/apparmor/apparmor/-/merge_requests/729))
- Do not abuse AC_CHECK_FILE ([MR:728](https://gitlab.com/apparmor/apparmor/-/merge_requests/728),[debug984582](https://bugs.debian.org/984582))
- alphasort directory traversals ([MR:706](https://gitlab.com/apparmor/apparmor/-/merge_requests/706),
    [AABUG:147](https://gitlab.com/apparmor/apparmor/-/issues/147))
- fix setting proc_attr_base ([MR:701](https://gitlab.com/apparmor/apparmor/-/merge_requests/701))
- Honor global LDFLAGS when building python library ([MR:689](https://gitlab.com/apparmor/apparmor/-/merge_requests/689),
    [AABUG:138](https://gitlab.com/apparmor/apparmor/-/issues/138))



## Policy Compiler (a.k.a apparmor\_parser)
- update the parser to add interface rules for change_XXX ([MR:713](https://gitlab.com/apparmor/apparmor/-/merge_requests/713),
[AABUG:150](https://gitlab.com/apparmor/apparmor/-/issues/150))
- Detect and handle include loop when parsing profiles ([MR:743](https://gitlab.com/apparmor/apparmor/-/merge_requests/743),
    [MR:750](https://gitlab.com/apparmor/apparmor/-/merge_requests/750),
    [MR:743](https://gitlab.com/apparmor/apparmor/-/merge_requests/743),
    [BOO:1184779](https://bugzilla.opensuse.org/show_bug.cgi?id=1184779))
- fix cache time stamp check to include dir time stamps ([MR:760](https://gitlab.com/apparmor/apparmor/-/merge_requests/760))
- Fix comment wording in file_cache.h ([MR:752](https://gitlab.com/apparmor/apparmor/-/merge_requests/752))
- Fix invalid reference to name in attachment warning ([MR:727](https://gitlab.com/apparmor/apparmor/-/merge_requests/727))
- fix filter slashes for profile attachments ([MR:727](https://gitlab.com/apparmor/apparmor/-/merge_requests/727),
    [AABUG:154](https://gitlab.com/apparmor/apparmor/-/issues/154))
- fix filter slashes for link targets ([MR:723](https://gitlab.com/apparmor/apparmor/-/merge_requests/723),
    [AABUG:153](https://gitlab.com/apparmor/apparmor/-/issues/153))
- fix rule downgrade for unix rules ([MR:700](https://gitlab.com/apparmor/apparmor/-/merge_requests/700),
    [BOO:1180766](https://bugzilla.opensuse.org/show_bug.cgi?id=1180766))
- fix build issue with REALLOCARRAY check ([MR:712](https://gitlab.com/apparmor/apparmor/-/merge_requests/712))
- fix --jobs so job scaling is applied correctly ([MR:703](https://gitlab.com/apparmor/apparmor/-/merge_requests/703))
- don't abort profile compile if the kernel is missing caps/mask ([MR:691](https://gitlab.com/apparmor/apparmor/-/merge_requests/691),
    [AABUG:140](https://gitlab.com/apparmor/apparmor/-/issues/140))


## Utils
- Detect and handle include loop when parsing profiles ([MR:746](https://gitlab.com/apparmor/apparmor/-/merge_requests/746),
    [BOO:1184779](https://bugzilla.opensuse.org/show_bug.cgi?id=1184779))


## Policy

#### abstractions
- authentication
  - Allow reading /etc/login.defs.d/ ([MR:774](https://gitlab.com/apparmor/apparmor/-/merge_requests/774),
    [BOO:1188296](https://bugzilla.opensuse.org/show_bug.cgi?id=1188296))
- crypto
  - Add crypto abstraction to 3.0 Branch
    ([MR:773](https://gitlab.com/apparmor/apparmor/-/merge_requests/773))
- php
  - support PHP 8 ([MR:755](https://gitlab.com/apparmor/apparmor/-/merge_requests/755),
    [BOO:1186267](https://bugzilla.opensuse.org/show_bug.cgi?id=1186267))
- ssl_certs
  - allow reading crypto policies ([MR:720](https://gitlab.com/apparmor/apparmor/-/merge_requests/720))
  - add /etc/ca-certificates/ and /etc/libressl/ ([MR:698](https://gitlab.com/apparmor/apparmor/-/merge_requests/698))
- private-files-strict
  - add new deny path for kwallet (used in KDE 5) ([MR:704](https://gitlab.com/apparmor/apparmor/-/merge_requests/704))
- ubuntu-browsers.d/user-files
  - add new deny path for kwallet (used in KDE 5) ([MR:704](https://gitlab.com/apparmor/apparmor/-/merge_requests/704))

- wutmp
  - Add missing rule in rule ([MR:724](https://gitlab.com/apparmor/apparmor/-/merge_requests/724),
    [AABUG:152](https://gitlab.com/apparmor/apparmor/-/issues/152))


#### profiles
- dovecot
  - - allow Prometheus metrics end-point in dovecot/stats ([MR:776](https://gitlab.com/apparmor/apparmor/-/merge_requests/776))
- dhclient
  - allow setting task comm name ([LP:1918410](https://bugs.launchpad.net/bugs/1918410))
- dhcpd
  - add rule for port_range ([MR:726](https://gitlab.com/apparmor/apparmor/-/merge_requests/726),
    [LP:1901373](https://bugs.launchpad.net/bugs/1901373))
- firefox
  - Add support for widevine DRM ([MR:684](https://gitlab.com/apparmor/apparmor/-/merge_requests/684))
- nscd
  - Fix conflict with systemd-homed ([MR:707](https://gitlab.com/apparmor/apparmor/-/merge_requests/707),
    [AABUG:145](https://gitlab.com/apparmor/apparmor/-/issues/145))
- ntpd
  - add abstractions/ssl_certs ([MR:698](https://gitlab.com/apparmor/apparmor/-/merge_requests/698))
- postfix
  - Update postfix profiles to support latest release ([MR:753](https://gitlab.com/apparmor/apparmor/-/merge_requests/753))
  - postfix-flush and -showq: add permissions needed with latest postfix ([MR:717](https://gitlab.com/apparmor/apparmor/-/merge_requests/717))
  - allow access to *.lmdb files ([MR:717](https://gitlab.com/apparmor/apparmor/-/merge_requests/717))
  - cleanup postfix profiles ([MR:717](https://gitlab.com/apparmor/apparmor/-/merge_requests/717))


## Tests
- python tools
  - add re_match_include_parse() test with invalid rule name ([MR:695](https://gitlab.com/apparmor/apparmor/-/merge_requests/695))
  - Add missing test for ProfileList add_alias() ([MR:694](https://gitlab.com/apparmor/apparmor/-/merge_requests/694))
  - Fix comment in split_name() tests ([MR:692](https://gitlab.com/apparmor/apparmor/-/merge_requests/692))

- regression
  - Fix aa_policy_cache to use correct config file ([MR:653](https://gitlab.com/apparmor/apparmor/-/merge_requests/653))
  - Fix regression tests when using in tree parser ([MR:653](https://gitlab.com/apparmor/apparmor/-/merge_requests/653))
  - fix i18n.sh regression test on arm64 ([MR:765](https://gitlab.com/apparmor/apparmor/-/merge_requests/765),
    [LP:1932331](https://bugs.launchpad.net/bugs/1932331))

# Note

There is a semantic change in the 4.8 kernel (commit
9f834ec18defc369d73ccf9e87a2790bfa05bf46) that affects apparmor policy
enforcement. Specifically it affects when the m permission bit is
checked for elf binary executables. Policy and tests within apparmor
2.12 and later have been updated to support running on pre 4.8 and 4.8+ kernels.

