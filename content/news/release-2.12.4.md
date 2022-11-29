---
title: AppArmor 2.12.4 released
date: 2022-11-20
---
AppArmor 2.12.4 was released 2022-11-20.

# Note: AppArmor 2.12 is end of life.

Introduction
============

AppArmor 2.12.4 is the final maintenance release of the 2.12 release of user space components
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
- https://gitlab.com/apparmor/apparmor/-/releases/v2.12.4

### Launchpad Tarball
-   <https://launchpad.net/apparmor/2.12/2.12.4/+download/apparmor-2.12.4.tar.gz>
-   sha256sum: 750d94c6ba3ae94a8d6dd2310399218918fe83b0ccd3bef482a23f581b595c27
-   signature:  <https://launchpad.net/apparmor/2.12/2.12.4/+download/apparmor-2.12.4.tar.gz.asc>

# Changes in This Release


These release notes cover all changes between 2.12.3 (f2fb53c6c3752c5a816035b0561bb16e82f09dd9) and 2.12.4 (ad900176198150c6e09214c593f9b3b45ad59047) on the [apparmor-2.12 branch](https://gitlab.com/apparmor/apparmor/tree/apparmor-2.12).


## Init
- fix fails to load profiles in busybox ([AABUG:80](https://gitlab.com/apparmor/apparmor/-/issues/80))


## library
- Grep away deprecation warning for distutils ([MR:908](https://gitlab.com/apparmor/apparmor/-/merge_requests/908))
- add missing include for `socklen_t`
- add _aa_asprintf to private symbols ([MR:643](https://gitlab.com/apparmor/apparmor/-/merge_requests/643))
- fix a Python 3.8 autoconf check ([MR:519](https://gitlab.com/apparmor/apparmor/-/merge_requests/519), [debug943657](https://bugs.debian.org/943657))


## Policy Compiler (a.k.a apparmor\_parser)
- fix cache time stamp check to include dir time stamps ([MR:760](https://gitlab.com/apparmor/apparmor/-/merge_requests/760))
- fix filter slashes for link targets ([MR:723](https://gitlab.com/apparmor/apparmor/-/merge_requests/723), [AABUG:153](https://gitlab.com/apparmor/apparmor/-/issues/153))
- fix backport of MR700 (fixing rule downgrade for unix rules) ([MR:700](https://gitlab.com/apparmor/apparmor/-/merge_requests/700), [BOO:1180766](https://bugzilla.opensuse.org/show_bug.cgi?id=1180766))
- fix --jobs so job scaling is applied correctly ([MR:703](https://gitlab.com/apparmor/apparmor/-/merge_requests/703))
- call filter slashes for mount dbus conditionals ([MR:607](https://gitlab.com/apparmor/apparmor/-/merge_requests/607), [MR:607](https://gitlab.com/apparmor/apparmor/-/merge_requests/607))
- enable variable expansion for mount type= and options= ([MR:638](https://gitlab.com/apparmor/apparmor/-/merge_requests/638), [AABUG:99](https://gitlab.com/apparmor/apparmor/-/issues/99))
- Fix expansion of variables in unix rules addr= conditional ([MR:607](https://gitlab.com/apparmor/apparmor/-/merge_requests/607), [LP:1856738](https://bugs.launchpad.net/bugs/1856738))
- Fix automatic adding of rule for change_hat interface ([MR:625](https://gitlab.com/apparmor/apparmor/-/merge_requests/625))


## utils
- Fix case sensative hotkey conflict ([MR:679](https://gitlab.com/apparmor/apparmor/-/merge_requests/679))
- Support setuptools >= 61.2 in Python tests ([MR:910](https://gitlab.com/apparmor/apparmor/-/merge_requests/910), [HUBMR:3258](https://github.com/pypa/setuptools/pull/3258))
- fix failing testcase ([MR:391](https://gitlab.com/apparmor/apparmor/-/merge_requests/391), [MR:401](https://gitlab.com/apparmor/apparmor/-/merge_requests/401))
- Add 'mctp' network domain keyword ([MR:911](https://gitlab.com/apparmor/apparmor/-/merge_requests/911))
- Add new python versions to logprof.conf ([MR:795](https://gitlab.com/apparmor/apparmor/-/merge_requests/795), [AABUG:193](https://gitlab.com/apparmor/apparmor/-/issues/193))
- Add CAP_CHECKPOINT_RESTORE to severity.db ([MR:656](https://gitlab.com/apparmor/apparmor/-/merge_requests/656))
- make check_severity_db: say ERROR for failing the build ([MR:591](https://gitlab.com/apparmor/apparmor/-/merge_requests/591))
- Add CAP_BPF and CAP_PERFMON to severity.db ([LP:1890547](https://bugs.launchpad.net/bugs/1890547))
- Handle `symlink` log events in aa-logprof ([AABUG:107](https://gitlab.com/apparmor/apparmor/-/issues/107))
- Fix strip_quotes() to handle empty strings
- add libaparmor swig library path ([MR:586](https://gitlab.com/apparmor/apparmor/-/merge_requests/586), [AABUG:98](https://gitlab.com/apparmor/apparmor/-/issues/98))
- avoid accidently initializing profiles ([MR:539](https://gitlab.com/apparmor/apparmor/-/merge_requests/539))
- don't fail silently when reading a profile (https://gitlab.com/apparmor/apparmor/-/merge_requests/530)
- Use list as parameter for subprocess.call (MR:520](https://gitlab.com/apparmor/apparmor/-/merge_requests/520))
- Fix showing the local inactive profile in json ([MR:516](https://gitlab.com/apparmor/apparmor/-/merge_requests/516))
- Drop 'localinclude' support which is unused and causing crashes ([MR:427](https://gitlab.com/apparmor/apparmor/-/merge_requests/427))
- Fix crash on unbalanced parenthesis in filename ([MR:402](https://gitlab.com/apparmor/apparmor/-/merge_requests/402))
- aa-autodep
  - load abstractions on start ([MR:682](https://gitlab.com/apparmor/apparmor/-/merge_requests/682), [BOO:1178527](https://bugzilla.opensuse.org/show_bug.cgi?id=1178527))
- aa-remove-unknown
  - abort on parser failure ([MR:859](https://gitlab.com/apparmor/apparmor/-/merge_requests/859))
- aa-status
  - handle profile names containing '(' ([MR:415](https://gitlab.com/apparmor/apparmor/-/merge_requests/415), [AABUG:51](https://gitlab.com/apparmor/apparmor/-/issues/51))


## apparmor.vim: 
- add support for abi rules ([MR:690](https://gitlab.com/apparmor/apparmor/-/merge_requests/690))
- allow leading whitespace on alias rules ([MR:527](https://gitlab.com/apparmor/apparmor/-/merge_requests/527))
- support 'include if exists' ([MR:500](https://gitlab.com/apparmor/apparmor/-/merge_requests/500))


## Policy

#### tunables
- global
  - fix breakage due to gnome abstraction changes ([MR:446](https://gitlab.com/apparmor/apparmor/-/merge_requests/446))
- run
  - add new variable to support /run and /var/run/ ([MR:466](https://gitlab.com/apparmor/apparmor/-/merge_requests/466), [AABUG:88](https://gitlab.com/apparmor/apparmor/-/issues/88))
  - add trailing slash to the run variable definition ([MR:533](https://gitlab.com/apparmor/apparmor/-/merge_requests/533))
- share
  - fix breakage due to gnome abstraction changes ([MR:446](https://gitlab.com/apparmor/apparmor/-/merge_requests/446))


#### abstractions
- authentication
  - allow /usr/etc ([MR:426](https://gitlab.com/apparmor/apparmor/-/merge_requests/426))
- base
  - Allow access to possible cpus for glibc-2.36 ([LP:1989073](https://bugs.launchpad.net/bugs/1989073))
  - allow read access to /run/uuidd/request ([MR:445](https://gitlab.com/apparmor/apparmor/-/merge_requests/445))
  - allow read access to top-level ecryptfs directories ([MR:443](https://gitlab.com/apparmor/apparmor/-/merge_requests/443))
- fonts
  - update-debian-fonts ([MR:575](https://gitlab.com/apparmor/apparmor/-/merge_requests/575), [AABUG:94](https://gitlab.com/apparmor/apparmor/-/issues/94))
  - don't allow write of fontconfig cache files ([MR:420](https://gitlab.com/apparmor/apparmor/-/merge_requests/420))
- gnome
  - allow /usr/share/gtk-3.0/settings.ini ([MR:592](https://gitlab.com/apparmor/apparmor/-/merge_requests/592))
  - Allow access of /run/mount/utab
  - allow /etc/xdg/mimeapps.list ([MR:444](https://gitlab.com/apparmor/apparmor/-/merge_requests/444))
  - allow reading per-user themes from $XDG_DATA_HOME ([MR:442](https://gitlab.com/apparmor/apparmor/-/merge_requests/442), [debug930031](https://bugs.debian.org/930031))
- kerberosclient
  - allow reading /etc/krb5.conf.d/ ([MR:425](https://gitlab.com/apparmor/apparmor/-/merge_requests/425))
- nameservice
  - allow accessing /run/systemd/userdb/ ([AABUG:82](https://gitlab.com/apparmor/apparmor/-/issues/82))
- openssl
  - allow /etc/ssl/{engdef,engines}.d/ ([MR:818](https://gitlab.com/apparmor/apparmor/-/merge_requests/818))
- php
  - support PHP 8 ([MR:755](https://gitlab.com/apparmor/apparmor/-/merge_requests/755), [BOO:1186267](https://bugzilla.opensuse.org/show_bug.cgi?id=1186267))
- python
  - Update to support python 3.10 ([MR:783](https://gitlab.com/apparmor/apparmor/-/merge_requests/783), [AABUG:187](https://gitlab.com/apparmor/apparmor/-/issues/187))
- snap_browsers
  - update permissions ([MR:863](https://gitlab.com/apparmor/apparmor/-/merge_requests/863), [MR:877](https://gitlab.com/apparmor/apparmor/-/merge_requests/877))
- ssl
  - Add support for Certbot on openSUSE Leap ([MR:398](https://gitlab.com/apparmor/apparmor/-/merge_requests/398))
- video
  - fix sys rule for video4linux ([MR:791](https://gitlab.com/apparmor/apparmor/-/merge_requests/791))
- wutmp
  - Add missing rule in wutmp abstraction ([MR:724](https://gitlab.com/apparmor/apparmor/-/merge_requests/724), [AABUG:152](https://gitlab.com/apparmor/apparmor/-/issues/152))
- X
  - Allow (only) reading X compose cache ([MR:685](https://gitlab.com/apparmor/apparmor/-/merge_requests/685))
  - add another xauth path ([BOO:1174290](https://bugzilla.opensuse.org/show_bug.cgi?id=1174290), [BOS:1174293](https://bugzilla.suse.com/show_bug.cgi?id=1174293), [HUB:763](https://github.com/jonls/redshift/issues/763), [HUBMR:1230](https://github.com/sddm/sddm/pull/1230))


#### profiles
- avahi
  - Add missing /proc permissions to avahi-daemon profile ([MR:811](https://gitlab.com/apparmor/apparmor/-/merge_requests/811), [AABUG:203](https://gitlab.com/apparmor/apparmor/-/issues/203))
- dhclient
  - allow setting task comm name ([LP:1918410](https://bugs.launchpad.net/bugs/1918410))
- dhcpd
  - add rule for port_range ([MR:726](https://gitlab.com/apparmor/apparmor/-/merge_requests/726), [LP:1901373](https://bugs.launchpad.net/bugs/1901373))
- dnsmasq
  - Add missing r permissions for libvirt_leaseshelper ([MR:905](https://gitlab.com/apparmor/apparmor/-/merge_requests/905), [BOO:1202161](https://bugzilla.opensuse.org/show_bug.cgi?id=1202161))
  - add support for libvirt lease-helper ([MR:618](https://gitlab.com/apparmor/apparmor/-/merge_requests/618))
  - support dnsmasq 2.81 ([MR:475](https://gitlab.com/apparmor/apparmor/-/merge_requests/475))
- dovecot
  - Allow dovecot to use all signals ([MR:865](https://gitlab.com/apparmor/apparmor/-/merge_requests/865))
  - allow Prometheus metrics end-point ([MR:776](https://gitlab.com/apparmor/apparmor/-/merge_requests/776))
  - allow reading dh.pem ([MR:671](https://gitlab.com/apparmor/apparmor/-/merge_requests/671))
  - allow kill signal ([MR:671](https://gitlab.com/apparmor/apparmor/-/merge_requests/671))
  - fix postfix binary paths ([MR:602](https://gitlab.com/apparmor/apparmor/-/merge_requests/602))
  - allow reading my.cnf in dovecot-dict
  - Allow /proc/*/attr/current in dovecot imap and lmtp
- firefox
  - Add support for widevine DRM ([MR:684](https://gitlab.com/apparmor/apparmor/-/merge_requests/684))
- nscd
  - Fix conflict with systemd-homed ([MR:707](https://gitlab.com/apparmor/apparmor/-/merge_requests/707), [AABUG:145](https://gitlab.com/apparmor/apparmor/-/issues/145))
- postfix
  - allow reading icu *.dat ([MR:615](https://gitlab.com/apparmor/apparmor/-/merge_requests/615))
  - fix postfix binary paths ([MR:602](https://gitlab.com/apparmor/apparmor/-/merge_requests/602))
- samba
  - allow reading openssl.cnf ([MR:862](https://gitlab.com/apparmor/apparmor/-/merge_requests/862), [BOO:1195463](https://bugzilla.opensuse.org/show_bug.cgi?id=1195463))
- winbindd
  -  allow locking krb5 rcache files ([MR:460](https://gitlab.com/apparmor/apparmor/-/merge_requests/460))


## Tests
- Set (instead of compare) exresult ([MR:907](https://gitlab.com/apparmor/apparmor/-/merge_requests/907))
- fix i18n.sh regression test on arm64 ([MR:765](https://gitlab.com/apparmor/apparmor/-/merge_requests/765), [LP:1932331](https://bugs.launchpad.net/bugs/1932331))
- Don't build syscall_sysctl if missing kernel headers ([MR:637](https://gitlab.com/apparmor/apparmor/-/merge_requests/637), [AABUG:119](https://gitlab.com/apparmor/apparmor/-/issues/119), [LP:1897288](https://bugs.launchpad.net/bugs/1897288))
- regression tests/prologue: adjust sed to not use ~ as regex separators ([MR:599](https://gitlab.com/apparmor/apparmor/-/merge_requests/599))
- local target does not depend on parser ([MR:586](https://gitlab.com/apparmor/apparmor/-/merge_requests/586), [AABUG:98](https://gitlab.com/apparmor/apparmor/-/issues/98))
- fix aa-logprof invocation ([MR:586](https://gitlab.com/apparmor/apparmor/-/merge_requests/586), [AABUG:98](https://gitlab.com/apparmor/apparmor/-/issues/98))
- add check for built libapparmor ([MR:586](https://gitlab.com/apparmor/apparmor/-/merge_requests/586), [AABUG:98](https://gitlab.com/apparmor/apparmor/-/issues/98))
- Update 'make check' to select tools based on USE_SYSTEM ([MR:580](https://gitlab.com/apparmor/apparmor/-/merge_requests/580))
- fix setting apparmor.aa.profile_dir ([MR:574](https://gitlab.com/apparmor/apparmor/-/merge_requests/574))


## Documentation
- fix typos and punctuation ([MR:789](https://gitlab.com/apparmor/apparmor/-/merge_requests/789), [AABUG:192](https://gitlab.com/apparmor/apparmor/-/issues/192), [MR:429](https://gitlab.com/apparmor/apparmor/-/merge_requests/429), [MR:421](https://gitlab.com/apparmor/apparmor/-/merge_requests/421))


## Infrastructure
- Enable CI for the 2.12 branch ([MR:435](https://gitlab.com/apparmor/apparmor/-/merge_requests/435))
