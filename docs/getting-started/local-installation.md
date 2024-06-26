# Local Installation
*Please note that local installation requires some technical expertise and comfort using a terminal/command line. If you are not comfortable with this, we recommend using Turnroot Editor in the cloud at [editor.turnroot.com](https://editor.turnroot.com).*

## Overview
The Turnroot Editor runs on two databases and two Node.js "servers". The technical reasons for this are not relevant here (you can read them if you want: [Structure](../technical-details/structure.md)), but it does mean that you need to install some software on your computer to run the Turnroot Editor locally.

The most important thing to remember when working with the Turnroot Editor locally is that you need to have both the MariaDB and MongoDB services running. If you don't, the Turnroot Editor won't work. You also need to have both Node.js servers running. If you encounter any errors, there's a 99% chance that one of these four things isn't running.


## Requirements
- An administrator account on your computer
- [Node.js](https://nodejs.org/en/)
- [npm](https://www.npmjs.com/get-npm)
- [Git](https://git-scm.com/downloads) (optional, but recommended)
- [MariaDB](https://mariadb.org/download/)
- [MongoDB Community Server](https://www.mongodb.com/try/download/community)

If you already have Node.js installed, you're good to skip the next section. If you don't, or you're not sure, you'll need to install it. 

### Installing Node.js and Git
#### Windows
1. Download the Windows installer from the [Node.js website](https://nodejs.org/en/), and the Git installer from [Git website](https://git-scm.com/downloads). (You can skip Git if you want.)
2. Run the installers.
3. Follow the prompts in the installers.
4. Restart your computer.

#### macOS
You can use homebrew to install Node.js and Git on macOS.
1. Open Terminal.
2. Run the following command:
``` brew install node && brew install git``` (if you're not wanting to install Git, you can remove the `&& brew install git` part)
If this provides an error, you'll need to use a different method to install Node.js or install homebrew. Google is your friend here.

#### Linux
You can use your package manager to install Node.js and Git on Linux. For example, on Ubuntu, you can run the following command:
```sudo apt install nodejs && sudo apt install git``` (if you're not wanting to install Git, you can remove the `&& sudo apt install git` part)

### Installing MariaDB 
You don't need to change any settings during the installation process. Just install it and you're good to go. The Turnroot Editor will handle the database setup for you.

#### Windows
1. Download the Windows installer from the [MariaDB website](https://mariadb.org/download/).
2. Run the installer, install it, etc.

#### macOS
Run `brew install mariadb` in Terminal.

#### Linux
```sudo apt install mariadb-server```

### Installing MongoDB
Installing MongoDB is, to be candid, a bit of a pain. I highly recommend Googling your specific OS to find the best way to install it. One excellent guide I've found is: 
[Setting up a Local MongoDB Database - prisma.io](https://www.prisma.io/dataguide/mongodb/setting-up-a-local-mongodb-database)

Once installed, you can check that MongoDB is running by running `mongosh` in your terminal (if this works, type `exit` to leave the shell).

Again, you don't need to change any settings during the installation process.

## Setup
### Installing the Turnroot Editor
As mentioned, you'll need two Node.js applications running. One controls the editor itself, and one handles data. You can find the two applications here:
- https://github.com/turnroot/turnroot-editor-server
- https://github.com/turnroot/turnroot-schemas

You have two major options here; you can download those from the Releases page on GitHub (or the sidebar on the main page), or you can clone the repositories using Git. I recommend the latter, as it makes updating the applications easier. Please note that neither option will give you automatic updates; you'll need to check the repositories for updates yourself.

Once you've installed those applications your preferred way (and unzipped them, if needed), you'll need to install the dependencies. 

### Turnroot Schemas
1. Open a terminal and navigate to the turnroot-schemas folder. The easiest way to do this is to type `cd ` (with a space after) and then drag the folder into the terminal window. Press Enter.
2. Run `npm install` to install the dependencies.
3. Run `npm run start` to start the server.

### Turnroot Editor Server
1. Open a terminal and navigate to the turnroot-editor-server folder. The easiest way to do this is to type `cd ` (with a space after) and then drag the folder into the terminal window. Press Enter.
2. Run `cd server` to navigate to the server folder.
3. Run `npm install` to install the dependencies.
4. Run `npm run start` to start the server.

If you encounter any errors at this point, *make sure MariaDB and MongoDB are running*. 

### Accessing the Editor
Once you've started both servers, you can access the editor by going to `http://localhost:26068` in your browser. If you encounter any errors, check the terminal windows where you started the servers for any error messages.

Your editor is now running locally! If you have any questions or need help, please don't hesitate to ask on [Turnroot Community](https://community.turnroot.com).

### Stopping the Editor
To stop the editor, you can close the terminal windows where you started the servers. I don't recommend stopping the databases. 

Turning off your computer will also stop the editor. You can restart it by running `npm run start` in the appropriate folders (turnroot-schemas and turnroot-editor-server/server).

### Updating the Editor
If you used git to download, you can just run `git pull` in the folders.

Otherwise, you'll need to download the latest releases from the GitHub repositories. You can then replace the existing files with the new ones.  You'll need to run `npm install` again in the schemas folder and the server folder to update the dependencies.

## Support
If you're struggling with any part of this process, please don't hesitate to ask for help on [Turnroot Community](https://community.turnroot.com). We can definitely try to help! Please note that if our suggestions don't work, we're pretty limited in what we can do to help you. You are always welcome to use the cloud version of the Turnroot Editor at [editor.turnroot.com](https://editor.turnroot.com) instead.



