LockFortunes
=============

Dependencies
------------
 * [fortune-mod](http://en.wikipedia.org/wiki/Fortune_%28Unix%29)

**Installing from a package manager:**

*Brew*
        brew install fortune

*Fink*
        sudo apt-get install fortune-mod
        sudo apt-get install fortunes-off
        sudo apt-get install fortunes

*MacPorts* (guessing on this one)
        sudo port install fortune-mod

Usage
-----

LockFortunes is a *very* simple bash script for changing the OSX Lock Screen text to a random fortune, using *fortune-mod*.

The script is a measly one line of code:
        sudo /usr/bin/defaults write /Library/Preferences/com.apple.loginwindow LoginwindowText "$(/usr/local/bin/fortune | /usr/bin/sed "s/\"//g")"

I wrote this with the intention of running it from my *crontab*.

First, add it to the **root** crontab (*editing com.apple.loginwindow required root permissions*):
        sudo crontab -u root -e

I wanted to run it every minute:
        */1 * * * * /usr/bin/lockfortunes

Now I get a random fortune when my lock screen pops up.

**Note:** *You may have to change `/usr/local/bin/fortune` to the path of your `fortune` executable, which may vary depending on how it was installed. Find it using `which fortune`.*