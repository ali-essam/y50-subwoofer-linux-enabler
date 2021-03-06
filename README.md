# Lenovo Y50 Subwoofer Enabler for Linux

Hi!

This script fixes the issue of the subwoofer of Lenovo Y50 laptops not having any sound on Linux distributions (in a dirty way!). Tested on Ubuntu 16.04 but should work on all Linux distributions.

The script `install.sh` uses `apt-get` once to install `alsa-tools`. If using a non-Debian distribution, use your package manager of choice and continue to use the script (or modify acordingly). Also, use common sense and, if you can, inspect both scripts (*which are small!*) before anything. (see **Warnings** below). 

Open `subwoofer.py` to modify helpful options:

* **speakerBalance** (values between `-100` and `100`): Sets the stereo volume balancing of the speakers. Mostly needed because the subwoofer itself is on the right of the laptop and if everything was 100% volume and no balance, it would sound debalanced anyway. (but you should check *extraVolume*)
* **headphonesBalance** (values between `-100` and `100`): In case your headphones are a bit broken (like mine) and sound debalanced, this setting will help you. Using the normal sound settings panel from your Linux distribution won't work, since balancing is being reset every time you plug the headphones in or out.
* **subwooferBalance** (values between `-100` and `100`): If at `0`, the subwoofer will get the left and right channels of the song you are playing and play them both at 100%. Set at `-25` (as it is by default) makes it so you hear 100% of the left channel but only 75% of the right channel.
* **extraVolume** (values between `-100` and `100`): Helps balancing the whole sound as mentioned, since the subwoofer is placed on the right. This limits the subwoofer's volume instead and not the speakers'. 
    * `0` is maximum subwoofer volume if general volume is at 100%;
    * `100` is maximum subwoofer volume even if the general volume is low.

Maximize it for a party by setting it at `0`. Default is `-11`.

## Warnings

The script will let the program `hda-verb`, which is usually called using `sudo`, to be called *without it* by modifying the `/etc/sudoers` file. It does so for the current user and the `guest` user. **This might be a security issue for some!**

**I am not responsible if your speakers or subwoofer breaks!** Please inspect the script by yourself if you can, making sure that everything is being protected. I've designed it to scale down anything to the maximum range of the speakers (`100` for speakers and `87` *weirdly enough* for subwoofer), so nothing should break as I use the script myself and do still want a fully working laptop.

Try not to reinstall twice as it appends the needed modifications to `/etc/sudoers` file twice. Just recopy `subwoofer.py` to its install location `/opt/subwoofer.py`.

## Needed improvements

The script doesn't take care of the subwoofer when you suspend the laptop. Therefore, a crack is heard from the subwoofer when suspending.

The script is also a dirty way to fix things. A more resposible person would report the problem as a bug and cooperate with the people related to the component that has the issue. (`alsa` I believe)

## Related links

http://superuser.com/questions/945110/how-do-i-make-my-lenovo-y50s-subwoofer-work-on-linux

http://superuser.com/questions/975219/how-to-disable-power-saving-on-my-lenovo-y50s-subwoofer-audio-pins

https://www.reddit.com/r/linuxquestions/comments/3ejkbe/how_do_i_make_my_lenovo_y50s_subwoofer_work_on/

Have fun! 
