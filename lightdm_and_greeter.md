# Setup lightdm and greeter documentation :

![](https://www.maketecheasier.com/assets/uploads/2018/12/ubuntu-login-screen.jpg)

Lightdm is a lightweight display manager that is used on Linux-based operating systems and replaces the default GDM manager used on Ubuntu. In our project case, we needed it for compatibility reasons with our eGalax touch drivers. A LightDM greeter is the graphical interface that is presented to the user when they are selecting their session and entering their password.

While we needed lightdm, we encountered a problem with it, namely that we couldn't get the visual keyboard to show up at the login phase. To solve this issue, we tried to install another greeter and set it up to get access to the keyboard. In the end, it didn't work and we went around the problem by enabling autologin, but we made this documentation to explain the process around lightdm and its greeters.

## Install lightdm

It's very easy to install lightdm, in your terminal, type the following command : `sudo apt-get install lightdm`

Then, you need to set it as the default display manager using the following command : `sudo dpkg-reconfigure lightdm`

This will open a configuration window that allows you to select your default display manager. Use the arrow keys to select lightdm, and press Enter to confirm your selection. If you want to go back to GDM, use the same process.

## Installing a greeter

On Ubuntu, lightdm ships with the Unity Greeter by default, which didn't allow us to use the default visual keyboard.
There are many other greeters available, Some popular ones include:
- LightDM GTK+ Greeter
- Pantheon Greeter
- Slick Greeter
- WebKit2 Greeter

To install, a greeter, run the following command (example for GTK+ greeter) : `sudo apt-get install lightdm-gtk-greeter`. Then, once it's installed, you should configure lightdm to use your new greeter by editing the former's configuration file at : `/etc/lightdm/lightdm.conf`

In the file, add underneath the [SeatDefaults] section this line : `greeter-session=<your-wanted-greeter>`

Save the file and restart lightdm : `sudo systemctl restart lightdm`

Now, whenever you start your computer, you should see your choosen greeter at startup.

## (Try) to get an onscreen keyboard for your greeter

We didn't manage to get the following to work, but this *should* be how to do it for GTK+.

Create a new file `/etc/lightdm/lightdm-gtk-greeter.conf`:

Edit it and add the following lines : 
``` 
[greeter]
keyboard=onboard
```

Save, close and restart lightdm using the same command as previously : 

`sudo systemctl restart lightdm`


## Fixing booting with no GUI

If you (like us) boot your system and find that you only have a terminal to login, you may need to follow these steps.

Make sure that it is installed : `sudo systemctl status lightdm`
If it is installed, it may not be running, launch it with : `sudo systemctl start lightdm`. If you still don't have anything, try to reconfigure your display manager with : `sudo dpkg-reconfigure lightdm`

Finally as a last resort, use the last command to switch back to gdm.

