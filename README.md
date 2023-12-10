# Necessita'Maestra

*Design exercises within the digital design interstices workshop.*

- [Abstract](#abstract)
- [Raspberry](#portable-raspberry-pi-4-server-for-multimedia-sharing)
- [Edit page project](#2-edit-the-pages)



# abstract

"Necessità Maestra" (Necessity is the teacher) is a reflection of the great master Leonardo da Vinci which suggests the great human ability to find solutions in situations of real necessity. The concept of digital design interstices is very close to that of the Renaissance genius: a design approach focused on resolving everyday issues by employing and reinterpreting available resources.
Workshop participants will be catapulted into the simulation of particular situations and will have to plan the use of digital tools to overcome them. We will discuss and explore together the narratives that emerge from these opportunities, in order to observe new approaches and new perspectives on designing communicative solutions.

The participants should have their own computer, the ability to use software to work on materials such as images, audio, and video, and a great capacity to design outside the box.

The projects will become the content of an exhibition that can also be visited digitally.


## Portable Raspberry Pi 4 Server for Multimedia Sharing



On this page, you will find information on how to build a portable server based on Raspberry Pi 4 for sharing text, video, images, and sound through a website, as well as instructions on how to edit or add content.

### 1.1 Install Raspberry Pi os Lite (64-bit)
[Install](https://www.raspberrypi.com/software/)  Raspberry Pi OS using Raspberry Pi Imager.
Connect the Raspberry Pi to the internet router using a LAN cable.


### 1.2 Install RaspAP

Follow the official RaspAP documentation for installation:
[RaspAP Documentation](https://docs.raspap.com/)

Update RPi OS to its latest version, including the kernel and firmware, followed by a reboot:

```bash
sudo apt-get update
sudo apt-get full-upgrade
sudo reboot
```
Install RaspAP from your device's shell prompt:

```bash
curl -sL https://install.raspap.com | bash

```
After the reboot at the end of the installation the wireless AP network will be configured as follows:
```bash
IP address: 10.3.141.1 (check this on browser)
Username: admin
Password: secret
DHCP range: 10.3.141.50 to 10.3.141.254
SSID: raspi-webgui
Password: ChangeMe
```

### 1.3 Install nodogsplash
Follow the official RaspAP documentation for Captive portal  installation:
[Captive portal setup](https://docs.raspap.com/captive/)

With our package manager up to date, install a dependency required by nodogsplash:

```bash
# Install nodogsplash
sudo apt-get update
sudo apt-get install libmicrohttpd-dev
```

Next, clone the nodogsplash GitHub repository to your home directory:


```bash
cd ~/
git clone https://github.com/nodogsplash/nodogsplash.git
```
We can now compile nodogsplash from the source:


```bash
cd nodogsplash
make
sudo make install
```
```bash
sudo nano /etc/nodogsplash/nodogsplash.conf

```
With nodogsplash installed in the Pi's system, we will make two small changes to its configuration. The nodogsplash GatewayInterface should be set to the interface RaspAP runs on (wlan0 is the default). You will also need to change the GateWayAddress to 10.3.141.1.
```bash
# GatewayInterface is not autodetected, has no default, and must be set here.
# Set GatewayInterface to the interface on your router
# that is to be managed by Nodogsplash.
# Typically br-lan for the wired and wireless lan.
#
GatewayInterface wlan0
#
# Parameter: GatewayAddress
# Default: Discovered from GatewayInterface
#
# This should be autodetected on an OpenWRT system, but if not:
# Set GatewayAddress to the IP address of the router on
# the GatewayInterface.  This is the address that the Nodogsplash
# server listens on.
GatewayAddress 10.3.141.1

```

Save and quit out of the editor by pressing Ctrl+X and then pressing Y and finally Enter.

Repair permissions to write to the folder where the site is located
```bash
sudo chmod 777 /etc/nodogsplash/htdocs
```
You can use ftp to upload a new site  ( navigate to /etc/nodogsplash/htdocs)
```bash
user: same user you set with raspberry pi imager ( usually pi)
password:  same password you set with raspberry pi imager (usually raspberry)
host: same address you used to connect with ssh

```

## 2. Edit the pages
sites/projects/project-1.html, this page will contain your project.

splash.html it’s a page that only hold an menu for each project, that you will find in the directory:
```bash
/ sites
  / spash.hmtl
  / projects   
       / project-1.html
       / project-2.html
       / project-3.html
        ...

```
project pages organized by number project-1.html, project-2.html, project-3.html, and so on...

to modify your page, download a text editor for code in your computer [sublime](https://www.sublimetext.com/) text will do. you can use your computer notepad app but we recommend an advance tool.

You can modify and add these elements.
*If you are familiar with HTML, CSS, and JS, feel free to modify as you wish.*


#### 2.1 title
change title project here
```bash
<h1 class="titolo"> change title here </h1>
```
#### 2.2 paragraph
change main text for the project here
```bash
<p class="text">

 main text here
 <br> #line break

 </p>
```


#### 2.3 video
To upload the video, save the video in .webm and copy it inside the video folder

```bash
#<h3>video</h3>
#<video class="video" autoplay controls>
        <source src="../video/here-the-name-of-the-video.webm" #type="video/webm">  
#</video>
```

#### 2.4 image
To upload the images, save them in .png and copy it inside the images folder

```bash
#<h3>image</h3>
    <img class="image"src="../images/here-the-name-of-the-image.png">

```
#### 2.5 gif
To upload the gifs, save them in .gif and copy it inside the gif folder
```bash

#<h3>gif</h3>
    <img class="gif"src="../gif/here-the-name-of-the-gif.gif">

```
