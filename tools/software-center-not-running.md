**Make sure software-center is not running.**
First make sure the Software Center (process name software-center) is not running. 
Depending on how you've been forcing it to quit, 
a software-center process may or may not still be running in the background.

If you know how to make sure a process isn't running, you can skip the rest of this section.

You can use the GNOME System Monitor for this (type system monitor in the Unity dash and an icon for GNOME System Monitor will appear).

Or you can use **killall** from the Terminal ****(Ctrl+Alt+T):

```
killall software-center
```
Run it again and you should get:
```
software-center: no process found
```
If you don't see that, it's still running. In that case, run:
```
killall -KILL software-center
```
(Running that again will, in the same way, determine if it succeeeded)

The Software Center is not ordinarily run as root: instead, it uses **polkit** to perform specific actions as root.
But if it is running as root, then you'll have to put **sudo** before a **killall command for it to succeed.**

Clear out both user-specific and systemwide configuration files and reinstall USC.
Open a Terminal window (Ctrl+Alt+T) if you don't already have one open. Run these commands to remove user-specific configuration files:
```
cd ~/.config
mv software-center software-center.old
```
(This actually moves the configuration rather than deleting it, but it prevents it from being used. It's unlikely you'll need to restore it, but there's no major disadvantage.)

Then reinstall the Software Center, removing systemwide configuration files:
```
sudo apt-get update
sudo apt-get --purge --reinstall install software-center
```
Some errors that could interfere with the Software Center starting or working properly could also keep those commands from working.
In particular, if you see an error that says Unable to lock the administration directory, check out the answers here:

Unable to lock the administration directory **(/var/lib/dpkg/)** is another process using it?
Then try running the Software Center again.

If that doesn't work...
...then more information will be needed. Run the Software Center itself in the Terminal:
```
software-center
```
That may reveal messages **(errors or otherwise)** that would help solve the problem. You can edit your question to include all the text from the Terminal.

(Other people with this problem should create or edit their own questions, of course.)

One possible cause of this problem might be if polkit is not running, or not working properly. If you don't see any helpful messages when you run software-center in the Terminal, you might try running it as root:
```
gksudo software-center
```
If you don't have the **gksudo** command, you can install it (it's provided by the ![https://apps.ubuntu.com/cat/applications/gksu/](gksu) Install gksu package), or use **sudo -H** instead of **gksudo.**

