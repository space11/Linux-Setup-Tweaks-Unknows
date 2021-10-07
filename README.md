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
