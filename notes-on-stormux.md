## What is Stormux?

Stormux is a raspberry pi image running ArchLinux. It is available from
\[stormux.org](https://stormux.org/)]. My old friend from Vinux  days, Storm Dragon, runs this site. This is image is availblefor
raspberry pi 4, 400 and 5.

## Initial Setup

It has taken me a while to get my pi mostly the way I want it. Here's
what you might do.

1.  The initial configuration works well. There are several prompts to

    - adjust the volume of the speech
    - get the user (stormux) connected to the internet
    - expand the sd card
    - Modify the locale settings as the user wishes
    - have the time synched at boot.

2.  A script is provided to perform several tasks, including setting a
    fresh user and deleting the default one.

    
configure-stormux


3.  Initially I could not update the system. There was a conflict with
    nvidia firmware. The solution to this problem was to delete the
    `linux-firmware`package and then reinstall it.

         sudo pacman -Rdd linux-firmware
         sudo pacman -Syu linux-firmware --noprogress --needed

## Setting Up Emacs

My next challenge was to get emacs speaking. I could not get `emacspeak`, `speechd-el` or even `eloud` to talk. I finally decided `fenrir` was the problem. Here are my steps to resolve this:

        - The `configure-stormux` script let's you switch to `speakup`.
        - Uninstall fenrir.
  *Once you do this, uninstall `fenrir`.
  
    sudo pacman -Rdd fenrir

        - Reboot.

2. You may not have any speech when you reboot. Log in silently, This happens every time.

3. restart the `espeakup` service, remembering to type your password.

        sudo systemctl restart espeakup.service
                         <your-password>

4. It is then possible to put `skeaku`p to sleep and run `emacs`:                         speakup plus enter. I find the enter key on a number pad works best.

5.                            To initially get `emacs` talking, do the following:

                           1. Install the `speechd-el` package:

                                  m-x package-install ret
                                  speechd-el ret
                                  m-x speechd-speak

## Final Thoughts

I did not find installing either of the desktops from the `configure-stormux` menu
    worked. I am also not really familiar with `i3` windowing system.

ArchLinux uses `yay` to install packages from the `aur`.

`markdown` does not seem to need anything special in the `init.el`
    file to get it invoked properly.

For whatever reason, `speechd-el` does not work with `org-mode`.
    Just as well. That is defiitely a rabbit hole and a time suck I have
    fallen into in the past. 
	
