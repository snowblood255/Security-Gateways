# This Documentation Created By Kanan_H

## Steps to install pfsense, opensense adn VyOs

First, we need to download all of them.

For pfsense, we will use Internet Archive site. Link is provided below. I downloaded 2.6.0 for stability and ease of use. Click ISO and start download.

Here is the link: https://archive.org/details/pfSense-CE-2.6.0-RELEASE-amd64

![pfSense installation screen](pictures/pfsense-ie.png)

---

After that, we have to download Opensense. Go to this site: https://opnsense.org/download/

![pfSense installation screen](pictures/opensensedown.png)

Choose image type DVD and click download. The download will start automatically. It will download an archive file. After download, right-click it and extract it so you will find iso there.

---

Last, we need to download VyOS. Go to VyOS Github : https://github.com/vyos/vyos-nightly-build/releases

Choose the latest version and click it. In our case, it's 2026.08.14-0025-rolling. Click on it.

![pfSense installation screen](pictures/vyos1.png)

Then scroll down to the end and find asstes and in asstes there is a filename called `vyos-2026.08.14-0025-rolling-generic-amd64.iso`. Click on it and the download will start automatically.

![pfSense installation screen](pictures/vyos2.png)

Now we have downloaded all the required iso files. Now let's install them into Virual machine. I will use VmWare for this.

---

## First, let's install PfSense

Open your VmWare. You will see a home screen like in the picture:

![pfSense installation screen](pictures/wmware1.png)

Click Create new virtual machine, then click custom(advanced).

![pfSense installation screen](pictures/vmware2.png)

Click next and do not change anything on the next page, and click next again. Seleck I will install operating system later and click next.

![pfSense installation screen](pictures/wmare3.png)

In the next window, choose linux and Debian 12.x 64 Bit.

![pfSense installation screen](pictures/wmware4.png)

Give a name to your machine and click next. I named it PfSense.

![pfSense installation screen](pictures/wmware5.png)

Set the cpu setting like in the picture below, then click next:

![pfSense installation screen](pictures/wmware6.png)

Assign 2Gb Of ram on this page and click next:

![pfSense installation screen](pictures/wmawre7.png)

In the current section, select NAT for now and click next.

![pfSense installation screen](pictures/wmware8.png)

In the next page, select Recommend and click next, and choose recommend again and click next.

In the current section, select create new virtual disk and click next.

![pfSense installation screen](pictures/wmaware9.png)

Size 20gb and select single Virtual disk.

![pfSense installation screen](pictures/wmare10.png)

Click next on the next page and then click finish. If there is any checkbox that says Power On this vm, uncheck it. We will make adjustments before starting the vm.

Your Virtual machine will appear on the left panel. Right-click it, then go to manage, then click settings. This panel will appear:

![pfSense installation screen](pictures/wmare11.png)

Click add and choose network adapter, then click finish:

![pfSense installation screen](pictures/wmware12.png)

Click the newly added network adapter and in the right pane select host only:

![pfSense installation screen](pictures/wmware13.png)

Now click cd/dvd and select the iso file that you downloaded and click ok to close the settings tab, and click the PfSense and select start the VM.

---

## Now let's install and configure PfSense

After launch, wait a little bit and the install page will appear:

![pfSense installation screen](pictures/pfsense1.png)

Choose insall and press ok:

![pfSense installation screen](pictures/pfsense2.png)

Select Continue with default keymap and press select:

![pfSense installation screen](pictures/pfsense3.png)

Select Auto(ZFS) and press OK:

![pfSense installation screen](pictures/pfsense4.png)

Select install and press Select:

![pfSense installation screen](pictures/pfsense5.png)

Choose stripe and press ok:

![pfSense installation screen](pictures/pfsense6.png)

Press spacebar to select disk and press ok:

![pfSense installation screen](pictures/pfsense7.png)

Click yes to erase the disk:

![pfSense installation screen](pictures/pfsense8.png)

Wait for install to complete. After the install is completed, select no, then reboot it:

![pfSense installation screen](pictures/pfsense9.png)

Wait for it to start and you will see the main panel:

![pfSense installation screen](pictures/pfsense10.png)

You will see two ip addresses, one for wan and one for lan. We will access the admin panel via an address, so we have to configure it in order to reach it from windows.

Choose 2 from the list and enter:

![pfSense installation screen](pictures/pfsense11.png)

Select 2:

![pfSense installation screen](pictures/pfsense12.png)

Enter the desired ip address that situates in the same subnet. To know your machine ip, go to windows and type ipconfig.

you will see vmware host only or vmnet1 ip and subnet. In this case my subnet is 211, so I will set an ip with subnet zero.

![pfSense installation screen](pictures/pfsense13.png)

Set subnet count to 24, press enter:

![pfSense installation screen](pictures/pfsense14.png)

Press enter for none:

![pfSense installation screen](pictures/pfsense15.png)

We are not setting an ipv6 right now, so leave it none and press enter. Type y and press enter. Type ip start range and end range according to the ip you set. Then type n and press enter because we will use https.

![pfSense installation screen](pictures/pfsense16.png)

Now you can access the internet via the provided ip address on the screen of yours, not this but what appeared on your screen.
Default creds are admin, pfsense. After that, you will be prompted to configuration. That's all for now.

![pfSense installation screen](pictures/pfsense17.png)

---

## Now Let's Install Opnsense

The configuration will be the same as pfsense. Just repeat all the steps for the configuration to the VmWare.

Let's install OPNsense now:

OPNsense installation is a bit different from PFsense. After you start the machine, this screen will appear:

![pfSense installation screen](pictures/opn1.png)

What you see is live mode without installation, so we need to install. For this, type installer to the login and type opnsense to the password field and click enter. Then the install screen will appear.

![pfSense installation screen](pictures/opn2.png)

Select Continue with default keymap and press next:

Select install(zfs):

![pfSense installation screen](pictures/opn3.png)

If it asks for more than 2gb ram, click proceed anyways:

![pfSense installation screen](pictures/opn4.png)

Select stripe:

![pfSense installation screen](pictures/opn5.png)

Press spacebar to choose disk, then press enter:

![pfSense installation screen](pictures/opn6.png)

Click yes to erase the disk and start install:

![pfSense installation screen](pictures/opn7.png)

Wait for the install to complete as pfsense:

![pfSense installation screen](pictures/opn8.png)

After the install is completed, keep or change the password if you want, then reboot and wait for it to start, then login with root and opnsense password:

![pfSense installation screen](pictures/opn9.png)

Now, as in the pfsense, we have two interfaces there and we have to configure lan one, so type 2 then choose lan (enter lan number):

![pfSense installation screen](pictures/opn10.png)

Type yes if you want dynamic p and type n if you want static ip. I choose static one:

![pfSense installation screen](pictures/opn11.png)

Enter desired ip address as in pfsensee but same subnet with host only adapter:

![pfSense installation screen](pictures/opn12.png)

Type 24 as in pfsense:

![pfSense installation screen](pictures/opn13.png)

Choose what i chose for the following questions as provided in picture:

![pfSense installation screen](pictures/opn14.png)

Choose n for certificates and n for http request. After that, setup is complete and you can access the interface via web. Default creds are root and opnsense:

![pfSense installation screen](pictures/opn15.png)

---

##Last time to install VyOS

The configuration will be the same as pfsense. Just repeat all the steps for the configuration to the VmWare.

Let's install VyOS now:

Launch the machine and you will see menu. Choose first one:

![pfSense installation screen](pictures/vyoss1.png)

After start, you will be prompted to the login screen. Login is vyos, password is vyos. Use these and log in the system:

![pfSense installation screen](pictures/vyoss2.png)

After login, this will appear:

![pfSense installation screen](pictures/vyos3.png)

Type ip addr so we will know our interfaces to configure later:

![pfSense installation screen](pictures/vyos4.png)

Now we have to go into configuration mode to configure interfaces. Type configure to the command line.
After that, write this to configure eth0 interface via dhcp: set interfaces ethernet eth0 address dhcp.

![pfSense installation screen](pictures/vyos5.png)

Now we use host only adapter ip address and subnet to configure lan interface. For that I typed
set interfaces ethernet eth1 address 192.168.211.102/24 because my ip is this.

![pfSense installation screen](pictures/vyos6.png)

Now we have to apply the config, so type commit and press enter. This will apply the configuration. Type save to save the settings. Now our interfaces are set:

![pfSense installation screen](pictures/vyos7.png)

Now type exit to go back normal mode. Now it's time to test the connection. Go to the cmd and write ping 192.168.211.102 and look for replies.

![pfSense installation screen](pictures/vyos8.png)

Now let's test Vyos if it reaches the internet. In VyOs type ping 8.8.8.8 and look for replies:

![pfSense installation screen](pictures/vyos9.png)

Install completed. That's all for now.
