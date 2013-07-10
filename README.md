#Readme
In order to have smooth nfs4-root, it is desirable to avoid mapping of UIDs and GIDs on both sides, client and server, completely.
Patch with "nfs4_disable_idmapping" parameter for nfs module found it's way to kernel long time ago, and RHEL 6.x kernel has it.
Patch with "nfs4_disable_idmapping" parameter for nfsd module has appeared in 

I backported it from 3.11 kernel and exported nsfd soruce tree from 2.6.32-358.11.1.el6 with this patch for dkms.

#Installation

On target host perform next commands (assuming that you already have installed dkms)

```bash
 git clone https://github.com/antst/knfsd-idmapfix.git /usr/src/knfsd-idmapfix-358.11.1
 dkms add -m knfsd-idmapfix -v 358.11.1
 dkms build -m knfsd-idmapfix -v 358.11.1
 dkms install -m knfsd-idmapfix -v 358.11.1
 ```
