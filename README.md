![Platform: ALL](https://img.shields.io/badge/platform-ALL-green)
![Dependencies: python](https://img.shields.io/badge/dependencies-python,%20jailbroken%20iOS%20device-blue)
![Follow @rubynorails on Twitter](https://img.shields.io/twitter/follow/rubynorails?label=follow&style=social)


![pyusbmux](./logo.png?raw=true)

# pyusbmux
This is a fork of [https://github.com/rcg4u/iphonessh](https://github.com/rcg4u/iphonessh), which was last updated over a decade ago.  With the upcoming deprecation of Python 2.7, I figured there should be an implementation that would work with Python 3.

First, I cleaned up some of the code and ported it to Python 3, which was a manual task and could not be accomplished simply by using `2to3` because of Python 3's change to unicode-encoded strings as a `<bytes>` type object.  Then, I made the code backward-compatible with Python 2.7.  Finally, I tested using Python 2.7 and various versions of Python 3 (3.5 - 3.8) on the following Operating Systems:

+ Ubuntu 18.04 (`libimobiledevice` installed via `apt`)
+ Arch Linux (`libimobildevice` installed via `pacman`)
+ Windows 10 (Cygwin) with only iTunes installed
+ MacOS Mojave 10.14.6 (`libimobiledevice` installed via `brew`)
*I think this will also work on MacOS with only iTunes installed, but I normally use `iproxy`, which requires `libimobiledevice` to be installed via Homebrew.*

## Use cases:
You have a jailbroken iOS device.
+ That device is some stupid implementation of `sshd` which only listens on localhost for whatever reason, and you don't have access to Cydia or a terminal app.
+ Your WiFi is down, or wireless client isolation so that you are unable to SSH to your device over the network.
+ You want the decreased latency of using a wired connection over that of a wireless connection.
+ I think this can also be used with any TCP service such as HTTP/S, VNC, etc. -- but don't hold me to that, as I have currently only tested SSH and `netcat`.
*From what I recall, there are some issues with not issuing retransmissions which could create some trouble over the socket.*

## Run:
```
git clone https://github.com/phx/pyusbmux.git
cd pyusbmux/python-client
# In terminal tab/window #1:
./tcprelay.py -t 22:2222
# In terminal tab/window #2:
ssh -p 2222 root@localhost
```
## Install:
If you want to "install" this without having to run it in place, just clone the repo and copy `tcprelay.py` and `usbmux.py` to the same location somewhere in your `$PATH`.  `usbmux.py` should retain the original name, but you can rename `tcprelay.py` to whatever you want:

```
git clone https://github.com/phx/pyusbmux.git
sudo cp iphonessh/python-client/{tcprelay.py,usbmux.py} /usr/local/bin/
sudo mv /usr/local/bin/tcprelay.py /usr/local/bin/tcprelay
```
This will allow you to run it with the command `tcprelay`.

### History:
I was not responsible for creating this program over 10 years ago, but I have made significant contributions in order to keep it updated going forward.  For this reason, I have left the original AUTHORS and README intact with the exception of adding myself to the lists of contributors.  The original README is named `README`, whereas what you are currently reading is `README.md`.

### Contribution
If you want to contribute to add features or simply help clean up and optimize code, feel free to submit a pull request.

