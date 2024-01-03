# Linux-Setup-Tweaks-Unknows


## Sign, handwrite, sketch on PDF (stylus + mouse)
* Xournal http://xournal.sourceforge.net/


## Bluetooth
* Install Bluetooth stack if not installed  
`sudo apt install bluez bluez-tools`

* Better Bluetooth manager  
`sudo apt install blueman`. Once installed run `blueman-manager`

## Audio
* PulseAudio Voulume controll  
`sudo apt install pavucontrol`

## Set System limit for number of file watchers  
- set max_user_watches then reload and apply system parameters to the current system  
`echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf && sudo sysctl -p`

## Install ngrok
```bash
sudo apt-get update
sudo apt-get install unzip wget
wget https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-amd64.zip
unzip ngrok-stable-linux-amd64.zip
sudo mv ./ngrok /usr/bin/ngrok
ngrok
```

## How to kill a process running on particular port in Linux?
`sudo fuser -k 9229/tcp`
`npx kill-port 9229`

## Gnome screenshot tools crashing when selecting area
- Looks like a Ubuntu bug. Tool is crashing when clipboard wasn't empty when taking the screenshot. [Refs & Credit](https://askubuntu.com/questions/1227402/gnome-screenshot-area-selection-causing-freezes)  
`xclip -selection clipboard /dev/null`

## How do I set a hotkey for toggling the microphone on/off?
Credits / source: [https://forums.linuxmint.com/viewtopic.php?t=294680](https://forums.linuxmint.com/viewtopic.php?t=294680)  
`Keyboard shortcuts > Microphone mute/unmute`

# List available smb shares on a network
Credits / source: [https://serverfault.com/a/166255](https://serverfault.com/a/166255)  
This command is a very little known secret of Samba. It returns IP adresses of all Samba servers in one's own broadcast domain:

`nmblookup __SAMBA__`

This one returns a list of all NetBIOS names and their aliases of all Samba servers in the neighbourhood (it does a 'node status query'):

`nmblookup -S __SAMBA__`

This one returns a list of all IP adresses of SMB servers (that is, Linux+Unix/Samba or Windows) in the neighbourhood:

`nmblookup '*'`

Finally, all NetBIOS names and their aliases of all SMB servers (Linux+Unix/Samba or Windows):

`nmblookup -S '*'`

## APT check available packages - installed and candidates for install
`apt-cache policy nvim`

## Linux CLI

### `grep` snippets

Search for a specific pattern or text in files within a directory and its subdirectories recursively. 

```bash
grep -rn "pattern" /path/to/search
grep -rn "example" .
```

The `.` represents the current directory. Adjust the pattern and path as needed for your specific use case.

# Audio Video

## Edit video tracks - remove embeded subtitles
https://github.com/mifi/lossless-cut?tab=readme-ov-file


