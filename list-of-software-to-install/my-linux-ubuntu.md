- `sudo apt-get update`
- Install KeePassX & load passwords (if have any)
- Install Firefox: 
	- Login to Firefox with Firefox Account
	- Install Addons: 
		- https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/
		- https://addons.mozilla.org/en-US/firefox/addon/ecosia-the-green-search/
		- https://addons.mozilla.org/en-US/firefox/addon/flagfox/
		- https://addons.mozilla.org/en-US/firefox/addon/screengrab-fix-version/
		- https://addons.mozilla.org/en-US/firefox/addon/wappalyzer/
		- https://addons.mozilla.org/en-US/firefox/addon/lithuanian-spellcheck/
	- Configure:
		- Downloads dir
		- Home page
		- Etc.
- Configure Ubuntu look and behaviour:
	- // comment // https://askubuntu.com/questions/15520/how-can-i-tell-ubuntu-to-do-nothing-when-i-close-my-laptop-lid
	- `sudo nano /etc/systemd/logind.conf`
  ```
		HandlePowerKey=poweroff
		HandleLidSwitch=ignore
		HandleLidSwitchDocked=ignore
  ```
	- "Settings Power"
  ```
		Dim screen when inactive: Off
		Blank screen: Never
		When the Power Button is pressed: Power Off
  ```
	- "Language" (?)
  ```
		Input Sources > + > Lithuanian
  ```
	- "Lanuage Support"
  ```
		Language > Install / Remove Languages... > Lithuanian > Install	
		Regional Formats > Dispplay numbers, dates and currency amounts...: Lietuvių > Apply System-Wide > Close
  ```
	- `sudo apt-get install gnome-tweak-tool`
	- "Tweaks"
		> Power > Suspend when laptop lid is closed: Off
		> Top Bar > ...
		> Windows > ...
		> ...
	- "Keyboard" > Navigation
		- // comment // Change, because Ubuntu CTRL + ALT + LEFT (RIGHT) is the same as navigation (back to previous code snippet) in PHPStorm.
		- Move to workplace left > Change to "CTRL + ALT + 4"
		- Move to workplace right > Change to "CTRL + ALT + 6"
	- `touch ~/Templates/Untitled\ Document` to create "New Document" on right mouse click in dir.
	- Ctrl+H to Show hidden files of the directory or: https://askubuntu.com/questions/470837/how-to-show-hidden-folders-in-ubuntu-14-04
	
- Install additional software via Ubuntu software center:
	- `sudo apt install net-tools` (for ifconfig to work)
	- `sudo apt-get install traceroute` (for traceroute)
	- "Emacs" (GNU Emacs GUI)
	- "Gimp" (GNU Image Manipulation Program)
	- "MySQL Workbench"
	- "Slack"
	- "Skype"
	- `sudo apt-get install openjdk-8-jre` (SmartGit will need this)
	- `sudo apt-get install git`
	- "FileZilla"
	- "KDiff3"
	- "NetBeans"
	- "GtkHash"
	- "Telegram" (Official desktop version of Telegram messaging app)
	- "MonoDevelop"
		
- Generate ssh keys:
	- // comment // https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/
	- `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
	- `eval "$(ssh-agent -s)"`
	- `ssh-add ~/.ssh/id_rsa` # Add your SSH private key to the ssh-agent (check the file name)

- Make custom .bashrc file:
	- `touch ~/.bash_custom`
	- Add following lines to `~/.bachrc`:
		```
		# Custom definitions.
		if [ -f ~/.bash_custom ]; then
		    . ~/.bash_custom
		fi
		```
	- `source ~/.bashrc`

- Install additional software manualy:
	- SmartGit: 
		- `mkdir ~/software/smartgit`
		- Download from `https://www.syntevo.com/smartgit/download/`
		- Extract the content to `~/software/smartgit`
		- (Follow `~/software/smartgit/readme-linux.txt`)
		- `~/software/smartgit/bin/smartgit.sh`
		- `~/software/smartgit/bin/add-menuitem.sh`
		- `update-java-alternatives --list`
	- ArgoUML:
		- `mkdir ~/software/argouml`
		- Download from `http://argouml.tigris.org/`
		- Extract the content to `~/software/argouml`
		- (Follow `~/software/argouml/README.txt`)
		- `java -jar ~/software/argouml/argouml.jar` will run the app
	- Wine + Mono
		- `sudo apt-add-repository --remove ppa:ubuntu-wine/ppa`
		- `sudo apt purge winehq-stable wine-mono wine-gecko winetricks`
		- `sudo apt purge wine*`
		- `sudo rm -rf /var/lib/apt/lists/*`
		- `sudo rm -rf ~/.cache/wine`
		- `sudo rm -rf ~/.cache/winetricks`
		- `sudo apt clean`
		- `sudo apt autoremove`
		- `sudo apt update`
		- `sudo dpkg --add-architecture i386` If 64 bit, enable 32 bit architecture (if you haven't already)
		- `wget -nc https://dl.winehq.org/wine-builds/Release.key`
		- `sudo apt-key add Release.key`
		- `sudo apt-add-repository https://dl.winehq.org/wine-builds/ubuntu/`
		- `sudo apt-get update`
		- `sudo apt-get install --install-recommends winehq-staging`
		- `sudo apt-get install --install-recommends winehq-staging`
		- `sudo dpkg --configure -a`
		- `mono --version`
		- `wine --version`
		- `sudo apt-get install winbind`
		- `sudo apt autoremove`
		- `sudo apt update`
		- Copy Windows fonts (if have any) to: `~/.wine/drive_c/windows/Fonts` or `/usr/share/fonts/` (`gksu nautilus /usr/share/fonts`)
	- .NET Framework to Wine:
		- `mkdir ~/software/windows/windows-dot-net`
		- Download Microsoft .NET Framework 4.5: https://www.microsoft.com/en-us/download/details.aspx?id=40779 to `~/software/windows/windows-dot-net`
		- `cd ~/software/windows/windows-dot-net`
		- `wine start dotNetFx45_Full_setup.exe`
		

- // Do we need this? // "Wine"
	- Install
	- `Ctrl` + `Alt` + `T`
	- `winecfg` (Select your windows environment from here)
	- "Winetricks" > Install ##or alternative: `sudo apt-get install winetricks`
	- "Winetricks" > Install a font > OK > Select all > OK ## or alternative: `winetricks allfonts`
	- `winetricks dotnet45 && winetricks gdiplus && winetricks vcrun2008` (this is needed for Azuon)
	- `rm -rf ~/.wine && WINEARCH=win32 WINEPREFIX=~/.wine winecfg` (this is needed for Azuon)

- // Do we need this? // Install software vie "Winetricks" ("winetricks" > Install an application > OK > Check > OK):
	- vc2005express
	- vc2005expresssp1
	- vc2008express
	- vc2010express

- Install software via Wine:
	- // how to// `winefile` (Go to Shell > My Computer > Control Panel > Add/Remove Program > Install (Your windows apps)
	- [Pick Windows software and install it](my-windows-10.md)
		- // http://azuon.com/downloads/Azuon.zip
		- http://www.prestosoft.com/edp_examdiff.asp
		- http://encodingchecker.codeplex.com/
		- https://www.heidisql.com/
		- https://www.ytddownloader.com/
		- https://github.com/aleksas/laba-diena-tts
		- https://raylin.wordpress.com/downloads/md5-sha-1-checksum-utility/
		- https://www.microsoft.com/net/download
		- https://microsoft-office.en.softonic.com/
		- https://www.microsoft.com/lt-lt/download/details.aspx?id=35400
		- https://www.visualstudio.com
		- https://notepad-plus-plus.org/
		- https://ashkulz.github.io/NppFTP/
		- https://github.com/TaoK/PoorMansTSqlFormatter
		- http://www.pdfforge.org/pdfcreator
		- https://www.telerik.com/fiddler
		- https://quick-html-color-picker.en.uptodown.com/windows
		- https://sourcegear.com/diffmerge/
		- https://www.sourcetreeapp.com/
		- https://www.torproject.org/projects/torbrowser.html.en
		- https://www.vidyo.com/
		- https://vistanita-duplicate-finder.soft32.com/
		- https://www.videolan.org/vlc/index.html
		- http://winmerge.org/
		- https://www.wireshark.org/
		- https://androidmtk.com/download-blu-usb-drivers
	
- `mkdir ~/dev` (this will be for all dev projects like websites, phone apps, etc. to store)
