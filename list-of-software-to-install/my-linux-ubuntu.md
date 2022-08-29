# Intro

Before you even start with Ubuntu, you may test it or another distro, e.g. here: https://distrotest.net/

In case you are stuck with the too old Ubuntu 20.10 version (e.g. which is in EOL - End Of Life state - http://www.ubuntu.com/releaseendoflife), check:  
- https://askubuntu.com/questions/1361262/how-upgrade-ubuntu-20-10-after-its-eol  
- https://askubuntu.com/questions/760896/how-can-i-fix-apt-error-w-target-packages-is-configured-multiple-times  

# Action  (applies to Ubuntu 22.04, other versions are not tested)

Let's start with these basics:  

- `time sudo apt-get update`
- `time sudo apt update` 
- `time sudo apt-get install apt-file`
- `time sudo apt-file update`
- `sudo nano /etc/update-manager/release-upgrades`  
and change `prompt=lts` to `prompt=normal` (this will change the awareness level of new releases from LTS to normal)
- `sudo apt-get upgrade -y`
- `sudo apt-get dist-upgrade`
- `sudo do-release-upgrade`
- `sudo apt-get update`
- `sudo apt-mark showmanual` (optional) - this will list packages already installed manually, check if you are working on the clean machine :) 

Then make video recording working:  

Flatpak ( https://flatpak.org/setup/Ubuntu ) - a dependency for Kooha
  - Install Flatpak
    - In case you already do have Flatpak, just check for it:  
      - `flatpak --version` 
    - In case you don't have Flatpak, install it, this should be enough:  
      - `sudo apt install flatpak` 
      - `flatpak --version`
    - In case you still don't have Flatpack, install it like that then:
      - `sudo add-apt-repository ppa:flatpak/stable`
      - `sudo apt update`
      - `sudo apt install flatpak`
      - `flatpak --version`
  - Now, let's make it possible to install Flatpak apps without needing the command line:
    - `sudo apt install gnome-software-plugin-flatpak`
  - Let's now add the Flathub repository - the most known place to get Flatpak apps from:
    - `flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo`
    - (do we need this at all? optional?)`sudo apt-add-repository -r https://ppa.launchpadcontent.net/flatpak/stable/ubuntu`
  - Restart
  
Kooha ( https://github.com/SeaDve/Kooha ) - Video recorder that works in Wayland environment
- `flatpak install flathub io.github.seadve.Kooha` (pick y/yes all the times if requested)
- `flatpak run io.github.seadve.Kooha`  
- While the item is open - right click on the item on the toolbar and pick "Add to Favorites"
- Test by recording anything to make sure video and audio are ok
- In case of "No microphone source found", refer to https://github.com/SeaDve/Kooha/issues/177

And then we go like that:  

- "Settings" > "Appearance" > "Style" > "Dark"
- Install Firefox (You most likely already have it. If not then check https://www.mozilla.org/en-US/firefox/new/ to obtain it): 
	- Login to Firefox with Firefox Account
	- Install Addons: 
		- https://www.momentumdash.com/download (+ login)
		- https://addons.mozilla.org/en-US/firefox/addon/bitwarden-password-manager/ (+ login)
		- https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/
		- https://addons.mozilla.org/en-US/firefox/addon/youtube-nonstop/
		- https://addons.mozilla.org/en-US/firefox/addon/flagfox/
		- https://addons.mozilla.org/en-US/firefox/addon/ispell-lt/ (for the alternative way, right click on any textarea field in [any webpage](https://www.w3schools.com/tags/tryit.asp?filename=tryhtml_textarea) opened by Firefox and pick "Languages" > "Add Dictionaries..." > navigate to the language pack you want, and install each)
		- (optional) https://addons.mozilla.org/en-US/firefox/addon/wappalyzer/
		- ~~https://addons.mozilla.org/en-US/firefox/addon/screengrab-fix-version/~~
		- (optional) https://addons.mozilla.org/en-US/firefox/addon/ecosia-the-green-search/
		- (optional) https://addons.mozilla.org/lt/firefox/addon/saml-tracer/
		- (optional) https://nighteye.app/
	- Add duckduckgo as the default search engine, in case privacy maters: https://duckduckgo.com/ , check about:preferences#search > Default search engine
	- Turn on/off the extensions you want to be active (to open the Firefox extensions window: `Ctrl` + `Shift` + `A`)
	- Configure:
		- Downloads dir (go to about:preferences#general > File and Applications > do the configuration)
		- Home page (go to about:preferences#home )
		- Go to: `about:config`
			- `network.dnsCacheExpiration`: `60`
- Install Google Chrome:
	- Visit (https://www.google.com/chrome/), download, start instal by double clicking on the downloaded .deb package.
	- Login / Create the profiles to be in use (e.g. Company#1, Company#2, Personal#1, etc.) and continue the configuration under **each** profile:
		- (optional) Downloads dir
		- (optional) Go to & config: `chrome://about` , `chrome://net-internals/`
		- Install Extensions: 
			- https://chrome.google.com/webstore/detail/adblock-plus-free-ad-bloc/cfhdojbkjhnklbpkdaibdccddilifddb
			- https://chrome.google.com/webstore/detail/momentum/laookkfknpbbblfpciffpaejjkokdgca (+login)
			- https://chrome.google.com/webstore/detail/read-on-remarkable/bfhkfdnddlhfippjbflipboognpdpoeh (+login)
			- https://chrome.google.com/webstore/detail/xdebug-helper/eadndfjplgieldjbigjakmdgkmoaaaoc
			- https://chrome.google.com/webstore/detail/youtube-nonstop/nlkaejimjacpillmajjnopmpbkbnocid
			- https://chrome.google.com/webstore/detail/bitwarden-free-password-m/nngceckbapebfimnlniiiahkandclblb?hl=en (+login)
			- https://chrome.google.com/webstore/detail/scribe/okfkdaglfjjjfefdcppliegebpoegaii
			- https://chrome.google.com/webstore/detail/colorzilla/bhlhnicpbhignbdhedgjhgdocnmhomnp
			- https://chrome.google.com/webstore/detail/google-docs-offline/ghbmnnjooekpmoecnnnilnnbdlolhkhi
			- https://chrome.google.com/webstore/detail/read-aloud-a-text-to-spee/hdhinadidafjejdhmfkjgnolgimiaplp
			- (optional) https://chrome.google.com/webstore/detail/data-scraper-easy-web-scr/nndknepjnldbdbepjfgmncbggmopgden
			- (optional) https://chrome.google.com/webstore/detail/simplescraper-%E2%80%94-a-fast-an/lnddbhdmiciimpkbilgpklcglkdegdkg
			- (optional) https://chrome.google.com/webstore/detail/honey/bmnlcjabgnpnenekpadlanbbkooimhnj
			- (optional) https://chrome.google.com/webstore/detail/retailmenot-deal-finder%EF%B8%8F/jjfblogammkiefalfpafidabbnamoknm
			- (optional) https://chrome.google.com/webstore/detail/wappalyzer/gppongmhjkpfnbhagpmjfkannfbllamg
			- (optional) https://chrome.google.com/webstore/detail/saml-tracer/mpdajninpobndbfcldcmbpnnbhibjmch/related?hl=en
			- (optional) https://chrome.google.com/webstore/detail/https-everywhere/gcbommkclmclpchllfjekcdonpmejbdp
			- (optional) https://nighteye.app/ or https://chrome.google.com/webstore/detail/dark-mode-night-eye/alncdjedloppbablonallfbkeiknmkdi
			- (optional) https://chrome.google.com/webstore/detail/facebook-pixel-helper/fdgfkebogiimcoedlicjlajpkdmockpc
			- (optional) https://chrome.google.com/webstore/detail/gofullpage-full-page-scre/fdpohaocaechififmbbbbbknoalclacl
			- (optional) https://chrome.google.com/webstore/detail/lastpass-free-password-ma/hdokiejnpimakedhajhdlcegeplioahd
			- (optional) https://chrome.google.com/webstore/detail/tunnelbear-vpn/omdakjcmkglenbhjadbccaookpfjihpa
		- Add duckduckgo as the default search engine, in case privacy maters: https://duckduckgo.com/
		- Turn on/off the extensions you want to be active: chrome://extensions/
	- Configure:
		- Downloads dir location change?: chrome://settings/?search=Downloads
		- Home page?: chrome://settings/onStartup
		- More languages to be supported by Chrome's spell check?: chrome://settings/languages

Now, go on with the Ubuntu software install & config as usual:
- (If running on the system with GeForce video card. Update GeForce drivers? https://askubuntu.com/questions/1030886/how-do-i-install-the-nvidia-cuda-toolkit-on-18-04-with-coffee-lake-is-it-suppo/1030901#1030901 , https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-18-04-bionic-beaver-linux )
	- `sudo apt install nvidia-cuda-toolkit`
	- `nvcc -V`
	- `sudo apt install clinfo`
	- `clinfo`
	- `ubuntu-drivers devices`
	- Look for `driver   : nvidia-driver-390 - distro non-free recommended` or similar line.
	- If driver recommendations are acceptable then run `sudo ubuntu-drivers autoinstall`. Otherwise, run `nvidia-driver-390` (according to the driver name found after `ubuntu-drivers devices`)
- "Settings" > `Region & Language` > `Manage Installed Languages` > Install / Remove Languages... (select all languages you want to use and click Apply, OK, ...)
- `sudo apt install ubuntu-restricted-extras` (Adobe Flash, some forgoten codecs, fonts, etc. https://en.wikipedia.org/wiki/Ubuntu-restricted-extras )
- Install Brave browser https://brave.com/linux/#release-channel-installation
	- `sudo apt install apt-transport-https curl`
	- `sudo curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg`
	- `echo "deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main"|sudo tee /etc/apt/sources.list.d/brave-browser-release.list`
	- `sudo apt update`
	- `sudo apt install brave-browser`
- Install Postman ( https://snapcraft.io/install/postman/ubuntu ) :
    - `sudo apt update`
    - `sudo apt install snapd`
    - `sudo snap install postman`
- (optional) Install KeePassX or other password wallet & load passwords (if have any). 
- Generate ssh keys (or copy > paste the old ones), add it to ssh agent:
	- // comment // https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/
	- `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
	- `eval "$(ssh-agent -s)"` 
	- `ssh-add ~/.ssh/id_rsa` # Add your SSH private key to the ssh-agent (check the file name)
- Config `ssh_config`:
	- `touch ~/.ssh/config`
	- Add the following to the file:
    ```
	Host a2
	    Hostname nlss1.a2hosting.com
	    User myusername
        #IdentityFile ∼/.ssh/id_rsa
	    Port 7822
	    LocalForward localhost:3306 localhost:3306
	    ForwardAgent yes
	
	Host rancher-server
	    Hostname 167.99.46.128
	    User root
	    IdentityFile ∼/.ssh/id_rsa
	    ForwardAgent yes
	```
- Make custom .bashrc file:
	- `touch ~/.bash_custom`
	- Add following lines to `~/.bashrc`:
		```
		# Custom definitions.
		if [ -f ~/.bash_custom ]; then
		    . ~/.bash_custom
		fi
		```
	- `source ~/.bashrc` (in case of error about Docker, run the command once again after the docker will be installed later on)
- Configure Ubuntu look and behaviour:
	- // comment // https://askubuntu.com/questions/15520/how-can-i-tell-ubuntu-to-do-nothing-when-i-close-my-laptop-lid
	- `sudo nano /etc/systemd/logind.conf`
  ```
		HandlePowerKey=poweroff
		HandleLidSwitch=ignore
		HandleLidSwitchDocked=ignore
  ```	
  	- "Settings" > `Privacy` > `Screen` > :
  		- `Blank Screen Delay`: `Never`
		- `Automatic Screen Lock`: `Off`
		- `Show notifications on Lock Screen`: `Off`
	- "Settings Power"
		- Dim screen when inactive: `Off`
		- Screen Blank: `Never`
		- Power Button behaviour: `Power Off`
		- Show Battery Percentage: `On`  
	- 
	- "Keyboard"
  ```
		Input Sources > + > Lithuanian
  ```
	- "Region & Language"
  ```
		Manage Installed Languages > Language > Install / Remove Languages... > Lithuanian > Install	
		Formats > Lietuva > Done
  ```
	- `sudo apt-get install gnome-tweaks`
	- "Tweaks"
		- General:
			- Suspend when laptop lid is closed: Off
		- Top Bar:
			- Weekday: `On`
			- Date: `On`
			- Seconds: `On`
			- Calendar: `Week Numbers`
	- "Settings" > Appearance:
		- Style: Dark
		- Desktop Icons > Size: Small
		- Dock > Icon size: `30`
	- "Keyboard" > Keyboard Shortcuts > View and Customize Shortcuts > Custom Shortcuts:
		- "+" >
			- Name: `xkill`, Command: `xkill`, Schortcut: `Ctrl` + `Brake`
		- Hide all normal windows > Change to "SUPER + D"
	- `touch ~/Templates/Untitled\ Document` to create "New Document" on right mouse click in dir.
	- `touch ~/Templates/wine-programname.desktop` to create "New Document" on right mouse click in dir.
		- Copy > Paste the following code to `~/Templates/wine-programname.desktop`:
		 ```
		[Desktop Entry]
		Name=The Programs Name
		Comment=Information About The Program
		Exec=wine "c:\full\path\to\the\program.exe"
		Terminal=false
		Type=Application
		Icon=wine-notepad
		Categories=Wine-Programs-Accessories;
		```
	- Ctrl+H to Show hidden files of the directory or: https://askubuntu.com/questions/470837/how-to-show-hidden-folders-in-ubuntu-14-04  
	
- Install clipboard manager:
	- https://github.com/hluk/CopyQ  
	
- Install additional software via Ubuntu software center:
	- `sudo apt install aptitude` - helps to resolve conflicts
	- (optional)(, e.g. in case you have issues with sound, incl. microphone): Enable noise cancelation feature: https://www.youtube.com/watch?v=gKsBAEnVxEA&t=196s , https://github.com/alfredh/baresip/wiki/Using-PulseAudio:-module-echo-cancel
		- `sudo nano /etc/pulse/default.pa` and add the following at the end:
			```
			load-module module-echo-cancel source_name=baresip aec_method=webrtc format=s16le rate=8000 channels=1
			set-default-source baresip
			set-default-sink 2
			```
		- Restart pulseaudio:
			- `pulseaudio -k`
			- `pulseaudio --start`
		- Verify if your sink and source was properly created:
			- `pacmd list-sources`
			- `pacmd list-sinks`
			- (confirm if driver: `<module-echo-cancel.c>` was loaded in your default sink.)
		- Go to `Settings` > `Sound` > `Input` > pick the new device noticing noise cancelation as a feature. If nothing new is in there or noise cancelation does not work properly then restart the computer and check this one again.
	- `sudo apt-get install unrar`
	- `sudo apt-get install file-roller`
	- `sudo apt install glogg` - https://glogg.bonnefon.org/
	- `sudo apt-get install fim` - fim - fbi (linux framebuffer imageviewer) improved
	- `sudo apt install htop`
	- `sudo apt install atop`
	- `sudo apt-get install iotop` (for monitoring disk usage)
	- `sudo apt install tree`
	- `git --version` (git comes by default but lets be sure...)
		- `sudo apt install gitk`
	- `sudo apt install gource` (http://gource.io/)
	- `sudo apt-get install okular` 
		- For PDF reading in black background: `Settings/Configure Okular.../Accessibility` by checking `Change colors` then `Color mode: Change Paper Color`
	- `sudo apt install ruby`
	- `sudo apt install nmap` (for pinging over network)
	- `sudo apt-get install dnsutils` (mainly for having `dig`: https://linux.die.net/man/1/dig )
	- `sudo apt install xclip` (for usage like: `cat ~/.ssh/id_rsa.pub | xclip -sel clip`)
	- "Flameshot" (for taking screenshots and draw something on it later on)
	- "GNOME Clocks" - timer, world clock, alarms, stopwatch
	- `sudo apt install net-tools` (for ifconfig to work)
	- `sudo apt-get install traceroute` (for traceroute)
	- `sudo apt-get install curl`
	- "Emacs" (GNU Emacs GUI)
	- "KolourPaint" (Microsoft Paint-alike software)
	- "Gimp" (GNU Image Manipulation Program)
	- `sudo apt install mysql-server`
	- (optional) Secure MySQL, create a user for MySQL access
	  - `sudo mysql` - this will log you in by default, no passwords needed so far..
	  - `ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password by 'mynewpassword';`  - execute this one on MySQL server after you log in to it with `sudo mysql`, do chnage the password to your own. Then exit MySQL and run the next command in the Terminal.
	  - `sudo mysql_secure_installation`
	- "MySQL Workbench"
	  - `sudo snap connect mysql-workbench-community:password-manager-service :password-manager-service` - to avoid credentials storing error as mentioned [here](https://stackoverflow.com/questions/42671914/mysql-workbench-not-saving-passwords-in-keychain).
	- "Slack"
	- "Skype"
	- `sudo apt-get install git`
		- (Configure Git globals)
		- `git config --global user.name "Paulius Macernis"`
		- `git config --global user.email sugalvojau@gmail.com`
		- `touch ~/.gitignore`
		- `git config --global core.excludesfile '~/.gitignore'`
		- `git config --global core.filemode false`
		- `echo "/.idea" >> ~/.gitignore`
		- `git config --list`
	- "FileZilla"
	- "KDiff3"
	- (optional) "NetBeans"
	- "GtkHash"
	- "Telegram" (Official desktop version of Telegram messaging app)
		- Login to all phone numbers (aka. accounts) on the mobile phone. In case of VoIP service usage (e.g. you host a number at Fongo), use the code verification option with the voice which appears to be an option in case the code verification option with the sms message does not work for you in ~3 minutes of the trying. And this will most likely be the case for Fongo and alike users because Fongo does not receive sms messages from Telegram verification but receives voice calls well.
		- Only then we set up Telegram appication on desktop. In order top set up it on desktop, we will need to scan the QR code provided by the Telegram desktop app.
	- Establish VPN connection to the location of your choice  
		- Create an account or login to https://account.protonvpn.com/
		- Download the config file (1. Select platform - GNU/Linux; 2. Select protocol - TCP; 3. Select config file and download - Free server configs
; Click to download the file of the server of your choice) : https://account.protonvpn.com/downloads#openvpn-configuration-files
		- Get Username and Password: https://account.protonvpn.com/account#openvpn
		- "Settings" > "Network" > VPN "+" > "Import from file..." > load the downloaded file > append useranme and password of your account we have just checked for > "Add" button > toggle the connection button to make it on > Wait for the VPN connection to be established and check if you have the IP of other place, e.g. here: https://www.whatismyip.com/
		- Turn on/off the connection whenever you like by toggling the connection button
	- "Signal"
	- Sublime IDE (aka. Sublime Text)
		- `wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/sublimehq-archive.gpg`
		- `echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list`
		- `sudo apt-get update`
		- `sudo apt-get install sublime-text`
		- `sudo apt-get install apt-transport-https`
	- JAVA
		- ~~sudo apt-get install openjdk-8-jre (SmartGit will need this)~~  
		- `sudo apt install openjdk-18-jdk` (JWildfire will need this)
	- JWildfire ( https://jwildfire.overwhale.com/ ) - for generating fractals
		- `java -version` (make sure java exists)
		- `echo $JAVA_HOME` or check if the content in `/usr/lib/jvm/` exists (we will need the path to java if it's not detected later on; it is detected most of the times, according to the practice of mine)
		- `mkdir ~/software/j-wildfire/`  
		- Extract the contents of Zip-Archive found in [https://jwildfire.overwhale.com/](https://jwildfire.overwhale.com/)
		- `java -jar j-wildfire-launcher.jar` to run it
		- (if java is not found) Press the "Add runtime"-button in JWildfire and select the path, which was displayed under 3., for example /usr/lib/jvm/java-11-oracle
		- To export images:
			- "Random batch" button click
			- Double click on the generated image you like
			- Set "Resolution" and "Quality" dropdowns to the max or to the numbers required by yourself (the dropdowns are on the upper right corner of UI)
			- "Render" button > Give the name and location for the output, e.g. myimage > Save
			- Wait for the progress bar to reach 100% and complete
			- Check the directory for the generated png file			
	- (optional) "Sound Recorder" by The GNOME Project
	- (optional, does it exist at all?) "MonoDevelop"
	- "VLC media player" (Read, capture, broadcast your multimedia streams)
	- VirtualBox - run several virtual systems on a single host computer
	  - "VirtualBox" - install it
	  - Install Guest additions into each VirtualBox hosted OS, e.g. the Ubuntu 22.04 OS running on VirtualBox as a virtual machine (in case you want more info: https://www.itzgeek.com/how-tos/linux/ubuntu-how-tos/how-to-install-virtualbox-guest-additions-on-ubuntu-22-04.html )
	    - Host OS (aka. main OS)
	      - `sudo apt update`  
	      - (optional?) `sudo add-apt-repository multiverse` (What's multiverse? Read this: https://itsfoss.com/ubuntu-repositories/ )
	      - (optional) `sudo cat /etc/apt/sources.list`  (in case you are curious...)
	      - (optional) `sudo cat /etc/apt/sources.list.d`  (in case you are very curious...)
	      - `sudo apt install -y build-essential` (The build-essential package actually belongs to Debian. It is not a piece of software in itself. It contains a list of packages that are required to create a Debian package (deb). These packages are libc, gcc, g++, make, dpkg-dev etc. Read more: https://itsfoss.com/build-essential-ubuntu/ )
	      - `sudo apt install -y linux-headers-$(uname -r)` (to install the sources for your kernel specific version, read more: https://superuser.com/questions/697024/what-does-apt-get-install-linux-headers-generic-do)
	      - (optional) `apt-cache policy build-essential` (in case you wonder where "build-essential" came from.. read this: https://askubuntu.com/questions/8560/how-do-i-find-out-which-repository-a-package-comes-from ; in my case it seems it comes from the main, so adding multiverse may be redundant)
	      - (optional) `apt-cache policy linux-headers-$(uname -r)` (Again, in my case it seems it comes from the main, so adding multiverse may be redundant)
	      - (optional?) `sudo apt install virtualbox-guest-utils` (in my case, this comes from multiverse repo; x86 virtualization solution - non-X11 guest utilities ?; Read more:  https://packages.ubuntu.com/jammy/virtualbox-guest-utils )
	      - (optional?) `sudo apt install virtualbox-guest-x11` (in my case, this comes from multiverse repo; This package provides the X11 guest utilities for VirtualBox. These utilities are meant to be run inside the virtual machine. They provide closer integration and improve the interactive performance; read more: https://packages.ubuntu.com/jammy/virtualbox-guest-x11 )
	      - `mkdir -p  ~/virtualbox-shared`
	    - Hosted OS (aka. OS installed on VirtualBox)
              - Then do the changes on the guest OS - Ubuntu 22.04
	        - Install OS on the VirtualBox
	        - (optional?) `sudo apt update`
	        - (optional?) `sudo add-apt-repository multiverse`
	        - (optional?) `sudo apt install virtualbox-guest-utils virtualbox-guest-x11`
	        - Devices > Insert Guest Additions CD Image ( ...may be on `~/.config/VirtualBox/VBoxGuestAdditions_6.1.34.iso` or similar, or download it by yourself to the location you wish)
	        - `sudo mount /dev/cdrom /media` (or just check if the cd is available, because it may be mounted already by Ubuntu OS itself automatically)
	        - `cd /media`
	        - `sudo ./VBoxLinuxAdditions.run`
	        - `sudo reboot`
	        - `lsmod  | grep vbox` - once booted back up, you can confirm that Virtualbox guest additions is running on your system with this command
	    - (optional?) `sudo reboot`
	- `mkdir -p ~/dev ~/software`
	- (PHP)
		- `sudo apt install php`
		- `php --version`
		- `sudo apt install php-xml`
		- `sudo apt install php-mbstring`
		- `sudo apt-get install php-pear`
		- `pecl help version`
		- `php -m | egrep -i mcrypt`
		- `sudo apt update`
		- `sudo apt install -y build-essential`
		- `gcc --version`
		- `make --version`
		- `sudo apt install php php-pear php-dev libmcrypt-dev`
		- `which pecl`
		- `pecl help`
		- `sudo pecl channel-update pecl.php.net`
		- `sudo pecl update-channels`
		- `sudo pecl search mcrypt`
		- `sudo pecl install mcrypt`
		- Add `extension=mcrypt.so` to the following files: `sudo nano /etc/php/*/cli/php.ini`, `sudo nano /etc/php/*/apache2/php.ini`
		- `php -m | grep mcrypt`
		- `sudo apt-get install libcurl4-openssl-dev`
		- `sudo systemctl restart apache2`
	- (Graphviz - Graph Visualization Software (http://www.graphviz.org/)) -- ~draw graphs to image
		- `sudo apt install graphviz`
		- `dot -V`
		- `echo 'digraph { a -> b }' | dot -Tsvg -o ~/Desktop/output.svg` 
		- Check the files generated, if the content is there
	- `sudo apt install cmake`
	- `sudo apt install devscripts`
	- `sudo apt-get install debhelper`
	- `sudo apt-get install extra-cmake-modules`
	- `sudo apt-get install kdevelop-pg-qt`
	- `sudo apt-get install kdevplatform-dev`
	- `sudo apt-get install kdoctools5` ~~`sudo apt-get install kdoctools-dev`~~
	- `sudo apt-get install kinit-dev`
	- `sudo apt-get install libboost-dev`
	- `sudo apt-get install libkf5crash-dev`
	- `sudo apt-get install libkf5kdelibs4support-dev`
	- `sudo apt-get install libqt5svg5-dev`
	- `sudo apt-get install libxml2-dev`
	- `sudo apt-get install libxslt1-dev`
	- `sudo apt-get install pkg-kde-tools`
	- https://github.com/PauliusMacernis/RegularWebcamAndScreenShots -- install by using the instructions given in the README.md file; the code makes screenshots every 300 seconds, it is every 5 minutes, - useful for tracking "what I was on during past time"
	- `sudo apt-get install rlwrap` (Clojure dependency)
	- Install Clojure (https://clojure.org/guides/getting_started#_installation_on_linux)
		- (check the link above for the newer install instructions, the following instructions may be too old though) 
		- `curl -O https://download.clojure.org/install/linux-install-1.9.0.381.sh`
		- `chmod +x linux-install-1.9.0.381.sh`
		- `sudo ./linux-install-1.9.0.381.sh`
	- Install Leiningen (https://leiningen.org/)
		- Download the lein script: https://raw.githubusercontent.com/technomancy/leiningen/stable/bin/lein
		- Place it on your `$PATH` where your shell can find it (eg. into `/usr/bin` dir)
		- Set it to be executable (`sudo chmod a+x /usr/bin/lein`)
		- Run it (`lein`) and it will download the self-install package
	- Install [Umbrello] (https://umbrello.kde.org/)
		- `mkdir -p ~/software/umbrello`
		- `cd ~/software/umbrello`
		- `dget https://archive.neon.kde.org/user/pool/main/u/umbrello/umbrello_18.04.1-0neon+16.04+xenial+build43.dsc`
		- `dpkg-source -x umbrello_18.04.1-0neon+16.04+xenial+build43.dsc`
		- `cd umbrello-18.04.1/`
		- `dch -i` (in case we want to change the changelog)
		- `dpkg-buildpackage -rfakeroot`
		- `cd ..`
		- `sudo dpkg -i umbrello_18.04.1-0neon+16.04+xenial+build43_amd64.deb`
	- "Wireshark" ( https://www.wireshark.org/ )
	- "notepadqq"
	- "Eclipse" (Extensible Tool Platform and Java IDE)
		- (Papyrus)
			- Help > Check for Updates...
			- Help > Install new software... > 
				- Work with: `http://download.eclipse.org/modeling/mdt/papyrus/updates/releases/oxygen/` > Select all > Next
				- Keep my installation the same and modify the items being installed to be compatible > Next
				- Next
				- Accept all licenses > Finish
			- Help > Check for Updates...
			- Do you trust these certificates? Select All > Accept selected
			- Restart Now
	- Vidyo (16.10 - works, 18.04 - does not work)
		- Download Vidyo installer (.deb) file from here: http://information-technology.web.cern.ch/services/fe/downloads/Vidyo
		- Rename the file to `vidyodesktop.deb` and place under home (`~`) dir
		- `cd ~`
		- `dpkg-deb -x vidyodesktop.deb vidyobuild`
		- `dpkg-deb --control vidyodesktop.deb vidyobuild/DEBIAN`
		- `nano vidyobuild/DEBIAN/control`
		- Replace the entire Depends: line by copying and pasting the following: `Depends: libxss1,libaudio2,libasound2,libqt4-network`
		- `dpkg-deb -b vidyobuild vidyodesktop-custom.deb`
		- `sudo dpkg -i vidyodesktop-custom.deb`
	- (Stride)
		- `sudo sh -c 'echo "deb https://packages.atlassian.com/debian/stride-apt-client $(lsb_release -c -s) main" > /etc/apt/sources.list.d/atlassian-stride.list'`
		- `wget -O - https://packages.atlassian.com/api/gpg/key/public | sudo apt-key add -`
		- `sudo apt-get update`
		- `sudo apt-get install stride`
	- ~~(HipChat for Ubuntu 17.10, follow: https://www.hipchat.com/downloads , Upgraded to Stride)~~
		- ~~`sudo sh -c 'echo "deb https://atlassian.artifactoryonline.com/atlassian/hipchat-apt-client $(lsb_release -c -s) main" > /etc/apt/sources.list.d/atlassian-hipchat4.list'`~~
		- ~~`wget -O - https://atlassian.artifactoryonline.com/atlassian/api/gpg/key/public | sudo apt-key add -`~~
		- ~~`sudo apt-get update`~~
		- ~~`sudo apt-get install hipchat4`~~
	- ~~(HipChat for Ubuntu 18.04 LTS, follow: https://www.hipchat.com/downloads , Upgraded to Stride)~~
		- ~~`sudo sh -c 'echo "deb https://atlassian.artifactoryonline.com/atlassian/hipchat-apt-client xenial main" > /etc/apt/sources.list.d/atlassian-hipchat4.list'`~~
		- ~~`wget -O - https://atlassian.artifactoryonline.com/atlassian/api/gpg/key/public | sudo apt-key add -`~~
		- ~~`sudo apt-get update`~~
		- ~~`sudo apt-get install hipchat4`~~
		- ~~`sudo rm /opt/HipChat4/lib/libcrypto.so*` (see https://jira.atlassian.com/browse/HCPUB-6249 )~~
		- ~~`sudo ln -s /usr/lib/x86_64-linux-gnu/libcrypto.so.1.0.0 /opt/HipChat4/lib/libcrypto.so.1.0.0` (see https://jira.atlassian.com/browse/HCPUB-6249 )~~
		- ~~`sudo ln -s /usr/lib/x86_64-linux-gnu/libssl.so.1.0.0 /opt/HipChat4/lib/libssl.so.1.0.0` (see https://jira.atlassian.com/browse/HCPUB-6249 )~~
		- ~~`sudo ln -s /usr/lib/x86_64-linux-gnu/libssl.so.1.0.0 /opt/HipChat4/lib/libssl.so` (see https://jira.atlassian.com/browse/HCPUB-6249 )~~
	- (ignore)(Toggl Desktop tracker)
		- (ignore)`wget http://fr.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/libgstreamer-plugins-base0.10-0_0.10.36-1_amd64.deb`
		- (ignore)`wget http://fr.archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10/libgstreamer0.10-0_0.10.36-1.5ubuntu1_amd64.deb`
		- (ignore)`sudo dpkg -i libgstreamer*.deb`
	- (OpenVPN with SSL) (https://www.my-private-network.co.uk/ubuntu-ssl-setup/)
		- `sudo apt install openvpn`
		- `openvpn --version`
		- `sudo apt-get install network-manager-openvpn-gnome`
		- (optional) Download the [ca.crt](https://www.my-private-network.co.uk/files/ca.crt) certificate file and [tls-auth.key](https://www.my-private-network.co.uk/files/tls-auth.key) file
		- (optional) "Settings" > Network > VPN > + > OpenVPN
			- Name: `MPNGBR`
			- Gateway: `fre.mypn.co`
			- Authentication:
				- Type: Password
				- Username: MyUsername
				- Password: MyPassword
				- CA certificate: choose the ca.crt file you downloaded earlier
			- Advanced
				- Security
					- Cipher: AES-256-CBC
					- Use custom size of cipher key: off
					- HMAC Authentication: SHA-256
				- TLS Authentication
					- Subject Match: (leave it empty)
					- Verify peer (Server) certificate usage signature: On
						- Remote peer certificate TLS type: Server
					- Additional TLS authentication or encryption
						- Mode: TLS-Auth
						- Key file: select the downloaded tls-auth.key file that you’ve downloaded earlier
						- Key Direction: 1
				- OK
		- (optional) Add
		- (optional) In the icon area in the top right of the screen, left click on the Network Manager icon again. Choose VPN Connections and click on the connection you have just created. The icon should animate for a while and then have a little padlock on it to denote that the VPN has connected. Authenticate the connection with your My Private Network password as necessary. Check your IP address again, it should not be the same anymore.
		- (optional) For logs, debuging, etc: `tail -f /var/log/syslog`
- VMware Player
	- `sudo apt install build-essential`
	- Download installation file (don't wory if txt-alike): https://www.vmware.com/products/workstation-player.html
	- Make the file executable: `chmod +x VMware-Player*`
	- Run the installation file: `sudo ./Downloads/VMware-Player*`
- Configure VirtualBox for Windows10 to host:
	- "virtualBox"
	- New
	- Name: `Windows 10`, Type: `Microsoft Windows`, Version: `Windows 10 (64-bit)`
	- ...
	- Right click on the new Machine 
		- `Settings...`
			- `General` > `Advanced`
				- `Shared Clipboard`: `Bidirectional`
				- `Drag n drop`: `Bidirectional`
			- `Shared Folders` > Select all folders you ACTUALLY need (e.g. `~/virtualbox-shared`), check `Auto-mount`
	- Open the Windows10 machine window and do `Devices` > `Insert Guest Additions CD image...` > `Download` > `Download` > `Insert` > Open the image via Windows file manager (run the downloaded and inserted CD image - .iso) > Install Guest Additions to WIndows OS by following the wizzard > reboot Windows10 VM after the install when asked to.
- Install software via VirtualBox:
	- [Windows 10](https://www.microsoft.com/software-download/windows10)
		- [Mozilla Firefox](https://www.mozilla.org/en-US/firefox/new/)
		- [Google Chrome](https://www.google.com/chrome/)
		- [Filezilla FTP client](https://filezilla-project.org/)
		- [7zip archive manager](https://www.7-zip.org/download.html)
		- [Java (JRE)](https://www.oracle.com/technetwork/java/javase/downloads/)
		- [Adobe PDF reader](https://get.adobe.com/reader/)
		- [VLC media player](https://www.videolan.org/vlc/)
		- [Microsoft Office: Word, Excel, etc.](https://www.microsoft.com/en-us/download/office.aspx)
		- [CCleaner](https://www.ccleaner.com/ccleaner/download)
		- [Azuon](http://azuon.com/)
		- (optional) https://www.avg.com/en-ww/tuneup-utilities
		- (optional) https://www.adobe.com/creativecloud/
		- (optional) https://www.daemon-tools.cc/products/dtLite
		- (optional) [BLU Studio Energy 2 USB Driver](https://androidmtk.com/download-blu-usb-drivers)
- Install additional software manualy:
	- Java JDK:
		- `sudo apt-get update`
		- `sudo add-apt-repository ppa:webupd8team/java` (click `Enter` if asked)
		- `sudo apt-get update`
		- `sudo apt-get install oracle-java8-installer` (or `sudo apt-get install oracle-java9-installer` for newer)
		- Accept license terms
		- (ignore this) `sudo apt install oracle-java8-set-default`
		- `sudo update-alternatives --config java`
		- Select java8-oracle version (default is fine if java8-oracle, e.g. manual mode)
		- `java -version`
		- `javac -version`
	- IntelliJ IDEA:
		- Download the installation pack (`tar.gz`): https://www.jetbrains.com/idea/download/#section=linux
		- Extract it to `/home/paulius/software/intellij` or elsewhere.
		- `cd /home/paulius/software/intellij/bin`
		- `./idea.sh`
		- Do not import settings (or import if you want) > OK
		- Dracula theme (or any other theme you want) > Next
		- Create a desktop entry for integration with system application menu: check, For all users: check > Next
		- Create script for opening files and projects from the command line: check, `/usr/local/bin/idea` > Next
		- Plugins (defaults are ok): Next
		- Install Scala and IDE Features Trainer plugins > Start using IntelliJ IDEA
		- Configure IntelliJ IDEA (`Configure` > `Project Defaults` > `Project Structure` > `Project Settings` > `Project`):
			- Project SDK: `New...` > `JDK` > Select JDK we have installed, like `/usr/lib/jvm/java-8-oracle` > OK
			- Project language level: `SDK default`
			- `OK`
		- Configure IntelliJ IDEA (`Configure` > `Settings`):
			- `Editor` > `General` > `Auto import`:
				- Add unambiguous imports on the fly: checked
				- Optimize imports on the fly (for current project): checked
				- `Apply`
			- `Editor` > `General` > `Appearance`:
				- Show line numbers: checked
				- `OK`		
	- Docker CE:  
		- ( Follow: https://docs.docker.com/install/linux/docker-ce/ubuntu/ )
		- `sudo apt-get remove docker docker-engine docker.io`
		- `sudo apt-get update`
		- 
		  ```
		  sudo apt-get install \
		  apt-transport-https \
		  ca-certificates \
		  curl \
		  software-properties-common
		  ```
		
		- `curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`
		- `sudo apt-key fingerprint 0EBFCD88`
		- 
		  ```
		  sudo add-apt-repository \
		  "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
		  $(lsb_release -cs) \
		  stable"
   		  ```
		  
		- `sudo apt-get update`
		- `sudo apt-get install docker-ce`, if Ubuntu 18.04 LTS then: `sudo apt install docker`, `sudo apt install docker.io`
		- `sudo docker run hello-world`
		- (Follow: https://docs.docker.com/install/linux/linux-postinstall/ )
		- `sudo groupadd docker`
		- `sudo usermod -aG docker $USER`
		- Log out and log back in so that the `docker` group membership is re-evaluated.
		- `docker run hello-world`
		- `sudo chown "$USER":"$USER" /home/"$USER"/.docker -R`
		- `sudo chmod g+rwx "/home/$USER/.docker" -R`
		- `sudo systemctl enable docker` to start Docker service on system boot.
		- `echo manual | sudo tee /etc/init/docker.override` to disable loading Docker service via `upstart` on startup
		- `sudo chkconfig docker off`  to disable loading Docker service via `chconfig` on startup
		- `env | grep DOCKER_HOST` If this command returns a value, the Docker client is set to connect to a Docker daemon running on that host. If it is unset, the Docker client is set to connect to the Docker daemon running on the local host.
		- `docker --version`
		- (Install Docker Compose: https://docs.docker.com/compose/install/ )
		- [Check for the latest version number](https://github.com/docker/compose/releases), edit and run the command: `sudo curl -L https://github.com/docker/compose/releases/download/1.21.0/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose`
		- `sudo chmod +x /usr/local/bin/docker-compose`
		- [Check for the latest version number](https://github.com/docker/compose/releases), edit and run the command: `sudo curl -L https://raw.githubusercontent.com/docker/compose/1.21.0/contrib/completion/bash/docker-compose -o /etc/bash_completion.d/docker-compose`
		- Relaunch all launched terminals to utilize completion.
		- `docker-compose --version`
		- (Install Docker Machine: https://docs.docker.com/machine/install-machine/ )
		- [Check for the latest version number](https://github.com/docker/machine/releases), edit and run the command:
		  ```
		  base=https://github.com/docker/machine/releases/download/v0.14.0 &&
  		  curl -L $base/docker-machine-$(uname -s)-$(uname -m) >/tmp/docker-machine &&
  		  sudo install /tmp/docker-machine /usr/local/bin/docker-machine
		  ```
		  
		- `docker-machine --version`
		- [Check for the latest version number](https://github.com/docker/machine/releases), edit and run the command:
		  ```
		  base=https://raw.githubusercontent.com/docker/machine/v0.14.0
		  for i in docker-machine-prompt.bash docker-machine-wrapper.bash docker-machine.bash
		  do
		    sudo wget "$base/contrib/completion/bash/${i}" -P /etc/bash_completion.d
		  done
		  ```
		  
		- `source /etc/bash_completion.d/docker-machine-prompt.bash`
		- add `$(__docker_machine_ps1)` to `PS1` setting in `~/.bashrc` or in the existing`~/.bash_custom` (preffered):  
		  `PS1='[\u@\h \W$(__docker_machine_ps1)]\$ '`  
	- Rancher Compose:
		- Download the latest Rancher Compose from https://github.com/rancher/rancher-compose/releases (e.g. https://github.com/rancher/rancher-compose/releases/download/v0.12.5/rancher-compose-linux-amd64-v0.12.5.tar.gz ) to the place of your choice (e.g. `~/Desktop`), extract it.
		- Adapt the following to the path of the downloaded Rancher Compose and run: `sudo cp path/to/rancher-compose /usr/local/bin/rancher-compose` (e.g. `sudo cp /home/paulius/Desktop/rancher-compose-linux-amd64-v0.12.5/rancher-compose-v0.12.5/rancher-compose /usr/local/bin/rancher-compose`)
		- `sudo chmod u+x /usr/local/bin/rancher-compose`
		- `rancher-compose --help`
		- `rancher-compose --version`
	- Composer (PHP dependency manager):
		- `cd ~`
		- (Follow: https://getcomposer.org/download/ )
		- `php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"`
		- `php -r "if (hash_file('SHA384', 'composer-setup.php') === '544e09ee996cdf60ece3804abc52599c22b1f40f4323403c44d44fdfdd586475ca9813a858088ffbc1f233e9b180f061') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"`
		- `php composer-setup.php`
		- `php -r "unlink('composer-setup.php');"`
		- `sudo mv composer.phar /usr/local/bin/composer` to make the composer globally available.
		- `composer --version`
		- `composer self-update`
		- `composer --version`
	- SmartGit: 
		- `mkdir ~/software/smartgit`
		- Download from `https://www.syntevo.com/smartgit/download/`
		- Extract the content to `~/software/smartgit`
		- (Follow `~/software/smartgit/readme-linux.txt`)
		- `~/software/smartgit/bin/smartgit.sh`
		- `~/software/smartgit/bin/add-menuitem.sh`
		- `update-java-alternatives --list`
		- `Repository` > `Add or Create...` for each project you are developing.
		- `Git-Flow (arrow)` > `Configure...` > `Full (feature, release, hotfix, support branches` > `OK`
	- PHPStorm:
		- `sudo nano /etc/sysctl.conf`
			- Add the line: `fs.inotify.max_user_watches = 524288`, save it.
			- Apply the change: `sudo sysctl -p --system`
		- `mkdir ~/software/phpstorm`
		- Download from https://www.jetbrains.com/phpstorm/download/download-thanks.html?platform=linux
		- Extract the content to `~/software/phpstorm`
		- (Follow `~/software/phpstorm/Install-Linux-tar.txt`)
		- `cd ~/software/phpstorm/bin/`
		- `./phpstorm.sh`
		- (Configure PHPStorm)
		- File > Settings > Plugins > Install, enable and configure these:
			- PHP Annotations
			- Symfony Plugin
			- PHP Toolbox
			- SensioLabInsight (inspection)
			- Lines Sorter
			- Php Inspections (EA Extended)
			- nginx support
			- https://www.tabnine.com/
		- (optional) File > Settings > Languages & Frameworks > PHP > Symfony
			- Enable Plugin for this Project (check)
			- Web directory: `web` (Symfony3), or `public` (Symfony4)
		- (optional) File > Settings > Languages & Frameworks > PHP > Composer
			- Path to composer.json (browse to composer.json of the PHP project)
		- Xdebug configuration:
			- Install and enable `xdebug` inside Docker container or elsewhere by following: https://xdebug.org/docs/install
			- Use the following settings in `xdebug.ini` (`php --ini` will help finding the file):
                          
               ```
               [xdebug]
               xdebug.default_enable=1
               xdebug.remote_autostart=1
               xdebug.remote_connect_back=1
               xdebug.remote_port=9001
               xdebug.remote_enable=1
               xdebug.idekey=DOCKER_XDEBUG
               ```
                           
			- File > Settings > Languages & Frameworks > PHP > Debug:
				- Debug port: `9001`
			- Click the Xdebug bar (usually in the top right corner) drop-down and click `edit configurations...`
			- Click the plus (`+`) button in the top left and select `PHP Web Page` to create a run configuration
			- Give the application a name (i.e., `Localhost`), and then click the `...` button to add a server.
			- Server Host: `localhost`
			- Server Port `8080` (or any other port used to connect to the project, e.g. the case: `http://localhost:8080/test`)
			- Server Debugger: `Xdebug`
			- Use pat mappings (...) - `checked`. 
			- Map your local project path to the path on the server (e.g. `/srv/app`) so Xdebug knows how to map files correctly
			- Once you have configured the web server and run configuration, toggle the `start listening for PHP Debug Connections` icon
		- Change PHPStorm settings to prevent closing old tabs: File > Settings > Editor > General > Tabs > Tab Closing Policy > Tab limit: `999`
		- `File` > `Settings...` > `Keymap`. Check if keymaps are as expected. If not then edit the keymap of the interest. Keymap of PHPStorm may conflict with Keymap of Ubuntu ("Keyboard shortcuts").:
			- Check `Main menu` > `Navigate` > `Back` 
				- In case of Conflict with Ubuntu keymap: "Keyboard shortcuts" > `Move to workplace left` > Change to `CTRL` + `ALT` + `4` or other.
			- Check `Main menu` > `Navigate` > `Forward`
				- In case of Conflict with Ubuntu keymap: "Keyboard shortcuts" > `Move to workplace right` > Change to `CTRL` + `ALT` + `6` or other.
		- PHP CodeSniffer ( https://github.com/squizlabs/PHP_CodeSniffer )
			- Go to `File` > `Settings...` > `Editor` > `Inspections` > `PHP` > `PHP Code Sniffer validation` (select this) > Coding standard:" (select the one you want to use)
		- PHP Code Beautifier and Fixer ( `phpcbf` )
			- Go to `File` > `Settings...` > `Tools` > `External Tools`
			- Click on `+` to add one more tool, set requested settings as follows:
				- Name: `phpcbf`
				- Group: `External Tools`
				- Description: `Fix PHP Codesniffer warnings using phpcbf`
				- Tool Settings > Program: `/home/username/.config/composer/vendor/squizlabs/php_codesniffer/bin/phpcbf` (edit to meet you path to `phpcbf`)
				- Tool Settings > Arguments: `--standard=symfony2 $FileDir$/$FileName$` (edit to the standard you want to use)
				- Tool Settings > Working directory: `$ProjectFileDir$`
				- Show in > Main menu: `checked`
				- Show in > Editor menu: `checked`
				- Show in > Project views: `checked`
				- Show in > Search result: `checked`
				- Advanced option > Synchronize files after execution: `checked`
				- Advanced option > Open console for tool output: `checked`
				- Advanced option > Make console active on message in stdout: `checked`
				- Advanced option > Make console active on message in stderr: `checked`
				- Output filters: `` (leave it empty)
				- Save it by clicking `OK`
		- PHPStorm: install upsource plugin, connect to upsource.
			- PHPStorm > Tools > Upsource > Connection: 
				- Server URL: http://upsource.example.com:3333
				- Disable SSL certificate validation: Checked (make sure you need this)
		- Any other external tools? ( https://www.jetbrains.com/help/phpstorm/external-tools.html )
		- Extra keyboard shortcut needed? For example, for `phpcbf`?
			- `Settings` -> `Keymap`
		- PHP Mess Detector ( https://confluence.jetbrains.com/display/PhpStorm/PHP+Mess+Detector+in+PhpStorm )
	- ArgoUML:
		- `mkdir ~/software/argouml`
		- Download from `http://argouml.tigris.org/`
		- Extract the content to `~/software/argouml`
		- (Follow `~/software/argouml/README.txt`)
		- `java -jar ~/software/argouml/argouml.jar` will run the app
	- - (optional, that's more of a PHP5 tool, not really PHP7+) (phUML (https://github.com/jakobwesthoff/phuml), requires Graphviz)
		- `git clone https://github.com/jakobwesthoff/phuml`
		- `cd phuml/src/app/`
		- `./phuml -h`
		- `./phuml -l`
		- (test) `./phuml -r /var/www/php_app_folder -graphviz -createAssociations false -neato output_image.png`
		- (make a symlink to `/usr/bin/phuml` or so?)
	- (PhpDependencyAnalysis (https://github.com/mamuz/PhpDependencyAnalysis), requires Graphviz)
		- `curl -OsSL https://raw.github.com/mamuz/PhpDependencyAnalysis/master/download/phpda.pubkey`
		- `curl -OsSL https://raw.github.com/mamuz/PhpDependencyAnalysis/master/download/phpda`
		- `chmod +x phpda`
		- `sudo mv phpda /usr/bin/phpda`
		- `sudo mv phpda.pubkey /usr/bin/phpda.pubkey`
		- `sudo phpda update`
		- `phpda --version`
	- (KCachegrind: https://kcachegrind.github.io - profile data visualization, e.g. PHP debugging)
	- youtube-dl (media downloader):
		- `sudo curl -L https://yt-dl.org/downloads/latest/youtube-dl -o /usr/local/bin/youtube-dl`
		- `sudo chmod a+rx /usr/local/bin/youtube-dl`
		- Test it: `youtube-dl https://www.youtube.com/watch?v=FM7MFYoylVs`
	- Chef Development Kit
		- Download and install: https://downloads.chef.io/chefdk/3.9.0#ubuntu
	- TBD: Anbox ( https://anbox.io/ ):
		- Install Kernel Modules ( https://docs.anbox.io/userguide/install_kernel_modules.html )
		- Other ( https://docs.anbox.io/userguide/install.html )
	- TBD: Darling ( https://darlinghq.org/, https://docs.darlinghq.org/build-instructions.html )
	- TBD: snap ( https://snapcraft.io/docs/getting-started#heading--install ) -- it may be installed by default already.
	- Wine + Mono
		- (Clean up if needed)
			- `sudo apt purge win*`
			- `sudo apt autoremove`
			- `sudo apt update`
			- `sudo apt-add-repository --remove ppa:ubuntu-wine/ppa`
			- `sudo apt purge winehq-stable wine-mono wine-gecko winetricks`
			- `sudo apt purge wine*`
			- `sudo rm -rf /var/lib/apt/lists/*`
			- `sudo rm -rf ~/.cache/wine`
			- `sudo rm -rf ~/.cache/winetricks`
			- `sudo apt clean`
			- `sudo apt autoremove`
			- `sudo apt update`
		- (Add repository)
			- `sudo dpkg --add-architecture i386` If 64 bit, enable 32 bit architecture (if you haven't already)
			- `wget -nc https://dl.winehq.org/wine-builds/Release.key`
			- `sudo apt-key add Release.key`
			- `sudo apt-add-repository https://dl.winehq.org/wine-builds/ubuntu/`
			- (If Ubuntu 18.04 LTS)
				- `sudo nano /etc/apt/sources.list`
				- Change distro: `https://dl.winehq.org/wine-builds/debian/ beaver main` to `https://dl.winehq.org/wine-builds/debian/ artful main`
			- `sudo apt install mono-runtime` (not sure if works on versions before 18.04 LTS)
			- `sudo apt-get update`
			- `reboot` (Restart the computer if were cleaning up)
		- (Install)
			- `sudo apt-get install --install-recommends winehq-staging`
			- `sudo apt-get install --install-recommends winehq-staging`
			- `sudo dpkg --configure -a`
			- `mono --version`
			- `wine --version`
		- (Extras and Config)
			- `sudo apt-get install winbind`
			- `sudo apt-get install winetricks`
			- `sudo apt autoremove`
			- `sudo apt update`
			- `winecfg` (Select your windows environment from here)
				- Install all additional packages if asked before Wine configuration window opens up.
			- `winecfg` > Drives > Add > H: > OK > Select `H:` > Browse... > Select /home/{user} dir > Apply > OK
			- `winetricks`
				- > Select the default wineprefix > OK > Install a font > OK > Select all 
				- or alternative: `winetricks allfonts baekmuk cambria cjkfonts consolas constantia corefonts droid eufonts fakechinese fakejapanese fakejapanese_ipamona fakekorean ipamona liberation lucida opensymbol tahoma takao uff unifont wenquanyi`
			- (Import Windows fonts if have any)
				- Copy Windows fonts (if have any) to: `~/.wine/drive_c/windows/Fonts`
				- or copy Windows fonts (if have any) to: `/usr/share/fonts/` (`gksu nautilus /usr/share/fonts`)
	- `sudo apt update`
	- `sudo apt-get upgrade`
- Install software via Wine:
	- // how to// `winefile` (Go to Shell > My Computer > Control Panel > Add/Remove Program > Install (Your windows apps)
	- [Pick Windows software and install it](my-windows-10.md)
		- http://www.prestosoft.com/edp_examdiff.asp
			- `mkdir ~/software/windows/ExamDiff`
			- `cd ~/software/windows/ExamDiff`
			- (Download the software to current dir)
			- `wine start ed19_setup.exe`
			- Test it: `wine start /unix ~/.wine/drive_c/Program\ Files/ExamDiff/ExamDiff.exe`
		- http://encodingchecker.codeplex.com/
			- `cd ~/`
			- `wget https://codeplexarchive.blob.core.windows.net/archive/projects/EncodingChecker/EncodingChecker.zip -O encodingchecker.zip`
			- `mkdir ~/software/windows/encoding_checker`
			- `unzip ~/encodingchecker.zip -d ~/software/windows/encoding_checker`
			- `rm ~/encodingchecker.zip`
			- `cd ~/software/windows/encoding_checker`
			- `unzip ~/software/windows/encoding_checker/releases/0/661fe6e2-7846-4be6-9b03-ed9346b255be -d ~/software/windows/encoding_checker`
			- Test it: `wine start EncodingChecker.exe`
			- `touch ~/wine-encodingchecker.desktop`
			- Make the content of `*.desktop` file look like this:
			```
			[Desktop Entry]
			Name=File Encoding Checker (via Wine)
			Comment=File Encoding Checker is a GUI tool that allows you to validate the text encoding of one or more files. The tool can display the encoding for all selected files, or only the files that do not have the encodings you specify. File Encoding Checker requires .NET 2 or above to run.
			Exec=wine "H:/software/windows/encoding_checker/EncodingChecker.exe"
			Terminal=false
			Type=Application
			Icon=wine-file-encoding-checker
			Categories=Wine-Programs-Accessories;
			```
			- `sudo mv ~/wine-encodingchecker.desktop /usr/share/applications/wine-encodingchecker.desktop`
		- https://www.heidisql.com/
			- `cd ~/`
			- `mkdir ~/software/windows/HeidiSQL`
			- `cd ~/software/windows/HeidiSQL`
			- `wget https://www.heidisql.com/installers/HeidiSQL_9.5.0.5196_Setup.exe -O HeidiSQL_Setup.exe`
			- `wine start HeidiSQL_Setup.exe`
			- Answer questions of Install Wizzard
			- Click `Run the application` button at the end of the installation.
			- Right click with the mouse on Icon in Ubuntu bar > `Add to Favorites`
			- Test it: `wine start /unix ~/.wine/drive_c/Program\ Files/HeidiSQL/heidisql.exe`
		- https://notepad-plus-plus.org/
			- `cd ~/`
			- `mkdir ~/software/windows/npp`
			- `cd ~/software/windows/npp`
			- `wget https://notepad-plus-plus.org/repository/7.x/7.5.6/npp.7.5.6.Installer.exe -O npp.exe` (32bit)
			- `wine start npp.exe`
			- Answer questions of Install Wizzard
			- Check `Run the application` at the end of the installation.
			- Right click with the mouse on Icon in Ubuntu bar > `Add to Favorites`
			- Test it: `wine start /unix ~/.wine/drive_c/Program\ Files/Notepad++/notepad++.exe`
		- (skip this, not working) https://quick-html-color-picker.en.uptodown.com/windows
			- Download from (https://quick-html-color-picker.en.uptodown.com/windows) to `~/software/windows/quick-html-color-picker/quick-html-color-picker-1.0.exe`
			- Test it: `wine start /unix ~/software/windows/quick-html-color-picker/quick-html-color-picker-1.0.exe`
		- https://sourcegear.com/diffmerge/
			- `cd ~/`
			- `mkdir ~/software/windows/diffmerge`
			- `cd ~/software/windows/diffmerge`
			- `wget http://download.sourcegear.com/DiffMerge/4.2.0/DiffMerge_4.2.0.697.stable_x86.msi -O DiffMerge.msi` (32bit)
			- `wine start DiffMerge.msi`
			- Answer questions of Install Wizzard
			- Check `Run the application` at the end of the installation.
			- Right click with the mouse on Icon in Ubuntu bar > `Add to Favorites`
			- Test it: `wine start /unix ~/.wine/drive_c/Program\ Files/SourceGear/Common/DiffMerge/sgdm.exe`
		- https://vistanita-duplicate-finder.soft32.com/
			- `mkdir ~/software/windows/vistanita-duplicate-finder`
			- Download from (https://vistanita-duplicate-finder.soft32.com/) to `~/software/windows/vistanita-duplicate-finder/vdf.exe`
			- `wine start /unix ~/software/windows/vistanita-duplicate-finder/vdf.exe`
			- Answer questions of Install Wizzard
			- Check `Run the application` at the end of the installation.
			- Right click with the mouse on Icon in Ubuntu bar > `Add to Favorites`
			- Test it: `wine start /unix ~/.wine/drive_c/Program\ Files/Vistanita/DF/vdf.exe`
			- `touch ~/wine-vistanitaduplicatefinder.desktop`
			- Make the content of `*.desktop` file look like this:
			```
			[Desktop Entry]
			Name=Vistanita Duplicate Finder (via Wine)
			Comment=Vistanita Duplicate Finder is a program which allows you to find duplicate files on your hard disk. It can compare all types of files even if they have different names. As it performs byte by byte comparison.
			Exec=wine "C:/Program Files/Vistanita/DF/vdf.exe"
			Terminal=false
			Type=Application
			Icon=wine-vistanita-duplicate-finder
			Categories=Wine-Programs-Accessories;
			```
			- `sudo mv ~/wine-vistanitaduplicatefinder.desktop /usr/share/applications/wine-vistanitaduplicatefinder.desktop`
		- http://winmerge.org/
			- `mkdir ~/software/windows/winmerge`
			- `wget http://downloads.sourceforge.net/winmerge/WinMerge-2.14.0-Setup.exe -O ~/software/windows/winmerge/WinMerge-Setup.exe`
			- `wine start /unix ~/software/windows/winmerge/WinMerge-Setup.exe`
			- Answer questions of Install Wizzard
			- Check `Launch the application` at the end of the installation.
			- Right click with the mouse on Icon in Ubuntu bar > `Add to Favorites`
			- Test it: `wine start /unix ~/.wine/drive_c/Program\ Files/WinMerge/WinMergeU.exe`
	
- `sudo apt-get install ttf-mscorefonts-installer` (to install Microsoft fonts, for example "Times New Roman")
- `mkdir ~/dev` (this will be for all dev projects like websites, phone apps, etc. to store)
- If still cannot find applications by just typing then create `*.desktop` files in `/usr/share/applications` by using the `*.desktop` template we made before. This is for invoking the program (e.g. wine-compatible) via quick launch.
- "Online Accounts" - add online accounts
- `Tweaks` > `Startup Applications` and pick applications to startup on boot
- `journalctl --verify` - Check the systemd journal file for internal consistency.
- Set File default opening program by going to a file's (for example, any `.php` file) properties, going to the `open with` tab, and then setting the chosen app as default one for that file type. The next time clicking `open` on the file will result to file opening in the chosen app.
- Extend swap (optional):
	- `grep SwapTotal /proc/meminfo` - Check the amount of swap available 
	- `sudo swapoff -a` - Turn off all swap processes  
	- `sudo dd if=/dev/zero of=/swapfile bs=1G count=16` - Resize the swap to 16 GB
	- `sudo mkswap /swapfile` - Make the file usable as swap 
	- `sudo swapon /swapfile` - Activate the swap file 
	- `grep SwapTotal /proc/meminfo` - Check the amount of swap available 
	
###### Clean up

- `sudo apt autoremove`
- `sudo apt clean`


###### Some other software to consider:
- https://github.com/aleksas/laba-diena-tts
- https://www.microsoft.com/net/download
- https://microsoft-office.en.softonic.com/
- https://www.microsoft.com/lt-lt/download/details.aspx?id=35400
- https://www.visualstudio.com
- https://ashkulz.github.io/NppFTP/
- https://github.com/TaoK/PoorMansTSqlFormatter
- http://www.pdfforge.org/pdfcreator
- https://www.telerik.com/fiddler
- https://www.sourcetreeapp.com/
- https://www.torproject.org/projects/torbrowser.html.en
- https://www.vidyo.com/
- https://www.wireshark.org/
- http://www.sparxsystems.com/products/ea/
- https://www.arduino.cc/en/Main/Software

###### "magic keys":
- Terminal: Ctrl + C, Ctrl + L, Ctrl + R
- Windows: "Windows" + arrow

## 2021

- Install AWS CLI: https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html#cliv2-linux-install
  - `curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"`
  - `unzip awscliv2.zip`
  - `sudo ./aws/install`
  - `aws --version` -- must be a version listed
  - `which aws` -- must be one line output
- Install AWS ECS CLI: https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ECS_CLI_installation.html
  - `sudo curl -Lo /usr/local/bin/ecs-cli https://amazon-ecs-cli.s3.amazonaws.com/ecs-cli-linux-amd64-latest`
  - `gpg --version` (you must have it already, if not - google on how to install it)
  - `gpg --keyserver hkp://keys.gnupg.net --recv BCE9D9A42D51784F` (try once again if did not work from the 1st attempt)
  - `curl -Lo ecs-cli.asc https://amazon-ecs-cli.s3.amazonaws.com/ecs-cli-linux-amd64-latest.asc`
  - `gpg --verify ecs-cli.asc /usr/local/bin/ecs-cli`
  - `sudo chmod +x /usr/local/bin/ecs-cli`
  - `ecs-cli --version` (must work if installed correctly, e.g. should output `ecs-cli version 1.21.0 (bb0b8f0)` or similar)
- `mandb` - create or update the manual page index caches (relates to `man ...` command)
- Consider "Open Visual Traceroute" - https://visualtraceroute.net/  
- Install Go (https://golang.org/dl/) by following instructions under https://golang.org/doc/install
  - Download the latest `*.tar.gz` archive, it is currently `go1.17.linux-amd64.tar.gz`
  - `sudo rm -rf /usr/local/go && sudo tar -C /usr/local -xzf go1.17.linux-amd64.tar.gz`
  - `sudo nano /etc/profile` and add the following new line at the very end for a system-wide installation: `export PATH=$PATH:/usr/local/go/bin
  - `Ctrl` + `X` (Save), `Y` (Yes, save), `Enter` (Yes yes, save)
  - `source /etc/profile`
  - `go version`
  - Install IDE and related plugins, e.g.:
    - Visual Studio Code (https://code.visualstudio.com/)
    - `File` > `Preferences` > `Extensions` > Find `Go` extension, click `Install`
    - Install other extensions:
      - Do `Ctrl` + `Shift` + `p` and look for the following extensions, install these too:
      - Extensions for Golang:
      - `>GO: install/Update Tools`, sellect it and all "sub-extensions", click "ok", wait to be installed:
        - `gopkgs`
        - `go-outline`
        - `gotests`
        - `gomodifytags`
        - `impl`
        - `goplay`
        - `dlv`
        - `dlv-dap`
        - `staticcheck`
        - `gopls`
      - Restart IDE
      - Extensions for JavaScript:
        - Material Icon Theme
        - Prettier Formatter for Visual Studio Code
        - open in browser by TechER
      - Restart IDE
- Install Anki: https://apps.ankiweb.net/
- Check for external IP: `curl ifconfig.me` ( taken from https://linuxcommandlibrary.com/basics )  

# 2022  

- Install WebStorm: https://www.jetbrains.com/webstorm/   
- Install JavaScript related tools:
  - nvm: https://github.com/nvm-sh/nvm#installing-and-updating  
    - `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash`
  - npm:
    - `sudo apt install npm`
  - NodeJS ( https://nodejs.org/en/download/package-manager/ , https://github.com/nodesource/distributions/blob/master/README.md )
    - `sudo npm install -g n` , - see https://www.npmjs.com/package/n
    - `sudo n lts`, - see https://www.npmjs.com/package/n
  - TypeScript
    - `sudo npm install -g typescript && tsc --version`, - see https://www.typescriptlang.org/download  
  - (optional) other
    - `sudo apt install libssl1.0-dev`
    - `sudo apt install nodejs-dev`
    - `sudo apt install node-gyp`    
  - (optional) `sudo aptitude install npm` - install a package with aptitude  
  - Yarn (https://yarnpkg.com):
    - (Follow: https://yarnpkg.com/en/docs/install#debian-stable )
    - `curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -`
    - `echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list`
    - `sudo apt-get update && sudo apt-get install yarn`
    - `yarn --version`
  - Forge CLI: https://developer.atlassian.com/platform/forge/getting-started/#install-the-forge-cli  
  - `npm i -g nodemon` -- restart the application automatically whenever there is a change in the application
- ngrok https://dashboard.ngrok.com/get-started/setup
- GUI customizations
  - Add bookmarks to the file explorer left side (Ctrl + D), e.g.:
    - `¬/dev`
    - `~/software`
    - `~/.ResponsibleTime`
    - `~/.virtualbox-shared`
    - Another HDD
    - tmp
    - .ssh
    - memes
    - BACKUP
    - ...
- "Settings" > `Displays` > `Night Light` > `On` (Schedule: Sunset to Sunrise)

- WoeUSB (to make bootable Windows ISOs on USB sticks)
  - `sudo add-apt-repository ppa:tomtomtom/woeusb`
  - `sudo apt update && sudo apt install woeusb-frontend-wxgtk`
- Edit sound:
  - ffmpeg (to convert mp3 to wav and alike, e.g. `ffmpeg -i track1.mp3 track1.wav`)
    - `sudo apt install ffmpeg`
  - (optional) mhWaveEdit:
    - `sudo apt-get install mhwaveedit`
    - `sudo apt-get install lame vorbis-tools`
    - `sudo apt-get install libsndfile1`
  - Audacity (probably the most comprehensive one out of all mentioned audio tools in this section)
    - `sudo add-apt-repository ppa:ubuntuhandbook1/audacity`
    - `sudo apt update`
    - (if the above does not work, just download the binary from [https://www.audacityteam.org/download/linux/](https://www.audacityteam.org/download/linux/) and run it in a simple way, e.g. `./audacity-linux-3.1.3-x86_64.AppImage`)
  - snapd ("dependency" for mp3gain)
    - `sudo apt update`
    - `sudo apt install snapd`
  - mp3gain (dependency for MP3 Diags)
    - `sudo snap install mp3gain`
  - MP3 Diags (for mp3 files to fix and normalize)
    - `sudo apt-get update`
    - `sudo apt-get install mp3diags`


