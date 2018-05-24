- `sudo apt-get update`
- `sudo nano /etc/update-manager/release-upgrades`  
and change `prompt=lts` to `prompt=normal` (this will change the awareness level of new releases from LTS to normal)
- `sudo do-release-upgrade`
- `sudo apt-get update`
- (update GeForce drivers? https://askubuntu.com/questions/1030886/how-do-i-install-the-nvidia-cuda-toolkit-on-18-04-with-coffee-lake-is-it-suppo/1030901#1030901 , https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-18-04-bionic-beaver-linux )
	- `sudo apt install nvidia-cuda-toolkit`
	- `nvcc -V`
	- `sudo apt install clinfo`
	- `clinfo`
	- `ubuntu-drivers devices`
	- Look for `driver   : nvidia-driver-390 - distro non-free recommended` or similar line.
	- If driver recommendations are acceptable then run `sudo ubuntu-drivers autoinstall`. Otherwise, run `nvidia-driver-390` (according to the driver name found after `ubuntu-drivers devices`)
- `mkdir -p ~/dev ~/software virtualbox-shared`
- "Settings" > `Region & Language` > Input Sources > `+` > Lithuanian (or other)
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
		- Go to: `about:config`
			- `network.dnsCacheExpiration`: `60`
		- Etc.
- Install Google Chrome:
	- Visit (https://www.google.com/chrome/), download, start instal by double clicking on the downloaded .deb package.
	- Downloads dir
	- Go to: `chrome://about` , `chrome://net-internals/`
- Install Postman:
    - `sudo apt install libgconf2-4` (dependency, applies for Ubuntu 18.04 LTS)
    - `wget https://dl.pstmn.io/download/latest/linux64 -O postman.tar.gz`
    - `sudo tar -xzf postman.tar.gz -C /opt`
    - `rm postman.tar.gz`
    - `sudo ln -s /opt/Postman/Postman /usr/bin/postman`
    -
	```
   cat > ~/.local/share/applications/postman.desktop <<EOL
   [Desktop Entry]
   Encoding=UTF-8
   Name=Postman
   Exec=postman
   Icon=/opt/Postman/resources/app/assets/icon.png
   Terminal=false
   Type=Application
   Categories=Development;
   EOL
	```
- Install KeePassX & load passwords (if have any)
- Generate ssh keys:
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
	- Add following lines to `~/.bachrc`:
		```
		# Custom definitions.
		if [ -f ~/.bash_custom ]; then
		    . ~/.bash_custom
		fi
		```
	- `source ~/.bashrc`
- Configure Ubuntu look and behaviour:
	- // comment // https://askubuntu.com/questions/15520/how-can-i-tell-ubuntu-to-do-nothing-when-i-close-my-laptop-lid
	- `sudo nano /etc/systemd/logind.conf`
  ```
		HandlePowerKey=poweroff
		HandleLidSwitch=ignore
		HandleLidSwitchDocked=ignore
  ```	
  	- "Settings" > `Privacy`:
		- `Screen Lock`: `Off`
	- "Settings Power"
		- Dim screen when inactive: `Off` (cannot find this on Ubuntu 18.04 LTS)
		- Blank screen: `Never`
		- When the Power Button is pressed: `Power Off`
	- 
	- "Language" (?)
  ```
		Input Sources > + > Lithuanian
  ```
	- "Language Support"
  ```
		Language > Install / Remove Languages... > Lithuanian > Install	
		Regional Formats > Dispplay numbers, dates and currency amounts...: Lietuvių > Apply System-Wide > Close
  ```
	- `sudo apt-get install gnome-tweak-tool`
	- "Tweaks"
		- Appearance:
			- Animations: `Off`
		- Desktop:
			- Icons on Desktop: Show Icons: `On`
			- Icons on Desktop: Home: `On`
			- Icons on Desktop: Network Servers: `Off`
			- Icons on Desktop: Trash: `On`
			- Icons on Desktop: Mounted Volumes: `On`
		- Extensions:
			- Ubuntu appindicators: `Off`
			- Ubuntu dock: `On`
		- Power:
			- Suspend when laptop lid is closed: `Off`  
		- Startup Applications:
			- `ignore-lid-switch-tweak` (ignore if does not exist)
		- Top Bar
			- Application Menu: `On`
			- Battery Percentage: `On`
			- Activities Overview Hot Center: `Off`
			- Clock: Date: `On`
			- Clock: Seconds: `On`
			- Calendar: Week Numbers: `On`
		- Windows
			- Attach Modal Dialogs: `On`
			- Resize with Secondary-Click: `On`
			- Window Action Key: `Super`
			- Window Focus: Click to focus: `Checked`
			- Window Focus: Sloppy: `Not Checked`
			- Window Focus: Secondary-Click: `Not Checked`
			- Reise Windows When Focused: On (frozen)
			- Titlebar Actions: Double-Click: `Toggle Maximize`
			- Titlebar Actions: Middle-Click: `None`
			- Titlebar Actions: Secondary-Click: `Menu`
			- Titlebar Buttons: Maximize: `On`
			- Titlebar Buttons: Minimize: `On`
			- Titlebar Buttons: Placement: `Right` (selected is darker)
		> ...
	- "Settings" > Dock
		- Icon size: `30`
	- "Keyboard" > Navigation
		- Hide all normal windows > Change to "SUPER + D"
		- Switch windows > "ALT + TAB" (this will disable "Switch applications" which is ok)
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
	
- Install additional software via Ubuntu software center:
	- `sudo apt install htop`
	- `sudo apt install atop`
	- `sudo apt install tree`
	- `sudo apt install xclip` (for usage like: `cat ~/.ssh/id_rsa.pub | xclip -sel clip`)
	- `sudo apt install net-tools` (for ifconfig to work)
	- `sudo apt-get install traceroute` (for traceroute)
	- `sudo apt-get install curl`
	- "Emacs" (GNU Emacs GUI)
	- "Gimp" (GNU Image Manipulation Program)
	- "MySQL Workbench"
	- "Slack"
	- "Skype"
	- `sudo apt-get install openjdk-8-jre` (SmartGit will need this)
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
	- "NetBeans"
	- "GtkHash"
	- "Telegram" (Official desktop version of Telegram messaging app)
	- "MonoDevelop"
	- "VLC media player" (Read, capture, broadcast your multimedia streams)
	- "VirtualBox" (Run several virtual systems on a single host computer)
	- (PHP)
		- `sudo apt install php`
		- `sudo apt install php-xml`
		- `sudo apt install php-mbstring`
		- `sudo apt-get install php-pear`
		- `pecl help version`
		- `sudo apt install php-mcrypt` (does not exist in Ubuntu 18.04 LTS because of PHP 7.2)
		- `sudo apt install php-dev` (if Ubuntu 18.04 LTS)
		- `sudo apt-get install libcurl4-openssl-dev` (if Ubuntu 18.04 LTS)
		- `sudo pecl channel-update pecl.php.net`
		- `sudo pecl install mcrypt-1.0.1` (get the latest version number: https://pecl.php.net/package/mcrypt) (if Ubuntu 18.04 LTS)
	- (Graphviz - Graph Visualization Software (http://www.graphviz.org/))
		- `sudo apt install graphviz`
	- (phUML (https://github.com/jakobwesthoff/phuml), requires Graphviz)
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
	- "Wireshark" ( https://www.wireshark.org/ )
	- "notepadqq"
	- (HipChat for Ubuntu 17.10, follow: https://www.hipchat.com/downloads)
		- `sudo sh -c 'echo "deb https://atlassian.artifactoryonline.com/atlassian/hipchat-apt-client $(lsb_release -c -s) main" > /etc/apt/sources.list.d/atlassian-hipchat4.list'`
		- `wget -O - https://atlassian.artifactoryonline.com/atlassian/api/gpg/key/public | sudo apt-key add -`
		- `sudo apt-get update`
		- `sudo apt-get install hipchat4`
	- (HipChat for Ubuntu 18.04 LTS, follow: https://www.hipchat.com/downloads)
		- `sudo sh -c 'echo "deb https://atlassian.artifactoryonline.com/atlassian/hipchat-apt-client xenial main" > /etc/apt/sources.list.d/atlassian-hipchat4.list'`
		- `wget -O - https://atlassian.artifactoryonline.com/atlassian/api/gpg/key/public | sudo apt-key add -`
		- `sudo apt-get update`
		- `sudo apt-get install hipchat4`
		- `sudo rm /opt/HipChat4/lib/libcrypto.so*` (see https://jira.atlassian.com/browse/HCPUB-6249 )
		- `sudo ln -s /usr/lib/x86_64-linux-gnu/libcrypto.so.1.0.0 /opt/HipChat4/lib/libcrypto.so.1.0.0` (see https://jira.atlassian.com/browse/HCPUB-6249 )
		- `sudo ln -s /usr/lib/x86_64-linux-gnu/libssl.so.1.0.0 /opt/HipChat4/lib/libssl.so.1.0.0` (see https://jira.atlassian.com/browse/HCPUB-6249 )
		- `sudo ln -s /usr/lib/x86_64-linux-gnu/libssl.so.1.0.0 /opt/HipChat4/lib/libssl.so` (see https://jira.atlassian.com/browse/HCPUB-6249 )
	- (ignore)(Toggl Desktop tracker)
		- (ignore)`wget http://fr.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/libgstreamer-plugins-base0.10-0_0.10.36-1_amd64.deb`
		- (ignore)`wget http://fr.archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10/libgstreamer0.10-0_0.10.36-1.5ubuntu1_amd64.deb`
		- (ignore)`sudo dpkg -i libgstreamer*.deb`
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
	- Yarn (https://yarnpkg.com):
		- (Follow: https://yarnpkg.com/en/docs/install#debian-stable )
		- `curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -`
		- `echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list`
		- `sudo apt-get update && sudo apt-get install yarn`
		- `yarn --version`
	- SmartGit: 
		- `mkdir ~/software/smartgit`
		- Download from `https://www.syntevo.com/smartgit/download/`
		- Extract the content to `~/software/smartgit`
		- (Follow `~/software/smartgit/readme-linux.txt`)
		- `~/software/smartgit/bin/smartgit.sh`
		- `~/software/smartgit/bin/add-menuitem.sh`
		- `update-java-alternatives --list`
	- PHPStorm:
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
	- ArgoUML:
		- `mkdir ~/software/argouml`
		- Download from `http://argouml.tigris.org/`
		- Extract the content to `~/software/argouml`
		- (Follow `~/software/argouml/README.txt`)
		- `java -jar ~/software/argouml/argouml.jar` will run the app
	- youtube-dl (media downloader):
		- `sudo curl -L https://yt-dl.org/downloads/latest/youtube-dl -o /usr/local/bin/youtube-dl`
		- `sudo chmod a+rx /usr/local/bin/youtube-dl`
		- Test it: `youtube-dl https://www.youtube.com/watch?v=FM7MFYoylVs`
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
	
- `mkdir ~/dev` (this will be for all dev projects like websites, phone apps, etc. to store)
- If still cannot find applications by just typing then create `*.desktop` files in `/usr/share/applications` by using the `*.desktop` template we made before. This is for invoking the program (e.g. wine-compatible) via quick launch.
- "Online Accounts" - add online accounts
- `Tweaks` > `Startup Applications` and pick applications to startup on boot

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
