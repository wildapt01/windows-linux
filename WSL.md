## Complete Development environment with Windows 10 and Linux - Part 2

This guide is for installing Linux Ubuntu 18.04 LTS in the Windows 10 environment on a PC, using Windows Subsystem for Linux.
The base of this project came from a personal lack of comfort with the dominant coding machine, the one sporting a bitten common fruit. I personally don’t own any interest, share or sponsorship from any of the corporations mentioned in this article. This article is the second of two intending to install a viable, useful and professional development environment on a PC desktop or laptop. The first one can be found HERE. Some of the following info will refer to it, and avoid duplication.

The main components are:

- Ubuntu 18.04LTS
- Chrome
- Git
- Visual Studio Code
  - EsLint
  - Prettier
- Node JS
  - NVM, NPM
  - Nodemon, Testem
- PostgreSQL
- DBeaver
- Postman

### IMPORTANT DISCLAIMER

> **Please note that some of the modifications could potentially brick your machine or necessitate a new install of Windows if done without precautions. Proceed at your own risk. The information in this post is true and complete to the best of my knowledge. All recommendations are made without any guarantee, implied or express, on the part of the author. The author disclaim any liability in connection with the use of this information.**

### OTHER IMPORTANT FACT

> **Some of the tools are implemented through the WSL/Ubuntu console, also known as Bash. DO NOT TRY TO IMPLEMENT LINUX/UBUNTU TOOLS THROUGH OTHER MEANS. Really, really bad things will happen. In short, before ANY installation or call to a ressource, like installing a Node package or dependency, CHECK THOROUGHLY this happens in Bash, not in CMD prompt terminal, not in the Powershell terminal, or anywhere else. Each time, the installation environment is detailed. Respect this.**

### Why Ubuntu? Why Windows? Why?...

Linux is more or less just the OS Kernel. Different orgs or companies use this kernel to put together a full OS. Microsoft has collabored with Canonical, owner of Ubuntu, to get that particular OS to function on Windows. The first article can be accessed for a bit more background on that. It is an on-going venture and more exciting stuff will come in the near future.

Now a bit more about that choice as a personal Dev' box. As said previously, Macs are fine machines. I have the chance to own a Surface Book 2 and I prefer working on it for its comfort, its OS and its touch functions. It brings another dimension to delopment work, absent from the Apple eco-system so far. For instance, it can take an instant screenshot and use it as a background for writing on it. This is just awesome, basically offering our own whiteboard to scribble on with the base code or definition visible at the same time. It offers a large tablet where I can examine or handle a database, or jost a few notes for later work on my app. It makes mock-ups very easy to figure out. It is as well a great tool for presentations or code reviews. Those points are just a few among many others and one can see it differently. Tastes and colors...

### Windows Sub-System for Linux

Links:
MSFT Dev Blog

In short: WSL.
It allows the installation and use of Ubuntu (18.04 in this case) within Win10. It is a Console App, not a virtual machine, not the Console per se. It can be represented like this:

// image console MSFT

It makes it possible to run and operate a complete Dev' box, using Visual Studio Code, NodeJS and Github Desktop, ESlint (not global) and Testem (not global either), while keeping access to Win10 ressources. It may encounter some difficulties running global packages. PostgreSQL can run in the WSL “bubble” with some constraints.
It is a nice environnement, and it is rather easy to set up. Main caveat is it is somewhat slower than a native Linux environment. Some global installations will not work (as of the time of writing), though a lot of libraries and resources are best installed and used on a per-project basis.

Another consideration to be made is that WSL is still happening. It is not complete, it has still some flaws and bugs. It works for 95% of Dev' needs and should see a lot more coming in the near future.

### Windows requirements

To operate Windows Sub-system for Linux, the machine must run a Windows 10 version different from the Home version, so no 32-bit Windows. A latest build is also better. It is advised to run Fall Creator or later (Build 16215 and above).

### First steps

Before any action, prepare a Windows 10 system image with the 32GB USB drive.
Backup your files and documents, so you have them in case something goes wrong. Use some DVDs or other USB drives.

What you need:

1 USB drive 32GB,

DVDs or some more USB drives.

### Initializing WSL

Links:
Microsoft WSL Documentation
Initializing WSL
WSL installation tutorial

First, enable the Developer mode in the settings:
Settings => Update and Security => For Developers => Click Developer mode ON.

Second, enable WSL through a Powershell command (official MSFT Docs)

```js
```

or through Windows features (2nd tutorial).

After a restart, install the chosen version of Ubuntu, preferably the latest LTS. MSFT Store provides different versions for free, as well as different distributions. Other distros may require different options and / or utility software. Some may not support all the features required by this environment. Just select and click `install`.

Restart again the computer.

Pin the Ubuntu client to the Start menu. Other quick links will get there in time, it is a handy place to gather all the Dev tiles (see screenshot).

### Bionic Beaver is alive!

At that point, you are pretty much done. Congratulations!
Ubuntu (or the chosen distro) is active in the Windows eco-system.

One thing needs to be very clear. This is Ubuntu, this is Linux (actually the Linux binaries), BUT this is not a Linux kernel. It cannot be updated as seen in a dual boot config. The distro can be updated at this time through installing a new version of it.

If using a Surface device, no need to install a custom kernel, all the touch stuff and peripherics are working at peek efficiency. Important to say is that all this is still Win10, with Win10 drivers and processes, and so on.
Now comes the Dev environment set-up. This is in part the beauty of it, as a lot of tools implemented in Win10 can interact with Ubuntu via WSL and ports. This is illustrated in the next sections, as we take shamelessly advantage of it (cue in evil chuckles!)

### WSL Linux for Fullstack Academy

There are some differences between the Toolbox from FSA and the implementation with WSL.

**One important note**: some software need to be installed in Windows, some in the Ubuntu console. DO NOT TRY to install Linux stuff through the PowerShell or Command Prompt terminal. Some really nasty effects will happen, with the potential of breaking down Win10. It bears being repeated.
Links:

- [Git](https://www.digitalocean.com/community/tutorials/how-to-install-git-on-ubuntu-18-04-quickstart)
- [Curl](https://linuxhint.com/install-curl-on-ubuntu-18-04/)
- [NVM](https://github.com/creationix/nvm)
- [NodeJS](https://linuxconfig.org/how-to-install-node-js-on-ubuntu-18-04-bionic-beaver-linux)

Git (version manager, hosted on GitHub) should be the first item on the list. And it is best installed on both sides, meaning in Win10 (), AND in Ubuntu.
Open the brand new Ubuntu terminal and type:

```js
User@Linux~$ sudo apt update
User@Linux~$ sudo apt upgrade
User@pc~$ sudo apt-get install git
```

After that download and install Git, this will allow Git to run on both sides.

From experience, it is best to start with NVM and NodeJS, as presented in the first post. The sam econsiderations apply.

**Important** : Git, Curl, NVM and NodeJS are installed IN the Ubuntu terminal

### Text Editor and linter
Links:

- [Visual Studio Code](https://code.visualstudio.com/download)
- [VSC install](https://code.visualstudio.com/docs/setup/linux#_installation)
- [Github Desktop](https://desktop.github.com/)
  **This is done on the Win10 side, not in the WSL-Ubuntu client.**

Get to the download with the link, fetch the 64-bit version and install. Pin that tile to the Start Menu.In the same way, install GitHub Desktop. It may not be necessary, but it is quite helpful when things get a bit hairy in Git.

ESLint and Prettier will be installed from the Ubuntu terminal as will be the config files. See Part 1 for the specifics. ESlint and Prettier can be installed, and Prettier will work globally, not ESlint. But it is important to install the dependencies and peer dependencies globally. The config.file for ESLint will work the same and needs to be created. In short ESLint will look for a config file in the project directory and bubble up to Home if not found.

There is one thing to add to the User Settings in VSC which will convert the VSC terminal into a WSL terminal. Add the following snippet to the new Settings:

```js
"terminal.integrated.shell.windows": "C:\\WINDOWS\\System32\\wsl.exe"
```

### Hitting the limits in WSL

WSL, as good as it is, will not play nice with GUI tools, so no GNOME or Linux Unity.
It is also not too good at global installations. NodeJS passes muster, not ESLint or Nodemon , for instance. They will need to be installed on a per-project basis. One work-around is to integrate them in one's boilerplate `package.json`. Finally, the Ubuntu 18.04 provided works around a binary set from Linux kernel v. 4.04, not the most recent version of it. It is best left alone, no need to update.

### Installing PostgreSQL
This is a necessary item with 2 options, both with trade-offs. One is to install PostgreSQL for Win10, but then the PostgreSQL server will start with Win10, every time, and stay on all the time. It may be something not needed nor wanted.

The other way is to install PostgreSQL on the WSL side so it is sandboxed sort of, which is what is described further down. On the flip side, the server needs to be restarted each time a WSL session is started. In some instances, the database needs to be created before the app scripts sync the app DB part to the database. Be cautious and take it slow, this part is pretty involved and can go sideways easily.

First, open a WSL/Ubuntu window and update/upgrade the Ubuntu machine
```js
User@Linux~$ sudo apt update

User@Linux~$ sudo apt upgrade
```
The installation of Postgres is similar to the Part 1.

```js
User@Linux~$ sudo apt-get install postgresql postgresql-contrib

User@Linux~$ sudo -u postgres createuser --superuser <$YOUR_USERNAME>

User@Linux~$ createdb <$YOUR_USERNAME>
```
Then edit `pg_hba.conf` the same way, the version number is 10 as of August 2018.

```js
User@Linux~$ sudo nano /etc/postgresql/VERSION_NUMBER_HERE/main/pg_hba.conf
```
Replace the `md5` values by `trust`, moving with the arrows and typing in the same exact spot. The file should look like this:

![pg_hba.config](/images/pbhgaConf.png)

Confirm with `CTRL + O`, then `ENTER`, and exit with `CTRL + X`. Go back to home with `cd ~`.

Restart postgreSQL. It is the same command line for each time it is restarted. Or write a quick script to be executed when WSL is loaded.

### Starting and stopping PostgreSQL service

The main trade-off from installing PostgreSQL in WSL-Ubuntu and not in Win10 is to restart the PostgreSQL server each time the Ubuntu client is opened. Do it with :
```js
User@Linux~$ sudo service postgresql start
```
The other part is that the same server needs to be shut off when leaving. The server will continue taxing the memory and the CPU because of the Unix socket it uses. This can cause the machine to heat up. On thin machines like the Surface devices, it can be an issue. Use the following command:
```js
User@Linux~$ sudo service postgresql stop
```

### Installing some Tools
Links:

- ConEmu
- [Installing Postman](https://itrendbuzz.com/install-postman-native-app-on-ubuntu/)
- DBeaver documentation
- DBeaver install
- [Psql cheat sheet](http://www.postgresqltutorial.com/postgresql-cheat-sheet/)

From previously, Homebrew, or more exactly its little brother for Linux (Linuxbrew), will not work well in WSL, so skip it.
ZSH and Oh-My-Zsh will work, if prefered. A terminal manager like ConEmu can also be used, it’s just not completely necessary. It can run some GUI apps in WSL though. There are some possibilities but the cost in time may be a bit too much to really be interesting.

1. Postman, a really great tool for back-end development. Here, the __Win10__ version will be installed, __from the Win10 side__, NOT the WSL-Ubuntu side. It works off the port served by the app, so it needs to simply plug in the same port.

2. DBeaver: installed on the __Win10__ side, as WSL does not support GUI. Setting up the connection in DBeaver can be a tad tricky. First, the JDBC driver needs to be installed, via the tab Driver.The connection parameters are mainly the user previously created, and the relevant password, if one has been defined. Check in the DB window if the <your_user> database can be accessed, even if it is presently empty.

3. Nodemon and Testem: installable on a per-project basis, AFAIK.

4. Psql cheat sheet: The kind of handy link to have somewhere, just in case.

It is more comfortable to get all these grouped in the Start Menu, even more so with a tousch screen device. It should look something like this.

### Which browser?
Firefox is a good option, but Chrome or its open source twin Chromium are probably better for development. Just the debugger, if it’s the only aspect considered, is so worth the install. On the other hand, Firefox Inspector is quite good too. Your choice, or load them both.
It may be a good idea to add Chrome to the PATH in WSL. This allows chrome.exe to be invoked from the WSL prompt. It can also be opened from Win10, and used the same way as well.

### Testing
All those modifications have been tested on:
Custom-built desktop PC i-5 4690K overclocked, 16GB RAM, 2TB storage (SSD/2HD), GTX 1070 NVidia 8GB,
Surface Pro tablet (2017) i-7, 8GB RAM, 256GB SSD,
Surface Book 2 i-7, 16GB RAM, 1TB SSD, GTX 1060 NVidia 8GB.
All are running Windows 10 - April 2018.

_Microsoft, Windows, Windows 10 are trademarks of Microsoft Corp. MacBook Pro is a trademark of Apple Inc. Ubuntu is a trademark of Canonical Inc. UK._

_Thanks to Dakota Blair and the whole team at Fullstack Academy for their precious help._
