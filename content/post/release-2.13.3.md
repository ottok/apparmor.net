---
title: AppArmor 2.13.3 released
date: 2019-06-18
---
AppArmor 2.13.3 is a maintenance release of the user space components
of the AppArmor security project. The kernel portion of the project
is maintained and pushed separately.
This version of the userspace should work with all kernel versions from
2.6.15 and later (some earlier version of the kernel if they have the
apparmor patches applied). And supports features released in the 4.18
kernel and ubuntu 18.04 kernel with the apparmor 3 development patches.
AppArmor 2.13.3 was released 2019-06-18.

Obtaining the Release
These release notes cover all changes between 2.13.2 (af4808b5) and 2.13.3 (2f9d9ea7) apparmor-2.13 branch.
Tarball

https://launchpad.net/apparmor/2.13/2.13.3/+download/apparmor-2.13.3.tar.gz
sha256sum: 267053234c68cdb122c5294d7c276b6e2f5fa7e75c6c2d23e3ce69f95d9a7639
signature: https://launchpad.net/apparmor/2.13/2.13.3/+download/apparmor-2.13.3.tar.gz.asc



Changes in this Release

Translations

sync to most up to date language translations available


Build Infrastructure

add files to .gitignore: swig auto generated files for ruby (MR366)
fix libapparmor swig 4 failure 'aa_log_record' object has no attribute '__getattr__' (BUG33)


libapparmor

fix segfault in overlaydirat_for_each() causing overlaid cache directory failures
fix segfault when loading policy cache files (MR348)
fix failure to merge overlay directories in some situations (MR348)


Policy Compiler (a.k.a apparmor_parser)

clean up error handling (dbug921866, LP1815294)
fix parsing of target profile NAME in directed transitions “px -> NAME" (MR334)
improve runtime attachment by determine xmatch priority based on smallest DFA match (MR326)
don't skip cache loads just because optimizations flags are specified
(MR385, LP1820068)


Init

apparmor.systemd: fix minor issues detected by shellcheck (MR293)
ensure error value is returned correctly (MR352)


Utils

genprof/logprof

drop failing corner-case check in logparser.py (boo1120472, MR297)
drop unused get_profile_filename() from logparser.py (MR297)
fix error KeyError: 'logfiles' when no logprof.conf exists (MR365)
don't drop later events when user selects to deny a hat (MR378)


update network keyword list and add corresponding tests (MR350)


Policy


Profiles

dnsmasq:

allow peer=libvirtd to support named profile (MR304)
work around breakage caused by {bin,sbin} alternation (boo1127073, MR346)
revert /usr/{bin,sbin}/ alternation in dnsmasq profile name (boo1127073, MR346)


dovecot

allow FD passing between dovecot and dovecot's anvil (MR336)
allow chroot'ing the auth processes (MR336)
let dovecot/anvil rw the auth-penalty socket (MR336)
auth processes need to read from postfix auth socket (MR336)
add abstractions/ssl_certs to lmtp (MR336)
allow master to use SIGTERM on children that are slow to die (MR357)
align {pop3,managesieve}-login to imap-login (MR389)


identd: allow network netlink dgram (MR353)
lsb_release profile: new abstraction (MR154)
mysqld (MR310):

add mmap permission for mysqld (4.8 semantic change)
allow mysql to determine which cpus are online
allow locking of mysql files


syslog-ng: add abstractions/python for python-parser (MR361)



Tunables

share:

make it play well with aliases (MR300)
fix buggy syntax that broke the ~/.local/share part of the @{user_share_dirs} tunable (LP1816470, MR344)





Abstractions

audio:

fix alsa settings access
grant read access to the system-wide asound.conf (dbug920669, MR320)
grant read access to the libao configuration files (dbug920670, MR320)


base: allow mr permission on all .so common library paths (MR345)
dri-common: allow reading /dev/dri/ (AABUG29, MR382)
fonts:

allow to read conf-avail dir itself (MR165)
allow creating/writing config dirs (MR165)
add various openSUSE-specific font config directories (MR309)


gnome:

allow reading gtk-3.0 cache files ([MR342][MR342])
allow creating config dirs (MR165)


kde:

allow access to common KDE-specific settings (MR327)
allow access to global KDE settings (MR327)


ldapclient: allow rw access to the nslcd socket (LP1575438)
mesa:

allow reading drirc.d (MR308)
move dirc.d access to dir-common (MR314)


nameservice: allow access to /run/netconfig/resolv.conf (boo1097370)
nvidia: allow reading nvidia application profiles (MR125)
postfix-common: make compatible with updated postfix profiles naming (MR387)
python: allow reading /usr/local/lib/python3 (MR171)
qt5: allow reading user configuration (MR335)
qt5-compose-cache-write: fix anonymous shared memory access (MR301)
qt5-settings-write: fix anonymous shared memory access (MR302)
ssl_certs,keys - add support for libdehydrated in /var/lib/ (MR299)
ubuntu-browsers.d/multimedia: allow creating/writing config dirs (MR165)
vulcan: allow reading /etc/vulkan/icd.d/ (MR329)




Tests

fix mount test to use next available loop device (MR379)
update tests to support distros with user-merge where /bin and /sbin are symlinks (MR331)
fix regression test failures around new binary cache layout (MR348)
update tests for new network domain keywords (MR349)
update tests for base abstraction changes (MR358)


Documentation

apparmor.d (7):

update list of network domain keywords (MR349)
drop unsupported 'to' option for link rules from manpage (MR368)




Note
There is a semantic change in the 4.8 kernel (commit
9f834ec18defc369d73ccf9e87a2790bfa05bf46) that affects apparmor policy
enforcement. Specifically it affects when the m permission bit is
checked for elf binary executables. Policy and tests within apparmor
2.12 and later have been updated to support running on pre 4.8 and 4.8+ kernels.
