# Getting to Know Your Pi

Plug the USB end of your Serial-TTL cable into your computer, and plug the power adapter into the wall and the microUSB port on your Pi

\(photo\)

Here's where the instructions split -- Mac go to 1A, Linux go to 1B, Windows go to 1C

### 1A. TTL connection on Mac

Follow [these installation instructions from Adafruit](https://learn.adafruit.com/adafruits-raspberry-pi-lesson-5-using-a-console-cable/software-installation-mac)

Then, download the free trial of [Serial for Mac](https://www.decisivetactics.com/products/serial/)

Open Serial and click File--&gt;Open Port...

Look for an entry for USB-Serial controller and select it, then hit Open

Hit enter twice. If nothing shows up, Click Terminal--&gt;Settings and change the baud rate from 115200 to 9600 and try again.

### 1B. TTL connection on Linux

Follow [these installation instructions from Adafruit](https://learn.adafruit.com/adafruits-raspberry-pi-lesson-5-using-a-console-cable/software-installation-linux)

Then, follow [these connection instructions from Adafruit](https://learn.adafruit.com/adafruits-raspberry-pi-lesson-5-using-a-console-cable/test-and-configure#linux)

### 1C. TTL connection on Windows

Follow [these installation instructions from Adafruit](https://learn.adafruit.com/adafruits-raspberry-pi-lesson-5-using-a-console-cable/software-installation-windows)

Then, follow [these connection instructions from Adafruit](https://learn.adafruit.com/adafruits-raspberry-pi-lesson-5-using-a-console-cable/test-and-configure#windows)

### 2. Logging in

You should now see a prompt for a login and password

The default username is pi and the default password is raspberry

#### 2a. Change the Password

We're going to connect this to the internet for ssh shortly. So we're going to change our password.

run the command:

```
passwd
```

and follow the prompts to change your password to something else

#### 2b. Allow SSH, Boot to CLI

Run the following

```
sudo raspi-config
```

And under boot options, select Console, then under Interfacing Options, select SSH and Yes to enable

When you hit finish at tho main menu, hit yes.

Once rebooted, log back in with your new password.

### 3. Connect to the WiFi

First, run

```
ifconfig
```

And make sure a wlan0 entry is in the list.

We're going to use nano \(you can use whichever cli editor you know if you want\) to set up our WiFi connection.

to open the config file, run

```
sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
```

you'll see a basic text editor

\(photo\)

at the end of this file \(use arrow keys to navigate, and spaces instead of tabs, add:

```
network={
    ssid="Our SSID"
    psk="Our Password"
}
```

hit control-x, then y, then enter to save and exit

Then, reboot with

```
sudo reboot
```

and re-run

```
ifconfig
```

after logging in. You should see an IP address in your wlan0 entry:

\(photo\)

This means you're connected to the internet!

Code time? Not Quite. First we have to install Node \(actual good node\) and update the OS.

First, we'll switch to SSH to connect to our Pi instead of our cable.

### 4. Switching to an SSH connection

Jot down your Raspi's IP address, and then open a terminal on your computer and run

```
ssh pi@your.ip.address
```

hopefully, it'll ask you for your password, and then you'll be logged in via SSH! You can remove the Serial-TTL cable and close Serial/Putty/screen.

Now for some standard maintenance...

### 5. Updating the OS

Run the following commands on your Pi

```
sudo apt-get update
sudo apt-get upgrade
```

The first should complete really quickly, the second...go stretch your legs, grab a drink of water, take your time -- average 5 minutes.

### 6. Getting Node \(that's not 0.10.x\)

NodeSource hosts Debian packages that allow us to use Node 7.x instead of being stuck on 0.10.x

To get it, run the following on the Pi:

```
curl -sL https://deb.nodesource.com/setup_7.x | sudo -E bash -
```

Once it's done:

```
sudo apt install nodejs
sudo npm i -g npm
```

This will install node 7.x and update npm to 5.x \(you'll thank me later\)

Now, NOW we can code. Kiiiiinda. We gotta wire up some lights first! But **soon.**

