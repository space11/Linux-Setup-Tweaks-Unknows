# Linux-Setup-Tweaks-Unknows


## Sign, handwrite, sketch on PDF (stylus + mouse)
* Xournal http://xournal.sourceforge.net/


# Bluetooth
* Install Bluetooth stack if not installed  
`sudo apt install bluez bluez-tools`

* Better Bluetooth manager  
`sudo apt install blueman`. Once installed run `blueman-manager`

# Audio
* PulseAudio Voulume controll  
`sudo apt install pavucontrol`

# Set System limit for number of file watchers  
- set max_user_watches then reload and apply system parameters to the current system  
`echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf && sudo sysctl -p`

# Install ngrok
```bash
sudo apt-get update
sudo apt-get install unzip wget
wget https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-amd64.zip
unzip ngrok-stable-linux-amd64.zip
sudo mv ./ngrok /usr/bin/ngrok
ngrok
```

# How to kill a process running on particular port in Linux?
`sudo fuser -k 9229/tcp`
`npx kill-port 9229`

# Gnome screenshot tools crashing when selecting area
- Looks like a Ubuntu bug. Tool is crashing when clipboard wasn't empty when taking the screenshot. [Refs & Credit](https://askubuntu.com/questions/1227402/gnome-screenshot-area-selection-causing-freezes)  
`xclip -selection clipboard /dev/null`

# How do I set a hotkey for toggling the microphone on/off?
Credits / source: [https://forums.linuxmint.com/viewtopic.php?t=294680](https://forums.linuxmint.com/viewtopic.php?t=294680)  
`Keyboard shortcuts > Microphone mute/unmute`
