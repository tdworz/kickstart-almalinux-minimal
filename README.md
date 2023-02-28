Kickstart for an AlmaLinux Minimal System
=========================================

These resources use [Kickstart](https://en.wikipedia.org/wiki/Kickstart_(Linux))
and [iPXE](https://ipxe.org/) to perform automated
[AlmaLinux](https://almalinux.org/) installations.


⚠️ WARNING
----------

**THE KICKSTART FILES IN THIS REPOSITORY INCLUDE TOM DWORZANSKI'S PERSONAL
PUBLIC SSH KEY. USING A KICKSTART FILE IN THIS REPOSITORY WITHOUT FIRST
REPLACING ТOM DWORZANSKI'S PERSONAL PUBLIC SSH KEY WILL RESULT IN TOM DWORZANSKI
HAVING FULL ACCESS TO YOUR SYSTEM.**


Shortened URLs
--------------

These shortened URLs may be used to access plain-text versions of the Kickstart
and iPXE files in this repository.

| Shortcut | Destination |
|----------|-------------|
| https://tinyurl.com/ks-almalinux9 | [9/anaconda-ks.cfg](https://raw.githubusercontent.com/tdworz/kickstart-almalinux-minimal/master/9/anaconda-ks.cfg) |
| https://tinyurl.com/ipxe-almalinux9 | [9/kickstart.ipxe](https://raw.githubusercontent.com/tdworz/kickstart-almalinux-minimal/master/9/kickstart.ipxe) |


Usage
-----

The following sections provide details of how to launch Kickstart.

### Installation from iPXE

The iPXE files in this repository reference respective Kickstart files.
Launching Kickstart using iPXE requires providing the network location of the
desired iPXE configuration file to whatever management system exists at your
provider. For example, you might provide the URL,
https://tinyurl.com/ipxe-almalinux9.

### Installation from Media

Kickstart may be launched manually on a system booted from installation media.

Launching Kickstart manually is documented in [section 7.1 of Performing an
advanced RHEL 9 installation](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/9/html-single/performing_an_advanced_rhel_9_installation/index#starting-a-kickstart-installation-manually_starting-kickstart-installations).

Generally speaking, you will follow these steps:

1. Make sure the desired Kickstart file is available at a network location.

   For production, that may mean using one of the web-accessible Kickstart files
   from this repository. For example, you might use
   https://tinyurl.com/ks-almalinux9.

   For development, that may mean setting up a local web server to make a
   Kickstart file available on the local network. As an example, you might use
   Python to launch a simple web server in the root of this project:
   `python -m http.server 8000`.

2. Using desired installation media, boot a system that has network access to
   the Kickstart file described in _Step 1_.

   For production, that may mean booting a virtual private server from an
   uploaded ISO image.

   For development, that may mean booting Virtualbox from desired installation
   media after configuring the network to use a bridged adapter.

3. Once the installation options boot menu is shown, pick an installation
   option and then press \[Tab\] to edit the configuration options of the
   menu item.

4. Append `inst.ks=<kickstart_file_location>` to the configuration options.

   For production, that may mean appending:
   `inst.ks=https://tinyurl.com/ks-almalinux9`

   For development, that may mean appending the network address of the Kickstart
   file mentioned in _Step 1_ above:
   `inst.ks=http://192.168.0.1:8000/9/anaconda-ks.cfg`.

5. Press \[Enter\] to initiate the fully-automated installation.


Additional Resources
--------------------

The following resources may be useful for understanding and configuring
Kickstart.

* [Performing an advanced RHEL 9
installation](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/9/html-single/performing_an_advanced_rhel_9_installation/index)
* [Pykickstart documentation](https://pykickstart.readthedocs.io/)
* [Kickstart on Wikipedia](https://en.wikipedia.org/wiki/Kickstart_(Linux))

The following resources may be useful for understanding and configuring
iPXE.

* [iPXE website](https://ipxe.org/)


Copyright & License
-------------------

Copyright © 2022-2023 Tom Dworzanski (tdworz).

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the “Software”), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
