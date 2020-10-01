AppArmor 3.0 was released 2020-10-01.

# Introduction

AppArmor 3.0 is a major new release of the AppArmor user space that makes an important change to policy development and support. Its focus is transitioning policy to the new features abi and as such other new features have been limited.

Apprmor 3.0 is a bridge release between older AppArmor 2.x policy and the newer AppArmor 3 style policy which requires the declaration of a features abi. As such AppArmor 3.0 will be a short lived release, and will not receive long term support. The following AppArmor 3.1 feature release is planned to be a regular release, please take this into account when including AppArmor 3.0 into a distro release.

This version of the userspace should work with all kernel versions from
2.6.15 and later (some earlier version of the kernel if they have the
apparmor patches applied). And supports features released in the 4.20
kernel.

The kernel portion of the project is maintained and pushed separately.


# Highlighted new features

- Policy now must declare the feature abi it was developed for if it is to use any new features. For further information please see the [wiki](https://gitlab.com/apparmor/apparmor/-/wikis/AppArmorpolicyfeaturesabi).
- The use of profile names that are based on pathnames are deprecated. For further information please see the [wiki](https://gitlab.com/apparmor/apparmor/-/wikis/DeprecateProfilePathName).
- Support for new kernel features (requires appropriate features abi tagging in policy)
  - upstream v8 network socket rules
  - xattr attachment conditionals
  - capabilities PERFMON and BPF
- rewritten aa-status
  - supports use in systems/images where python is not available
  - supports kill, unconfined and mixed profile modes
- rewritten aa-notify
  - move from perl to python 3
  - shared backend with other python tools
  - support use of aa.CONFDIR instead of hard coded /etc/apparmor
  - improved message layout
- improved support for kernels that support LSM stacking
- support profile modes
  - enforce (default when no mode flag is supplied)
  - kill (experimental)
  - unconfined (experimental)
- reference policy updated for 3.0 feature abi
- basic support for [systemd v246 early load of apparmor policy](https://gitlab.com/apparmor/apparmor/-/wikis/AppArmorInSystemd#early-policy-loads).
- new tool [aa-features-abi](https://gitlab.com/apparmor/apparmor/-/wikis/manpage_aa-features-abi.1) for extracting feature abis from the kernel

# Important Notes

- Potentially breaking change: AppArmor will now issue warning about policy that does not specify a feature abi if that policy is not pinned to a specific feature abi. AppArmor will compile such policy using a default feature abi instead of the kernels abi. For more information see the [wiki](AppArmorpolicyfeaturesabi).

- Potentially breaking change: AppArmor no longer loads snapd policy by default. It is expected that snapd users are using the snapd unit file. If this is not the case distros will need to revert ```0164fd05 init: stop loading snap policy``` OR take advantage of systemd v246 early load of apparmor policy.

# Obtaining the Release
These release notes cover all changes between 2.13 (f97782b100733770eebc7cf2839ba43683a74f46) and 3.0 (5d51483bfecf556183558644dc8958135397a7e2) [apparmor-3.0 branch](https://gitlab.com/apparmor/apparmor/tree/apparmor-3.0).

gitlab: https://gitlab.com/apparmor/apparmor/-/releases/v3.0.0

Launchpad Tarball
-   <https://launchpad.net/apparmor/3.0/3.0/+download/apparmor-3.0.0.tar.gz>
-   sha256sum: 66fd751fe51eb427d2aa864ee035b12d01d212fd595579275219b0148c43755e
-   signature: <https://launchpad.net/apparmor/3.0/3.0/+download/apparmor-3.0.0.tar.gz.asc>

For full release notes please see https://gitlab.com/apparmor/apparmor/-/wikis/Release_Notes_3.0
