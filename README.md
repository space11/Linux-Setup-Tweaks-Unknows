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
`sudo apt install pavucontrol`Fcli

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

### Fastest Way To Copy a Directory In Linux - user `tar`

```bash
cd /path/to/SOURCE_FOLDER; tar cf - . | (cd /path/to/DESTINATION_FOLDER; tar xvf -)

```
### alternatives

- Add manually Neovim to alternatives list
```bash
sudo update-alternatives --install /usr/bin/editor editor /snap/bin/nvim 1111
```
- Change the default edtiro
```bash
sudo update-alternatives --config editor 
```

### `grep` snippets

Search for a specific pattern or text in files within a directory and its subdirectories recursively. 

```bash
grep -rn "pattern" /path/to/search
grep -rn "example" .
```

## Neovim + tmux input cursor

Add to `tmux.conf` file.

```bash
# Allowe for Neovim input cursor. https://vi.stackexchange.com/a/22239
set -as terminal-overrides '*:Ss=\E[%p1%d q:Se=\E[2 q'
```

The `.` represents the current directory. Adjust the pattern and path as needed for your specific use case.

# Audio Video

## Edit video tracks - remove embeded subtitles
https://github.com/mifi/lossless-cut?tab=readme-ov-file

# Locale

Set the keyboard using the X Keyboard Extensions.

```bash
setxkbmap pl
```
# i3-wm

```bash
## Modify // Carry Window to Next Free Workspace // <><Alt> ` ##
set_from_resource $i3-wm.binding.take_next_free i3-wm.binding.take_next_free Mod1+grave
bindsym $mod+$i3-wm.binding.take_next_free exec --no-startup-id /usr/bin/i3-next-workspace --move-window-and-follow

# ## Navigate // Next Free Workspace // <> ` ##
set_from_resource $i3-wm.binding.next_free i3-wm.binding.next_free grave
bindsym $mod+$i3-wm.binding.next_free exec --no-startup-id /usr/bin/i3-next-workspace

## Modify // Move Window to Next Free Workspace // <><Shift> ` ##
set_from_resource $i3-wm.binding.move_next_free i3-wm.binding.move_next_free Shift+grave
bindsym $mod+$i3-wm.binding.move_next_free exec --no-startup-id /usr/bin/i3-next-workspace --move-window
```

## Greenclip integration for ilia (rofi alternative used in Regolith 3)
```bash
## https://github.com/erebe/greenclip/tree/master
## https://github.com/orgs/regolith-linux/discussions/953

set $greenclip /home/borys/.local/bin/greenclip

## Launch // clipboard selection // <><p>
# copy to primary selection and clipboard. Install moreutils for `ifne` that prevents emptying the selection when nothing comes out of ilia
bindsym $mod+p exec $greenclip print | ilia -p textlist -n -l "Clippboard" | ifne xclip -i -sel clipboard -f | ifne xclip -i -sel primar
exec --no-startup-id $greenclip daemon
```
