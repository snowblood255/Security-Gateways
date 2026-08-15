# This Documentation Created By Kanan_H

## Steps to install pfSense, OPNsense, and VyOS

First, we need to download all of them.

For pfSense, we will use the Internet Archive site. The link is provided below. I downloaded 2.6.0 for stability and ease of use. Click ISO and start the download.

Here is the link: https://archive.org/details/pfSense-CE-2.6.0-RELEASE-amd64

![pfSense installation screen](pictures/pfsense-ie.png)

---

After that, we have to download OPNsense. Go to this site: https://opnsense.org/download/

![pfSense installation screen](pictures/opensensedown.png)

Choose the image type DVD and click download. The download will start automatically. It will download an archive file. After the download, right-click it and extract it so you will find the ISO there.

---

Last, we need to download VyOS. Go to VyOS GitHub: https://github.com/vyos/vyos-nightly-build/releases

Choose the latest version and click it. In our case, it's 2026.08.14-0025-rolling. Click on it.

![pfSense installation screen](pictures/vyos1.png)

Then scroll down to the end and find assets. In assets, there is a filename called `vyos-2026.08.14-0025-rolling-generic-amd64.iso`. Click on it and the download will start automatically.

![pfSense installation screen](pictures/vyos2.png)

Now we have downloaded all the required ISO files. Now let's install them into virtual machines. I will use VMware for this.

---

## First, let's install pfSense

Open your VMware. You will see a home screen like in the picture:

![pfSense installation screen](pictures/wmware1.png)

Click Create New Virtual Machine, then click Custom (Advanced).

![pfSense installation screen](pictures/vmware2.png)

Click next and do not change anything on the next page, then click next again. Select I will install the operating system later and click next.

![pfSense installation screen](pictures/wmare3.png)

In the next window, choose Linux and Debian 12.x 64-bit.

![pfSense installation screen](pictures/wmware4.png)

Give a name to your machine and click next. I named it pfSense.

![pfSense installation screen](pictures/wmware5.png)

Set the CPU settings like in the picture below, then click next:

![pfSense installation screen](pictures/wmware6.png)

Assign 2 GB of RAM on this page and click next:

![pfSense installation screen](pictures/wmawre7.png)

In the current section, select NAT for now and click next.

![pfSense installation screen](pictures/wmware8.png)

In the next page, select Recommended and click next, and choose Recommended again and click next.

In the current section, select Create a New Virtual Disk and click next.

![pfSense installation screen](pictures/wmaware9.png)

Set the size to 20 GB and select Single Virtual Disk.

![pfSense installation screen](pictures/wmare10.png)

Click next on the next page and then click finish. If there is any checkbox that says Power On this VM, uncheck it. We will make adjustments before starting the VM.

Your virtual machine will appear on the left panel. Right-click it, then go to Manage and click Settings. This panel will appear:

![pfSense installation screen](pictures/wmare11.png)

Click add and choose Network Adapter, then click finish:

![pfSense installation screen](pictures/wmware12.png)

Click the newly added network adapter and, in the right pane, select Host-only:

![pfSense installation screen](pictures/wmware13.png)

Now click CD/DVD and select the ISO file that you downloaded. Click OK to close the settings tab and click pfSense, then select Start the VM.

---

## Now let's install and configure pfSense

After launching, wait a little bit and the install page will appear:

![pfSense installation screen](pictures/pfsense1.png)

Choose Install and press OK:

![pfSense installation screen](pictures/pfsense2.png)

Select Continue with default keymap and press Select:

![pfSense installation screen](pictures/pfsense3.png)

Select Auto (ZFS) and press OK:

![pfSense installation screen](pictures/pfsense4.png)

Select Install and press Select:

![pfSense installation screen](pictures/pfsense5.png)

Choose Stripe and press OK:

![pfSense installation screen](pictures/pfsense6.png)

Press the spacebar to select the disk and press OK:

![pfSense installation screen](pictures/pfsense7.png)

Click Yes to erase the disk:

![pfSense installation screen](pictures/pfsense8.png)

Wait for the installation to complete. After the installation is completed, select No and then reboot it:

![pfSense installation screen](pictures/pfsense9.png)

Wait for it to start and you will see the main panel:

![pfSense installation screen](pictures/pfsense10.png)

You will see two IP addresses, one for WAN and one for LAN. We will access the admin panel via an IP address, so we have to configure it in order to reach it from Windows.

Choose 2 from the list and press Enter:

![pfSense installation screen](pictures/pfsense11.png)

Select 2:

![pfSense installation screen](pictures/pfsense12.png)

Enter the desired IP address that is situated in the same subnet. To know your machine's IP, go to Windows and type `ipconfig`.

You will see the VMware Host-only or VMnet1 IP and subnet. In this case, my subnet is 211, so I will set an IP with the same subnet.

![pfSense installation screen](pictures/pfsense13.png)

Set the subnet count to 24 and press Enter:

![pfSense installation screen](pictures/pfsense14.png)

Press Enter for none:

![pfSense installation screen](pictures/pfsense15.png)

We are not setting an IPv6 right now, so leave it as none and press Enter. Type Y and press Enter. Type the IP start range and end range according to the IP you set. Then type N and press Enter because we will use HTTPS.

![pfSense installation screen](pictures/pfsense16.png)

Now you can access the admin panel via the provided IP address on your screen, not the one shown here.

Default credentials are admin, pfsense. After that, you will be prompted to complete the configuration. That's all for now.

![pfSense installation screen](pictures/pfsense17.png)

---

## Now let's install OPNsense

The configuration will be the same as pfSense. Just repeat all the steps for the configuration in VMware.

Let's install OPNsense now:

OPNsense installation is a bit different from pfSense. After you start the machine, this screen will appear:

![pfSense installation screen](pictures/opn1.png)

What you see is live mode without installation, so we need to install it. For this, type installer in the login field and type opnsense in the password field, then press Enter. The install screen will appear.

![pfSense installation screen](pictures/opn2.png)

Select Continue with default keymap and press next:

Select Install (ZFS):

![pfSense installation screen](pictures/opn3.png)

If it asks for more than 2 GB of RAM, click Proceed Anyway:

![pfSense installation screen](pictures/opn4.png)

Select Stripe:

![pfSense installation screen](pictures/opn5.png)

Press the spacebar to choose the disk, then press Enter:

![pfSense installation screen](pictures/opn6.png)

Click Yes to erase the disk and start the installation:

![pfSense installation screen](pictures/opn7.png)

Wait for the installation to complete as with pfSense:

![pfSense installation screen](pictures/opn8.png)

After the installation is complete, keep or change the password if you want, then reboot and wait for it to start. Then log in with root and the OPNsense password:

![pfSense installation screen](pictures/opn9.png)

Now, as in pfSense, we have two interfaces there and we have to configure the LAN one. Type 2, then choose LAN (enter LAN number):

![pfSense installation screen](pictures/opn10.png)

Type Yes if you want a dynamic IP and type N if you want a static IP. I chose a static one:

![pfSense installation screen](pictures/opn11.png)

Enter the desired IP address as in pfSense, but use the same subnet as the Host-only adapter:

![pfSense installation screen](pictures/opn12.png)

Type 24 as in pfSense:

![pfSense installation screen](pictures/opn13.png)

Choose what I chose for the following questions, as provided in the picture:

![pfSense installation screen](pictures/opn14.png)

Choose N for certificates and N for HTTP requests. After that, the setup is complete and you can access the interface via the web. Default credentials are root and opnsense:

![pfSense installation screen](pictures/opn15.png)

---

## Last, let's install VyOS

The configuration will be the same as pfSense. Just repeat all the steps for the configuration in VMware.

Let's install VyOS now:

Launch the machine and you will see a menu. Choose the first one:

![pfSense installation screen](pictures/vyoss1.png)

After starting, you will be prompted to the login screen. The login is vyos and the password is vyos. Use these to log in to the system:

![pfSense installation screen](pictures/vyoss2.png)

After logging in, this will appear:

![pfSense installation screen](pictures/vyos3.png)

Type `ip addr` so we will know our interfaces to configure later:

![pfSense installation screen](pictures/vyos4.png)

Now we have to go into configuration mode to configure the interfaces. Type `configure` in the command line.

After that, write this to configure the eth0 interface via DHCP:

`set interfaces ethernet eth0 address dhcp`

![pfSense installation screen](pictures/vyos5.png)

Now we use the Host-only adapter IP address and subnet to configure the LAN interface. For that, I typed:

`set interfaces ethernet eth1 address 192.168.211.102/24`

because my IP is this.

![pfSense installation screen](pictures/vyos6.png)

Now we have to apply the configuration, so type `commit` and press Enter. This will apply the configuration. Type `save` to save the settings. Now our interfaces are set:

![pfSense installation screen](pictures/vyos7.png)

Now type `exit` to go back to normal mode. Now it's time to test the connection. Go to CMD and write:

`ping 192.168.211.102`

and look for replies.

![pfSense installation screen](pictures/vyos8.png)

Now let's test whether VyOS can reach the internet. In VyOS, type:

`ping 8.8.8.8`

and look for replies:

![pfSense installation screen](pictures/vyos9.png)

Installation completed. That's all for now.
