# The Node.js Version Manager _for Windows_
[![Open Source Helpers](https://www.codetriage.com/coreybutler/nvm-windows/badges/users.svg)](https://www.codetriage.com/coreybutler/nvm-windows)


## Manage Multiple Versions of Node.js on Windows

**TL;DR** This project is similar (but not identical) to [nvm](https://github.com/creationix/nvm), a popular Node.js version manager for macOS/Linux.

The original [nvm](https://github.com/nvm-sh/nvm) is a completely separate project _for macOS/Linux only._ This project is based on an entirely different philosophy, is built for Windows, and is not just a clone of nvm. Read more about [Why Another Version Manager?](https://github.com/coreybutler/nvm-windows#why-another-version-manager) and [What's the Big Difference?](https://github.com/coreybutler/nvm-windows#whats-the-big-difference).

### Purpose
There are situations where the ability to switch between different versions of Node.js can be very useful. Microsoft recommends this project in their [Node.js environment setup guide](https://github.com/coreybutler/nvm-windows.git) and npm recommends it in their [Node.js installation and configuration guide](https://docs.npmjs.com/cli/v6/configuring-npm/install#windows-node-version-managers).  Some common uses for NVM for Windows include:
- Testing code with a newer (beta) version of Node.js without uninstalling an older (stable or LTS) version
- Easily switching between working on multiple projects with different Node.js version requirements
- Testing specific combinations of Node.js versions and installed global packages


### Features
- Easy installation and switching of Node.js versions and architectures
- Designed from the ground-up for use with Windows
- Support for Node.js v4+
- Independent installer and uninstaller

### Requirements & Limitations
- This has always been a version manager for only Node.js so there is no back-support for [io.js](https://github.com/maxogden/io.js).

- You must have Windows administrator rights when executing `nvm install` or `nvm use` commands (which create symlinks).
- Global npm modules are **not** shared between the different versions of Node.js you have installed. **This is by design** to allow fully isolated environments between different Node.js versions.  Additionally, some npm modules may not be supported in the version of Node.js you're using, so be aware of your environment as you work.

### Downloading & Installing
Downloads are available on the [releases](https://github.com/coreybutler/nvm-windows/releases) page.  See below for important installation instructions.


---
## About

### Like This project?

Let people know with a [tweet](https://twitter.com/intent/tweet?hashtags=nodejs&original_referer=http%3A%2F%2F127.0.0.1%3A91%2F&text=Check%20out%20NVM%20for%20Windows!&tw_p=tweetbutton&url=http%3A%2F%2Fgithub.com%2Fcoreybutler%2Fnvm-windows&via=goldglovecb) or better yet, **click the "Sponsor" button** at the top of this page.

### Notices

This repository now uses [Github Discussions](https://github.com/coreybutler/nvm-windows/discussions) for updates. Sponsors also receive occasional email updates. The Gitter channel has been retired in favor of these new features. Old notices have moved to the [notices wiki entry](https://github.com/coreybutler/nvm-windows/wiki/Notices).

### Common Issues & Resolutions

Please see the [Common Issues](https://github.com/coreybutler/nvm-windows/wiki/Common-Issues) page before posting an issue.


## Getting Started


### Before Installation
**You must uninstall any existing versions of Node.js before installing NVM for Windows to prevent conflicting versions**.

1. Backup any global `npmrc` configurations (e.g. `C:\Users\<user>\AppData\Roaming\npm\etc\npmrc`) and/or copy the settings to the user config `C:\Users\<user>\.npmrc`.
2. Delete any existing installation directories (e.g. `C:\Program Files\nodejs`) that might remain. NVM for Windows uses symlinks to switch active versions which will **not** work properly if an installation directory exists, **even if it is empty**.
3. Delete the existing npm install location (e.g. `C:\Users\<user>\AppData\Roaming\npm`) to prevent global module conflicts.

### Installing
NVM for Windows comes with an installer and uninstaller that can be downloaded on the [releases](https://github.com/coreybutler/nvm/releases) page. There is also a manual option (see [manual installation](https://github.com/coreybutler/nvm-windows/wiki#manual-installation) in the wiki).

_Tip: If the command `nvm` does not work immediately after installation, you may need to restart terminal/cmd/powershell._

![NVM for Windows Installer](http://i.imgur.com/x8EzjSC.png)

### After Installation

After installation, you will need to install one or more Node.js versions and then reinstall global utilities (e.g. yarn) for each installed version of Node.js.  See examples below. For more details about using yarn with NPM for Windows, see the [wiki](https://github.com/coreybutler/nvm-windows/wiki/Common-Issues#how-do-i-use-yarn-with-nvm-windows).

Install Node.js 14.15.4 LTS (both 32 and 64-bit), use 32 bit, and install yarn globally:
```
nvm install 14.15.4 all
nvm use 14.15.4 32
npm install -g yarn
```
Install Node.js 12.20.1 (architecture matching your system) and install yarn globally:
```
nvm install 12.20.1
nvm use 12.20.1
npm install -g yarn
```

### Upgrading

To upgrade NVM for Windows, simply run the new installer. It will safely overwrite the files it needs to update without touching your Node.js installations. Make sure you use the same installation and symlink folder. If you originally installed to the default locations, you just need to click _"next"_ on each window until the installer finishes.

## Using NVM for Windows

_Figure 1: NVM for Windows_
![NVM for Windows](http://i.imgur.com/BNlcbi4.png)

_Figure 2: Switching between stable and unstable versions_.
![Switching between stable and unstable versions.](http://i.imgur.com/zHEz8Oq.png)

**Important**: NVM for Windows must be run from within a shell with administrator rights. You'll need to run `powershell`, [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701), or `cmd` (Command Prompt) as Administrator.  NVM for Windows supports the following commands:

### Available Commands (Old Version)
- `nvm`: Show help
- `nvm arch`: Show if Node.js is running in 32 or 64-bit mode.
- `nvm arch {32|64}`: Set the default architecture to 32 or 64-bit.
- `nvm install <version> [32|64|all]`: Install the specified Node.js version.
  - `<version>` (Required) The Node.js version to install (or "latest" to install the latest stable version).
  - `[32|64|all]` (Optional) Specify whether to install the 32 or 64-bit version or "all" to install both.
    - Defaults to system architecture if not specified.
- `nvm list`: Show the versions of Node.js currently installed.
- `nvm list available`: Show the versions of Node.js available for installation.
- `nvm on`: Enable Node.js version management.
- `nvm off`: Disable Node.js version management (does not uninstall anything).
- `nvm proxy`: Show the current proxy setting.
- `nvm proxy <url>`: Set a proxy to use for downloads.
- `nvm proxy none`: Remove the proxy setting.
- `nvm uninstall <version>`: Uninstall a specific version of Node.js.
- `nvm use [<version>] [32|64]`: Switch to the specified Node.js version or architecture.
  - `version` (Optional) Specify the version of Node.js to use (must be installed first).
  - `[32|64]` (Optional) Specify to use 32 or 64-bit architecture.
    - For information about using `use` in a specific directory (or using `.nvmrc`), please refer to [issue #16](https://github.com/coreybutler/nvm-windows/issues/16).
- `nvm root`: Show the current root.
- `nvm root <path>`: Set the directory where nvm should store Node.js installations.
- `nvm version`: Show the current running version of NVM for Windows.
- `nvm node_mirror <url>`: Set the node mirror to the URL provided.
  - People in China can use *https://npm.taobao.org/mirrors/node/*
- `nvm npm_mirror <url>`: Set the npm mirror to the URL provided.
  - People in China can use *https://npm.taobao.org/mirrors/npm/*

### Availble Commands
| Command | Purpose
| :--- | :--- 
| `nvm` | Show nvm syntax help
| `nvm arch` | Show if Node.js is running in 32-bit or 64-bit
| `nvm arch {32\|64}` | Set the default architecture to 32-bit or 64-bit
| `nvm install <version> [32\|64\|all]` | Install the specified Node.js version and architecture
| `nvm list` | Show the versions of Node.js currently installed
| `nvm list available` | Show the versions of Node.js available for installation
| `nvm on` | Enable Node.js version management
| `nvm off` | Disable Node.js version management (does not uninstall anything)
| `nvm proxy` | Show the current proxy setting
| `nvm proxy <url>` | Set a proxy to use for downloads
| `nvm proxy none` | Remove the proxy setting
| `nvm uninstall <version>` | Uninstall a specific version of Node.js
| `nvm use [<version>] [32\|64]` | Switch to the specified Node.js version or architecture
| `nvm root` | Show the current root
| `nvm root <path>` | Set the directory where nvm should store Node.js installations.
| `nvm version` | Show the current running version of NVM for Windows.
| `nvm node_mirror <url>` | Set the node mirror to the URL provided<br />_People in China can use https://npm.taobao.org/mirrors/node/_
| `nvm npm_mirror <url>` | Set the npm mirror to the URL provided<br />_People in China can use https://npm.taobao.org/mirrors/npm/_
  
### Command Examples

| Command | Result |
| :--- | :--- |
| `nvm` | Show nvm syntax help
| `nvm arch 32` | Set default architecture to 32-bit
| `nvm install 14.15.4 64` | Install 64-bit architecture of Node.js v14.15.4
| `nvm install latest` | Install latest stable version with current system architecture
| `nvm use 14.15.4 64` | Set active version to Node.js v14.15.4 (64-bit)
| `nvm use 64` | Set 64-bit architecture of currently active Node.js version
| `nvm uninstall 14.15.4` | Uninstall Node.js v14.15.4
| `nvm root D:\NVM` | Set NVM for Windows to install Node.js versions to D:\NVM

_Note: For information about using `nvm use` in a specific directory (or using `.nvmrc`), please refer to [issue #16](https://github.com/coreybutler/nvm-windows/issues/16)._

### Antivirus

Users have reported some problems using antivirus, specifically McAfee. It appears the antivirus software is manipulating access to the VBScript engine. See [issue #133](https://github.com/coreybutler/nvm-windows/issues/133) for details and resolution.

As of 1.1.7, the executable and installation files are code-signed by [Ecor Ventures LLC](https://ecorventures.com)/[Author.io](https://author.io). This should help prevent false positives with most antivirus software.


## Building NVM for Windows From Source
A detailed guide to build from source is outside the scope of this document, but can be achieved with the following steps:
1. Install go from http://golang.org
2. Download source (or git clone this repo)
3. Change GOARCH to amd64 in build.bat if you feel like building a 64-bit executable
4. Start a Windows command prompt and change directory to project directory
5. Execute `go get github.com/blang/semver`
6. Execute `go get github.com/olekukonko/tablewriter`
7. Execute `build.bat`
8. Check the `dist` directory for generated setup program

---
## More Information
### Why another version manager?

There are several version managers for Node.js. Tools like [nvm](https://github.com/creationix/nvm) and [n](https://github.com/tj/n) only run on macOS and Linux. Windows users are left in the cold? No. [nvmw](https://github.com/hakobera/nvmw) and [nodist](https://github.com/marcelklehr/nodist)
are both designed for Windows. So, why another version manager for Windows?

The architecture of most Node.js version managers for Windows rely on `.bat` files, which do some clever tricks to set or mimic environment variables. Some of them use Node.js itself (once it's downloaded), which is admirable, but prone to problems. Right around Node.js 0.10.30, the installation structure changed a little, causing some of these to just stop working with anything new.

Additionally, some users struggle to install these modules since it requires a little more knowledge of node's installation structure. I believe if it were easier for people to switch between versions, people might take the time to test their code on back and future versions... which is just good practice.

### What's the big difference?

First and foremost, this version of nvm has no dependency on node. It's written in [Go](https://golang.org/), which is a much more structured approach than hacking around a limited `.bat` file. It does not rely on having an existing node installation. Go offers the ability to create a macOS/Linux version on the same code base. In fact, this is already underway.

The control mechanism is also quite different. There are two general ways to support multiple node installations with hot switching capabilities. The first is to modify the system `PATH` any time you switch versions, or bypass it by using a `.bat` file to mimic the node executable and redirect accordingly. This always seemed a little hackish to me, and there are some quirks as a result of this implementation.

The second option is to use a symlink. This concept requires putting the symlink in the system `PATH`, then updating its target to the node installation directory you want to use. This is a straightforward approach, and seems to be what people recommend.... until they realize just how much of a pain symlinks are on Windows. This is why it hasn't happened before.

In order to create/modify a symlink, you must be running as an admin, and you must get around Windows UAC (that annoying prompt). Luckily, this is a challenge I already solved with some helper scripts in [node-windows](https://github.com/coreybutler/node-windows). As a result, NVM for Windows maintains a single symlink that is put in the system `PATH` during installation only. Switching to different versions of node is a matter of switching the symlink target. As a result, this utility does **not** require you to run `nvm use x.x.x` every time you open a console window. When you _do_ run `nvm use x.x.x`, the active version of node is automatically updated across all open console windows. It also persists between system reboots, so you only need to use nvm when you want to make a change.

NVM for Windows comes with an installer, courtesy of a byproduct of my work on [Fenix Web Server](http://fenixwebserver.com).

Overall, this project brings together some ideas, a few battle-hardened pieces of other modules, and support for newer versions of node.

NVM for Windows recognizes the "latest" versions using a [list](https://nodejs.org/download/release/index.json) provided by the Node project. Version 1.1.1+ use this list. Before this list existed, I was scraping releases and serving it as a standalone [data feed](https://github.com/coreybutler/nodedistro). This list was used in versions 1.1.0 and prior, but is now deprecated.

## Motivation

I needed it, plain and simple. Additionally, it's apparent that [support for multiple versions](https://github.com/nodejs/node-v0.x-archive/issues/8075) is not
coming to node core, or even something they care about. It was also an excuse to play with Go.

## Why Go? Why Not Node?

I chose Go because it is cross-platform, felt like less overhead than Java, has been around longer than most people think, and I wanted to experiment with it. I've been asked why I didn't write it with Node. Trying to write a tool with the tool you're trying to install doesn't make sense to me. As a result, my project requirements for this were simple... something that's not Node. Node will continue to evolve and change. If you need a reminder of that, io.js. Or consider all the breaking changes between 4.x.x and 6.x.x. These are inevitable in the world of software.

## License

MIT.

## Sponsors

<table cellpadding="10" cellspacing="0" border="0">
  <tr>
    <td><a href="https://metadoc.io"><img src="https://github.com/coreybutler/staticassets/raw/master/sponsors/metadoclogobig.png" width="200px"/></a></td>
    <td><a href="https://butlerlogic.com"><img src="https://github.com/coreybutler/staticassets/raw/master/sponsors/butlerlogic_logo.png" width="200px"/></a></td>
  </tr>
</table>

## Thanks

Thanks to everyone who has submitted issues on and off Github, made suggestions, and generally helped make this a better project. Special thanks to:

- [@vkbansal](https://github.com/vkbansal), who provided significant early feedback throughout the early releases.
- [@rainabba](https://github.com/rainabba) and [@sullivanpt](https://github.com/sullivanpt) for getting Node v4 support integrated.
- [@s-h-a-d-o-w](https://github.com/s-h-a-d-o-w) who resolved the longstanding space escaping issue in path names ([#355](https://github.com/coreybutler/nvm-windows/pull/355)).
