# Creating a new dashboard and workstation

These instructions detail how you can set up WikiBib as your literature manager from the [template`](https://github.com/wikibib/wikibib).
The process is largely manual, but you only have to perform it once for your dashboard. 

Currently, the repository has only been tested on Linux, and it might not work on other platforms. 

# Manual configuration

First, you must configure two environment variables (`OWNER` and `REPO`).
These variables specify the GitHub repository for the manuscript (i.e. `https://github.com/OWNER/REPO`).
Make sure that the case of `OWNER` matches how your username is displayed on GitHub.
In general, assume that all commands in this setup are case-sensitive.

On your terminal, add: 
```sh
# GitHub username or organization name (change from wikibib)
OWNER=wikibib
# Repository name
REPO=bib
```

## Create repository

**Execute the remaining commands verbatim.**
They do not need to be edited (if the setup works as intended).

You might have to run  **all commands as`sudo`, specially if you are using a Windows Subsystem for Linux.** 
Next you must clone `wikibib/wikibib` and reconfigure the remote repositories. 


```sh
# Clone manubot/rootstock
git clone --single-branch https://github.com/wikibib/wikibib.git $REPO
cd $REPO

# Configure remotes
git remote add rootstock https://github.com/wikibib/wikibib.git

# Option A: Set origin URL using its web address via SSH
git remote set-url origin git@github.com:$OWNER/$REPO.git
```

Then create an empty repository on GitHub. 

```sh
gh repo create
```
And run the default options.
 * Push an existing local repository to GitHub
 * Visibility  > Public
 * Add a remote > Y

You may also create a new repository manually at <https://github.com/new>, just make sure to use the same "Owner" and "Repository name" specified above. 

Next, push your repository:

```sh
git push --set-upstream origin main
```

# Install WikiBib

To install WikiBib just run
```bash
pip3 install -e . 
```

It also uses Virtual Studio Code for note management, so make sure you have it installed too. 
See the instructions for that [here](https://code.visualstudio.com/docs/setup/linux).


# Read your first article

After installing the pip package, just run in the command line.
 
 

```bash
bib read Q18507561
```

A vscode window for notes will appear on your screen.
You can check the [USAGE.md](./USAGE.md) file for details.

The file has been created under the `notes` folder. 
Save it, and come back to the terminal. 

On the terminal, you may now run `bib log`, which will commit your reading, and push it to GitHub.

## Set up the dashboard via GitHub Pages

On your GitHub settings, set GitHub Pages to run from "main/docs" and save.

To quickly go to the settings page, run the following command from your terminal:

```bash
xdg-open https://github.com/$OWNER/$REPO/settings/pages
```

After a short time, you should be able to access your dashboard already via GitHub pages, at `$OWNER.github.io/$REPO`. 

 ```bash
 xdg-open https://$OWNER.github.io/$REPO/index.html
 ```

# Continue reading

The SETUP is done! To know how you can actually use WikiBib effectively, please check the [USAGE.md](./USAGE.md) file for instructions.

# Credit

* This SETUP was adapted from Manubot's rootstock (<https://github.com/manubot/rootstock>), which you should definitely check out. 
