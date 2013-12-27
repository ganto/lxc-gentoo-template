lxc-gentoo-template
===================

gentoo lxc template that works with lxc-create (lxc >1.0.0beta1)

Usage
=====

```
ln -nsf ${PWD}/lxc-gentoo /usr/share/lxc/templates/lxc-gentoo
lxc-create -n mygentoo -t gentoo -- --autologin
lxc-start -n mygentoo
```

Options
=======

./lxc-gentoo -h|--help [-a|--arch <arch>] [-v|--variant <variant>] [-P|--private-portage] [--portage-dir <protagedir>] [-t|--tarball <stage3file>]
 [-F|--flush-cache] [-c|--cache-only] [-u|--user <username>] [-w|--password <password>] [-S|--auth-key <keyfile>]
 [-s|--more-secure] [-m|--mirror <gentoomirror>] [--tty <number>] [--nettun]

arch: the container architecture (e.g. amd64): defaults to host arch (currently: 'amd64')
        If you choose one that needs emulation, see 
        tested: amd64, x86, arm
        You could try any other gentoo arch, why not

variant: gentoo's Architecture variant as of dec 2013 : (currently: 'amd64')
        for amd64 arch: amd64 (default), amd64-hardened+nomultilib, amd64-hardened, amd64-nomultilib, x32
        for x86 arch: i686 (default), i486, i686-hardened
        for arm arch: armv7a (default), armv7a_hardfp, armv6j, armv6j_hardfp, armv5tel, armv4tl

private-portage: by default, /usr/portage is mount-binded with host one if exists (currently: '')
                this force container to have his own copy

portage-dir: portage dir used for shared portage
        by default the host on if any (currently: '')

tarball: force usage of local stage3 archive (currently: 'amd64')
        If empty, latest will be downloaded

flush-cache: do like there is no previous cache

cache-only: just ensure cache is present 
        if cache exists and "flush-cache" not specified, does nothing

user: user used in auth oriented options (currently: 'root')

password: password for user (currently: 'toor')
        if default, usage of auth-key will disable password setting
        
autologin: enable autologin for user (currently: '')
        This unset default password setting
        
auth-key: SSH Public key file to inject into container for user (currently: '')
        This unset default password setting

more-secure: does some additional security agressive settings (may prevent things to run) (currently: '')

mirror: gentoo mirror for download (currently: 'http://distfiles.gentoo.org')

tty: number of tty (9 max) (currently: '1')

nettun: enable creation of /dev/net/tun (for private container VPN) (currently: '')

