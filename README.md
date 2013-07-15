#Readme
kernel nfsd from centos/rhel kernel-2.6.32-358.11.1 with few backported patches/bugfixes, prepared as dkms module

Applied patches:
1) e9541ce8efc22c233a045f091c2b969923709038, adds parameter "nfs4_disable_idmapping" to nfsd, 
which allows to avoid id mapping on server side when AUTH_SYS (must have for NFS4-root)

2) a043226bc140a2c1dde162246d68a67e5043e6b2, allows proper handling of files with exec-only pemission mask.

#Installation

On target host perform next commands (assuming that you already have installed dkms)

```bash
 git clone https://github.com/antst/centos-nfsd.git /usr/src/centos-nfsd-358.11.1
 dkms install -m centos-nfsd -v 358.11.1
 ```
 
 native module will be masked by this one.
 
