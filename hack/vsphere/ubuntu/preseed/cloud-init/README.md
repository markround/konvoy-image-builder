# Base image building

These files provide the cloud-init files required to auto-provision a basic Ubuntu 20.04 base image on vSphere without any customizations.

Serve these files over HTTP, e.g. by running the following from this directory: 

```
python3 -m http.server
```

Provision your VM as normal (with at least 4GB of memory), and at the first boot screen on the ISO:

* Press ESC until you get to the main boot menu.
* press F6 to get to the "Other Options" menu.
* Press ESC again to dismiss the pop-up menu and focus on the Boot Options command line
* Add the following text: `autoinstall ds=nocloud-net;s=http://<IP address of host serving cloud-init files>:8000/` (adjusting the IP address, port and path if necessary)
* Press ENTER to start the boot/install process.

The system will then install and reboot. You can then shut the VM down and convert it to a template for use with KIB.
