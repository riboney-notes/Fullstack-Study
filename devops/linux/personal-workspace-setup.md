# Fedora Setup

*Instructions/ info on how to set up Fedora for noobs*

## Setup instructons

**Update system then reboot**

* `dnf upgrade` - upgrade all system packages
  * *Note: this can be done with GNOME Software center, but apparently using DNF is betters

**Enable RPMfusion repositories**

* `sudo dnf install <link-to-repo>`, repo link can be found here [rpmfusion](https://rpmfusion.org/Configuration)
* Run `sudo dnf upgrade` to refresh repositories
* You can see your software repositories in GNOME software center under "software repositories" or `sudo dnf repolist`

**Enable flatpak**

* Flatpak is a good way to install software like Discord that can't be installed from default repositories
  * Not recommended for installing apps like IDEs that may require root access, since flatpak apps run in sandbox environment
* Enable flatpak:`flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo`
* Install flatpak apps from [browser](https://flathub.org/home) or GNOME software center
* Recommended apps: 
  * Discord
  * Hydrapaper

## Development setup

**SSH Keys**

1. Create key pair: `ssh-keygen`
2. Press enter for the default key file location or enter your own
3. Whenever you need to add SSH keys, copy contents of `id_rsa.pub`
   3a. Manual way to copy: `cat <path-to-file>/id_rsa.pub` then copy output with mouse

**Git**

1. Set git username & email
```bash
git config --global user.name "Your Name"
# get private email from github 'Settings > Emails'
git config --global user.email "you@your-domain.com"
```
  1a. verify your changes with `git config --list`
2. Copy & paste SSH pub key to github 'Settings > ssh and gpg keys' 
3. Customize .bashrc for customized git-prompt display
  3a. Clone [repo](https://github.com/magicmonty/bash-git-prompt) into `~/.bash-git-prompt`
  3b. Copy & paste into `~/.bashrc`
  ```bash
  if [ -f "$HOME/.bash-git-prompt/gitprompt.sh" ]; then
    GIT_PROMPT_ONLY_IN_REPO=1
    source $HOME/.bash-git-prompt/gitprompt.sh
  fi
  ```
* Note: Need to run `eval` if getting "Permission denied" error...need to look into this more

**VSCode**

1. Install the RPM repo for VSCode (instructions can be found in [website](https://code.visualstudio.com/docs/setup/linux))
  1a. `sudo dnf check-update` & `sudo dnf install code`
2. Extensions to install:
  * Bracket Pair Colorizer 2 - Allows matching brackets to be identified with colors
  * ESLint - Integrates ESLint into VS Code
  * Java Extension Pack

**Postgres**

* Install the repo
* Install fedora server/client packages
* Init database 
* Enable systemctl service
* Setup admin user password

**Docker**



**WebDev**
*npm*
  * Install: `sudo dnf install npm` (note, this installs nodejs as well)
  * Prevent permission errors (and consequently, avoid use of sudo)
    * Create directory for global installations in home: `mkdir ~/.npm-global`
    * Configure `npm` to use new directory path: `npm config set prefix '~/.npm-global'`
    * Add global npm installations directory to `PATH` in `~/.bashrc`: `export PATH=$HOME/.npm-global/bin:$PATH` 
    * update variables: `source .bashrc`
* Global packages:
  * typescript: `npm install -g typescript`
  * angular: `npm install -g @angular/cli`

**Java**
* Set Java
  1. Find java package name: `sudo dnf search openjdk-devel` (devel = JDK not JRE)
    1a. For JDK11, this the package name you want: `java-11-openjdk-devel.x86_64`
  2. Install package: `sudo dnf install <java-package-name-here>`
  3. Verify installation with `java --version` & `javac --version` (you should see some message)
  4. See all installed JDKs and pick default with: `sudo alternatives --config java`

* Set `JAVA_HOME` and `PATH` variables (global)
  1. Find location of your java installation
    1a. `whereis java` is one option, but it did not provide correct location for me
    1b. Try looking in `/usr/lib/jvm`; thats where I found my java installations
  2. Create `java.sh` in `/etc/profile.d`
  3. Add this line to `java.sh`: `export JAVA_HOME=/usr/lib/jvm/<name-of-java-installation-folder>`
  4. Add this line to `java.sh`: `PATH=$JAVA_HOME/bin:$PATH`
  5. Source file: `source java.sh`
  6. Close terminal, and open terminal
  7. Test if worked by doing `echo $JAVA_HOME` & `echo $PATH`
  * NOTE: If you java folder is upgraded, then it breaks the paths---fix later...

* Setup Maven
  1. Ensure Java is installed and `JAVA_HOME` is set
  2. Download Maven into `/tmp`
    2a. Ex: `wget https://apache.osuosl.org/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz -P /tmp`
    2b. CD into directory of zip file and verify file integrity with checksum; ex: 
   ```bash
       echo "cb77181c0  apache-maven-3.6.3-bin.tar.gz" | sha512sum -c -
       apache-maven-3.6.3-bin.tar.gz: OK
   ```
  3. Extract file and move to `/opt/maven`
    3a. Ex: `sudo tar xzvf apache-maven-3.6.3-bin.tar.gz -C /opt` then `cd /opt`
  4. Create symbolic link to `/opt/maven` (good for dealing with maven updates; just have everything refer to `/opt/maven` and have it point to the latest maven installation)
    4a. `sudo ln -s <path-to-maven-installation> /opt/maven`
    4b. In the future, just change the symlink to point to the latest maven installation when updating
  5. Setup `M2_HOME` environment variable & add this to `PATH` variable
    5a. `sudo vi /etc/profile.d/maven.sh` & add:
       ```bash
       export M2_HOME=/opt/maven
       export PATH=${M2_HOME}/bin:${PATH}
       ```
  6. Load environment variables: `source /etc/profile.d/maven.sh`
  7. Verify installation: `mvn --version`

* Setup Tomcat
  * Install Tomcat
    * download tomcat
      * Ex: `wget -P /tmp https://ftp.wayne.edu/apache/tomcat/tomcat-9/v9.0.41/bin/apache-tomcat-9.0.41.tar.gz`
    * CD into directory of zip file
    * Verify file integrity: `echo "<insert-checksum-here" | sha512sum -c -`
    * Extract tarfile into `/opt`: `sudo tar -xzvf <tomcat-zip-folder> /opt`
    * Create symlink with `/opt/tomcat`: `ln -s /opt/<name-of-tomcat-folder-here> /opt/tomcat`
    * Create symlink with `/var/log/tomcat`
      * We do this because its good practice to put all logs in one place (not sure about this)
      * `mkdir /var/log/tomcat`
      * `rmdir /opt/tomcat/logs`
      * `ls -s /var/log/tomcat /opt/tomcat/logs`
  * Setup Tomcat User & perms
    * because its a bad idea to run Tomcat under root account
    * Create no-login tomcat account with /opt/tomcat as home and group named tomcat
      * `useradd -s /sbin/nologin -r -U -d <path-to-tomcat-installation> tomcat`
    * Configure ownership and perms: 
      * set `tomcat` as owner of tomcat directory: `chown -RH tomcat:tomcat <path-to-tomcat-installation>`
      * set `tomcat` as owner of tomcat log directory: `chown -RH tomcat:tomcat /var/log/tomcat`
      * give execute rights to scripts located in the `bin` directory: `sudo chmod +x /opt/tomcat/bin/`
      * Users should not modify configuration of tomcat: `sudo chmod -R g+r /opt/tomcat/conf`
      * folders users can modify:
        * `chmod -R g+w /opt/tomcat/logs`
        * `chmod -R g+w /opt/tomcat/temp`
        * `chmod -R g+w /opt/tomcat/webapps`
        * `chmod -R g+w /opt/tomcat/work`
      * Sticky-bit to keep permissions defined:
        * `chmod -R g+s /opt/tomcat/conf`
        * `chmod -R g+s /opt/tomcat/logs`
        * `chmod -R g+s /opt/tomcat/temp`
        * `chmod -R g+s /opt/tomcat/webapps`
        * `chmod -R g+s /opt/tomcat/work`
      * *NOTE*: you can do all of this in one command using this format: `/opt/tomcat/{file1,file2,etc}`
      * Add your user to tomcat group: `usermod -a -G tomcat <your-user-here>`
  * Configure Tomcat service
    * Change tomcat default port
      * open `/opt/tomcat/conf/server.xml`
      * Edit the `<connector port="...">` values: `<Connector port="8070" protocol="HTTP/1.1" connectionTimeout="20000" redirectPort="8071" />`
    * create systemd unit file to run Tomcat as a service: `sudo gedit /etc/systemd/system/tomcat.service`
    ```bash
	[Unit]
	Description=Apache Tomcat Web Application Container
	After=syslog.target network.target

	[Service]
	Type=forking

	# Path to java installation
	Environment=JAVA_HOME=/usr/lib/jvm/java-11-openjdk-11.0.9.11-9.fc33.x86_64
	# Specifies location of file where PID of forked tomcat process will be written
	#     provides better protection against duplicate start attempts and allows forceful termination of tomcat
	Environment=CATALINA_PID=/opt/tomcat/temp/tomcat.pid
	# Root directory of tomcat
	Environment=CATALINA_HOME=/opt/tomcat
	# For multiple instances of tomcat; not configured here (atm is the same as CATALINA_HOME)
	Environment=CATALINA_BASE=/opt/tomcat
	# Sets server runtime options
	Environment='CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC'
	Environment='JAVA_OPTS=-Djava.awt.headless=true -Djava.security.egd=file:/dev/./urandom'

	ExecStart=/opt/tomcat/bin/startup.sh
	ExecStop=/opt/tomcat/bin/shutdown.sh

	User=tomcat
	Group=tomcat

	[Install]
	WantedBy=multi-user.target
    ```
    * Reload systemd: `sudo systemctl daemon-reload`
    * Start tomcat: `sudo systemctl start tomcat`
    * View tomcat status: `sudo systemctl status tomcat`


## Quality of Life instructions

* Starting up v4l2loopback for obs studios:
 `sudo modprobe v4l2loopback devices=1 video_nr=10 card_label="OBS Cam" exclusive_caps=1`
* Installation instructions for setting up virtual cam for OBS on fedora: sudo modprobe v4l2loopback devices=1 video_nr=10 card_label="OBS Cam" exclusive_caps=1


* Install youtube-dl
  * `sudo pip install youtube-dl`
  * Install `ffprobe/avprobe` & `ffmpeg/avconv`
    * `sudo dnf install ffmpeg` (requires rpmfusion repos)
  * Create config file: `~/.config/youtube-dl/config`
    * Config options for mp3 downloads from youtube
    ```bash
      # File Location for downloads (make sure directory exists)
      -o "~/Music/Youtube/%(title)s.%(ext)s"

      # Always extract audio
      -x

      # audio format mp3
      --audio-format mp3

      # best quality
      --audio-quality 0
    ```
  * Example of extracting youtube video audio and downloading to music/youtube folder: `youtube-dl -x --audio-format mp3 --audio-quality 0 -o "~/Music/Youtube/%(title)s.%(ext)s" https://www.youtube.com/watch?v=dlRpLV6iqNg`

* Install Hydrapaper through flathub for dual-monitor wallpaper setup

* Install GNOME Shell extensions through GNOME extensions webpage
  * Dash to Panel
    * Windows 10-like desktop tool bar
  * ArcMenu
    * Windows like menu system for apps
  * Screenshot tool
    * not as good as Microsofts snipping tool
  * Sound Input & Output Device chooser
    * Saves the hassle of going into sound settings to change input/ output devices
  * User themes
    * Allows you to load themes from user directory
  * Tray Icons
    * allows for displaying icons of apps running in the background in system tray


* Tweak your GNOME UI with GNOME Tweaks
  * install : `sudo dnf install gnome-tweaks`
  * Window Titlebars: set titlebar buttons `maximize`  & `minimize` on
  * Top Bar: set weekday and week numbers on
  * Custom themes
    1. `mkdir `~/.themes`
    2. Install gnome-extension: `User themes`
    3. Download themes from gnome-look.com and follow instructions (most likely, place in `~/.themes` folder)
      3a. I like [nordic](https://www.gnome-look.org/p/1267246/) theme
    4. Choose theme in gnome tweaks > appearance
    

* Install multimedia codecs through Software center "add-ons"
  * Enable 3rd party repos (RPMfusion repos) first

* Change hostname
  * `sudo hostnamectl set-hostname <your-new-hostname>`
    * Can also do this by changing device name in GNOME settings

* Change terminal bash prompt
  * Involves changing the PS1 variable in `.bashrc` file
  * By default, it looks like this: `[username@hostname ~]$`
  1. Create backup copy of `~/.bashrc`: `cp ~/.bashrc ~/.bashrc.bak`
  2. Open `~/.bashrc` file for editing: `sudo nano ~/.bashrc`
  3. Add the following line `PS1=<your-new-bash-prompt>` at the bottom of the configuration file
    3a. Prompt name that displays username, current directory, time, and user type: 
      * `PS1="\u \w [\A]\$: "`
      * `PS1="(\u \A) '\w'\$: "`
    3b. See more options at [bashrcgenerator](http://bashrcgenerator.com/)
  4. Refresh BASH and apply your changes: `source ~/.bashrc`
 
* GNOME settings
  * Disable GNOME search & tracking feature to improve performance
    * Settings > Search > *Disable what you wish*
  
  * default keyboard shortcuts:
    * `alt + f2` - run commands (ex: launch apps, execute scripts, etc)
    * `shift + super + left/ right arrow`: moves the active program to the left or right monitor
    * switching to active window/app:
      * `alt + tab`
      * `alt + esc` - like `alt+tab` but way quicker (no GUI overlay to pick window; good when you have small number of apps open)
      * `alt + \``  - switches windows within applications (ex: switching between several running, separate terminal windows)

  * custom keyboard-shortcuts
    1. Settings > Keyboard Shortcuts
    2. Scroll to bottom, and press the `+` button
    3. Enter name, command (listing the name of the app is enough to launch it), and keyboard shortcut to invoke the command
    * My custom shortcuts
      * Terminal - gnome-terminal - ctrl+alt+t
      * Launchers - Home folder - ctrl+alt+h



## Terminologies / Concepts

### Software & Apps

**Source code/ `.TAR.GZ` / `.BZ2`**

* Overview of process for installing software from source code:
  * Find out software's dependencies and requirements
  * Find out location of binaries
  * Find out the configure script or makefile
  * Compile the software & handle installation of dependencies
  * For now, refer to this: [itsfoss article](https://itsfoss.com/install-software-from-source-code/)

* Packages & Package managers handle the process of installing applications from source code for you
  * Manual installation of source code is needed for a variety of reasons
 
**Package**

* Archive file that contains:
  * Binary executable
  * Configuration file
  * Metadata

* Packages are used to create ready-to-use software for users, getting rid of the complexity from compiling & configuring source code manually

* Packages are created and maintained by *package maintainers* who do the following:
  * Obtain source code from upstream provider (app developer)
  * Compile everything
  * Create pacakage metadata, installation scripts, etc

* Some packaging formats:
  * `.deb`
    * Used by debian based distributions like Ubuntu
  * `.rpm`
    * Used by Red Hat distributions like Fedora
  * TAR
    * Used by any distribution


**Package managers & dependency resolvers**

* Package management system features
  * Package downloading
    * Distros provide package repositories that package management systems use to download packages from
  * Dependency resolution
    * Packages contain metadata that contain details for package depenendencies and requirements
    * Dependency resolution will resolve the dependency requirements and handle all updates to packages and their dependencies
  * Enforces standard for installation/ configuration location
    * Packages installed by package mgmt systems will be found in the standard file locaitons

* apt & dpkg
  * apt is dependency resolver for dpkg the package manager for Debian based systems

* dnf & rpm
  * dnf is dependency resolver for RPM the package manager for Red Hat based distros

**Package Repositories**

* Package repos are storage locations hosted on remote servers from which your system retrieves and installs OS updates and apps
* Distros come with standard package repos by default
  * Sometimes, you may need to enable 3rd party repos to be able to install non-open/ non-free apps not provided by the default repos

### Desktop Environments / User interface

**GNOME**
  * is a desktop environment (?)
  * GNOME Shell
    * Refers to the general user interface features
      * Top bar
      * Activities overview
      * System menu
      * Message Tray
  * GNOME Shell extension
    * These are "add-ons" you can install through the [browser](https://extensions.gnome.org/) to modify how your desktop looks and behaves and/or add apps and functionalities
      * Need to install browser extension to configure the GNOME extensions; see gnome extensions webpage for instructions
      * Can also install and use `gnome-tweaks` to install and configure extensions through this app

### Environment Variables/ Paths
* To see your system's environment variables, do `env` command
* Enviroment variables are set and exported from `/etc/profile` and `/etc/bashrc` files


* `PATH` is an environment variable that contains an ordered list of paths that the OS will search for executables when running a command
  * without `PATH`, you would have to specify the file location of the executables you run in with that executable's command
* Different ways to set the PATH variable
  * Locally
    * appened new path by `export PATH=$PATH:<new-path-here>` in `~/.profile`
      * Note, you can do this in `~/.bash_profile` as well; however, changes to `.bash_profile` only apply to the bash shell, and not other shells (like zsh)
  * Globally
    * can be done by adding new path to `/etc/environment` file but this is not recommended
    * Recommended way: create a script file in `/etc/profile.d` and add `export PATH` line there
      * Ex: in `/etc/profile.d/<script-name-here>.sh`, add `export PATH=$PATH:<new-path-here>`

### Filesystem

File types
* *shareable*
  * files that can be stored on one host and used on others (shareable)
* *unshareable* 
  * system specific files that shouldn't be shared (ex: `device-lock` files)
* *static*
  * Files that don't change w/o admin access (ex: binaries, libraries, documentation, etc)
* *variable*
  * files that change often that therefore shouldn't be just "read-only"

* Example layout of files
  * shareable static files stored in `/usr` and `/opt`
  * unshareable static files stored in /etc` and `/boot`
  * shareable variable files stored in `/var/mail` and `/var/spool/news`
  * unshareable variable files stored in `/var/run` and `/var/lock`

Root filesystem
* Contents of root filesystem should be adequete to boot, restore, recover, and/or repair the system
  * As such, root file system requires certain things to be present
  * Contains things like system-specific config files
  * Should be kept small
* Required directories
  * `bin` - Essential command binaries
  * `boot` - static files of boot loader
  * `dev` - device files
  * `etc` - host-specific system configs
  * `lib` - essential shared libaries and kernel modules
  * `media` - mount point for removable media
  * `mnt` -  mount point for mounting a filesystem temporarily
  * `opt` - add-on application software packages
  * `sbin` - essential system binaries
  * `srv` - data for services provided by this system
  * `tmp` - temporary files
  * `usr` - secondary hierarchy
  * `var` - variable data
* Optional Directories
  * `home` - user home directories
  * `lib<qual>` - alternate format essential shared libaries
  * `root` - home directory for the root user

`/bin`
* Contains core OS commands such as `cat` and `ls`

`/boot`
* Contains mostly everything required for the boot process 

`dev`
* location for special device files (disks, drives, printers, etc)

`/etc`
* contains subdirectories for storing config files
* `/etc/opt`
  * contains configs for add-on app packages in `/opt`

`/home`
* Contains user specific directories & files
  * contains user specific config files for apps

`/lib`
* contains shared libary images needed to boot the system and run commands in `/bin`

`/media`
* contains subdirectories which are mount points for removeable media such as flopy disks, cdroms, and etc

`/mnt`
* location for temporary mount points

`/tmp`
* location for temporary files
* good place for downloading tar files that need to be extracted and moved 

`/opt`
*  app & programs
* 3rd party/ external apps are here

`/usr`
* directory for local software installation that should be safe from system updates
* anything managed by the user is here, like JDK, maven, etc
* Directories
  * `/bin` -  user commands
  * `/lib` - libraries for apps and programming dev stuff
  * `/local` - shareable data and stuff for all users
     * contains things like config (/etc), games (/games), etc
  * `/src`

`/var`
  * contains variable data files like logs, temp files, etc
  * `/local` variable data for `/usr/local`
  * `/opt` variable data for `/opt`
  * `/cache` cached data from apps

### Linux Permissions

Numeric values for permissions
* r (read) = 4
* w (write) = 2
* x (execute) = 1
* no permissions = 0
* Examples:
  * Owner: rwx=4+2+1=7
  * Group: r-x=4+0+1=5
  * Others: r-x=4+0+0=4
 
### systemd

 


### Misc

Checksum
* long string of data that is used to check/ verify integrity of files
  * Used to check if downloaded file is corrupted
* General process
  * Download file
  * On Download page, note the provided checksum value and algorithm
  * Perform the checksum command for the algorithm on the file and compare the results with the checksum provided on the website
    * If different, then downloaded file is corrupted
    * If same, then downloaded file has no corruption
    * Ex: `sha1sum test.txt` *outputs:* `086a17ae6ed9b4182f50899a3910666fff7738de  test.txt` 
      * compare this long string (omit the file name) with the checksum on download page
  * Another way to compare checksums:
    * `echo '<paste-checksum-here>  <paste-file-name-here>' | <use-algo here> -c -`
      * Ex: `echo "086a17ae6ed9b4182f50899a3910666fff7738de  test.txt" | sha1sum -c -`
      * NOTE: Must put *two* spaces after checksum value in echo statement
  * Another way to compare checksums:
    * Download checksum file from download page
    * Make sure contents are in format `<checksum-value>  <filename-of-file-to-check>`
    * Make sure checksum file and unverified file to be checked is are in the same directory
    * using the appropiate command for the algorithm, do: `<checksum-command> -c <checksum-file-name>`
      * Ex: `sha1sum -c test.txt.SHA1SUM`
      * NOTE: for apache's checksum, they don't formatted in the correct checksum format...if this is the case, just append double space + filename

Tomcat
  * is a servlet and JSP container that is used for hosting Java servlets and web apps
  * Key tomcat directories, files, and env variables:
    * `/bin` - startup, shutdown, and other scripts (`.sh` and `.bat` files)
    * `/conf` - config files
      * contains `server.xml` which is the main config file for the container
    * `/logs` - log files
    * `/webapps` the directory in which `Tomcat` looks for webapps to run
      * So to run your webapp on tomcat, place the `.war` file here
    * `CATALINA_HOME` - represents the root of Tomcat installation
    * `CATALINA_BASE` - represents the root of a runtime config of a specific Tomcat instance
      * Use this when running multiple tomcat instances

Terminal, console, shell, command line, shell, tty, etc
  * TTY
    * Back then, teleprinter devices (tty) were used to interact with Unix
    * in Unix, `tty` refers to the command that prints the file name of the terminal connected to stdin
      * used to detect if output is a *terminal*; if no file is detected, then `not a tty` is printed which means that the output is being run as part of a script or being piped (?)
  * Terminal
    * same as tty (?)
    * this is the GUI that user sees
  * Consoles are terminals but are the ones that are connected to the OS or physical hardware (?)
  * Shell is the software that inteprets and executes commands
  * Command line interface (CLI) user interface for commands and seeing the results of those commands

Interactive, non-interactive, login, non-login
  * Interactive
    * commands are run with user-interaction from keyboard
    * Shell can prompt user for input
    * Ex: your basic terminal when you open it
  * Non-interactive
    * shell that is run from an automated process
    * can't assume user input or that user will see output (output would be seen from the saved log files if any)
  * login
    * shell that is run as part of user login to system
    * Ex: when logging into a virtual private server, the shell is "login shell" because that launches the Users system and is tied to the system
  * non-login
    * shells that are run after the user logs in and not tied to a logged in user
    * Ex: terminal after logging into the fedora

Create user with description and expiry date
  * Ex: `sudo user add -c <"Insert short description here"> -e <YYYY-MM-DD> <username>` then `sudo passwd test_user` (password: `taskhavefun`)
  * switch to user: `su - test_user` (`-` creates a new environment when logging in, whereas omitting it lets you inherit the enviromnet from previous account)

Create immutable folder (can user directory, but not move or delete it)
  * just remove write permissions from parent of directory

Clipboard
*need to do this...*

## Resources used

* https://thecodersblog.com/linux-package-managment/ (not very good, imo)
* https://itsfoss.com/package-manager/
* https://www.makeuseof.com/tag/install-software-linux-package-formats-explained/
* https://www.linode.com/docs/guides/linux-package-management/
* https://phoenixnap.com/kb/change-bash-prompt-linux
* https://medium.com/ag-grid/git-on-the-command-line-improving-the-experience-5a604cb14cf6
* https://refspecs.linuxfoundation.org/FHS_3.0/fhs-3.0.pdf
* https://www.baeldung.com/linux/path-variable
* https://itsfoss.com/checksum-tools-guide-linux/
* https://askubuntu.com/questions/442960/how-to-automate-comparison-of-md5sum-hash-values-for-a-large-number-of-files/442968#442968
* https://tecadmin.net/install-apache-maven-on-fedora/
* https://linuxize.com/post/how-to-install-apache-maven-on-centos-7/
* http://tomcat.apache.org/tomcat-9.0-doc/RUNNING.txt
* https://askubuntu.com/questions/506510/what-is-the-difference-between-terminal-console-shell-and-command-line#:~:text=Shell%20is%20a%20program%20which,software%20%2C%20like%20Gnome%2DTerminal%20
* https://unix.stackexchange.com/questions/50665/what-is-the-difference-between-interactive-shells-login-shells-non-login-shell#:~:text=Interactive%3A%20As%20the%20term%20implies,someone%20will%20see%20the%20output
* https://linux-audit.com/
* https://www.redhat.com/sysadmin/gnome-keyboard-shortcuts
* https://itsfoss.com/install-switch-themes-gnome-shell/
* https://github.com/magicmonty/bash-git-prompt
* https://linuxconfig.org/how-to-install-apache-tomcat-on-linux-redhat-8
* tomcat perms: https://superuser.com/a/834270
* https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally
