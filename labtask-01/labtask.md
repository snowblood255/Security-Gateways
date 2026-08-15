# Steps to install pfsense, opensense adn VyOs

First we need to download all of them.

For pfsense we will use Internet Archive site. Link is provided below. I downloaded 2.6.0 for stability and ease of use. Click ISO and start download.

Here is the link: [https://archive.org/details/pfSense-CE-2.6.0-RELEASE-amd64](https://archive.org/details/pfSense-CE-2.6.0-RELEASE-amd64)

![pfSense installation screen](pictures/pfsense-ie.png)

---

After that we have to download Opensense. Go to this site: [https://opnsense.org/download/](https://opnsense.org/download/)

![pfSense installation screen](pictures/opensensedown.png)


Choose image type DVD and click download. The download will start automatically. It will download archive file after download right click and extract it so you will find iso there.

---

Last we need download VyOS. Go to VyOS Github : [https://github.com/vyos/vyos-nightly-build/releases](https://github.com/vyos/vyos-nightly-build/releases)

Choose the latest version and click it. in our case its 2026.08.14-0025-rolling. Click on it.

![pfSense installation screen](pictures/vyos1.png)

Then scroll down to end and find asstes and in asstes there filename called `vyos-2026.08.14-0025-rolling-generic-amd64.iso`. Click on it and download will start automatically.

![pfSense installation screen](pictures/vyos2.png)

Now we downloaded all the required iso files now lets install them into Virual machine i will use VmWare for this.

---

## First lets install PfSense

Open your VmWare you will see home screen like in picture:

![pfSense installation screen](pictures/wmware1.png)

Click Create new virtual machine then click custom(advanced).

![pfSense installation screen](pictures/vmware2.png)

Click next and do not change anything in next page and clik next again. Seleck i will install operating system later and click next.

![pfSense installation screen](pictures/wmare3.png)

In the next window choose linux and Debian 12.x 64 Bit.

![pfSense installation screen](pictures/wmware4.png)

Give name to you machine and click next. I named as PfSense.

![pfSense installation screen](pictures/wmware5.png)

Set the cpu setting like in the picture below then click next:

![pfSense installation screen](pictures/wmware6.png)

Assign 2Gb Of ram in this page and click next:

![pfSense installation screen](pictures/wmawre7.png)

In current section select NAT for now and click next.

![pfSense installation screen](pictures/wmware8.png)

In next page select Recommend and click next and choose recommend again and click next.

In current section select create new virtual disk and click next.

![pfSense installation screen](pictures/wmaware9.png)

Size 20gb And select single Virtual disk.

![pfSense installation screen](pictures/wmare10.png)

Click next on next page and then click finish if there any checkbox that says Power On this vm uncheck it we will make adjustments before start the vm.

Your Virtual machine will appear on the left panel. Right click it then go to manage then click settings. This panel will appear:

![pfSense installation screen](pictures/wmare11.png)

Clcik add and chhose network adapter and click finish:

![pfSense installation screen](pictures/wmware12.png)

Click new added network adapter and in the right pane select host only:

![pfSense installation screen](pictures/wmware13.png)

Now click cd/dvd and select iso file that you downloaded and clikk ok to close the settongs tab and click the PfSense and select star the VM.

---

## Now lets install and configure PfSense

Afer launch wait a little bit and the install page will appear:

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

Cliick yes to erase the disk:

![pfSense installation screen](pictures/pfsense8.png)

Wait for install complete. After the install completed select no then reboot it:

![pfSense installation screen](pictures/pfsense9.png)

Wait for the start and you will see main panel:

![pfSense installation screen](pictures/pfsense10.png)

You will see two ip adress one for wan one for lan. We will acees the admin panel via an adress so we have to configre it in order to reach t from windows.

Choose 2 from the list and enter:

![pfSense installation screen](pictures/pfsense11.png)

Select 2:

![pfSense installation screen](pictures/pfsense12.png)

Enter the desired ip adrees that situates in same subnet to know your machine ip go windows and type ipconfig.

you will see vmware host only or vmnet1 ip and subnet. In this case my subnet is 211 so I will set an ip with subnet zero.

![pfSense installation screen](pictures/pfsense13.png)

Set subnet count to 24 press enter:

![pfSense installation screen](pictures/pfsense14.png)

Prees enter for none:

![pfSense installation screen](pictures/pfsense15.png)

We are not setting an ipv6 right now so leave it none and press enter. Type y and press enter.Type ip start range and end range according the ip you set. Then type n and press enter cause we will use https.


![pfSense installation screen](pictures/pfsense16.png)

Now you can access the internet via provided ip address on the screen of yours not this but what you appeared on your screen.
Default creds are admin , pfsense. After then you will promote to configuration. Thats all for now.

![pfSense installation screen](pictures/pfsense17.png)


## Now Lets Install Opnsense

The configuration will be the same as pfsense.Just repeat all the steps for the configure to the VmWare
Lets install OPNsense now:
OPNsense installion a bit different from PFsense after you start the machine this screen will appear:
opn1
What you see is live mode without install so we need to install.For this type installer to the login and type opnsense to the password field and click enter.Then install screen will appear
opn2

