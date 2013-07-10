#Readme
In order to have smooth nfs4-root, it is desirable to avoid mapping of UIDs and GIDs on both sides, client and server, completely.
In RHEL 6.x kernels, on a client side there is "nfs4_disable_idmapping" parameter, which set to TRUE by default.
To complete this story, commit e9541ce8efc22c233a045f091c2b969923709038 added the same parameter for the server side.

I backported e9541ce8efc22c233a045f091c2b969923709038 for RHEL6 kernel and exported nsfd soruce tree from 2.6.32-358.11.1.el6 with this patch as dkms module.

#Installation

On target host perform next commands (assuming that you already have installed dkms)

```bash
 git clone https://github.com/antst/knfsd-idmapfix.git /usr/src/knfsd-idmapfix-358.11.1
 dkms add -m knfsd-idmapfix -v 358.11.1
 dkms build -m knfsd-idmapfix -v 358.11.1
 dkms install -m knfsd-idmapfix -v 358.11.1
 ```
 
 native module will be masked by this one.
 
