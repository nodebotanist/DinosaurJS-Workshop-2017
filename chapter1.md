# 0. Setup

### 1. Getting your OS set up

See me for \(hopefully\) a USB drive containing the Raspbian OS image that we'll be using, and copy the image to your computer.

Then, download [Etcher](https://etcher.io) for your platform.

Insert the SD card containing the MicroSD into your computer, and follow the instructions in Etcher to burn the Rasbian image to your SD card.

While that's burning, let's assemble the Pi

### 2. Assembling your Pi

Place your Pi in the clear case, but don't put the lid on it -- we need access to those GPIO pins!

Plug one end of your ribbon cable into the Pin Expander \(the T-shaped thing with a bunch of pins on it\), and the other end onto the GPIO pins an the Raspberry Pi

\(photos\)

Then place the Pin Expander into your full-sized breadboard as shown:

\(photo\)

Grab a green, black, and white breadboard cable \(the ones with pins at both ends\), and plug them into the corresponding sockets at the end of your TTL-Serial Cable

\(photo\)

Plug the other end of the black wire into any row of the breadboard with a GND pin, the white wire into the row marked TXD, and the green wire into the row marked RXD.

\(photo/fritzing\)

Now that that's done, your OS should be ready.

### 3. Finishing the OS config

Close Etcher when it is complete, remove the SD card, **then put it right back in.**

Use a file explorer to navigate to your SD card, and go into the boot folder. Open the file config.txt in any text editor, and add the line:

```
enable_uart=1
```

to the end of the file. This will allow us to use the TTL-Serial cable to get into our raspberry pi.

After you've saved your changes, eject the SD card, remove the MicroSD card, and place it into the slot in the Raspberry Pi

\(photo\)

Now, we're ready to boot and get to know our Raspberry Pis!

