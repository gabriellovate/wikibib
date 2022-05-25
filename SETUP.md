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

Next you must clone `wikibib/wikibib` and reconfigure the remote repositories:

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
You can do this at <https://github.com/new> or via the [GitHub command line interface](https://github.com/cli/cli) (if installed) with `gh repo create`.
Make sure to use the same "Owner" and "Repository name" specified above.
Do not initialize the repository, other than optionally adding a Description.
Next, push your cloned manuscript:

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

After installing the pip package, just run in the command line

```bash
bib read Q18507561
```

Don't worry about any errors that might pop up at this step. 

A vscode window for notes will appear on your screen.
It has some categories and links, but don't worry about that just now. 
You can check the [USAGE.md](./USAGE.md) file for instructions on that.

The file has been created under the `notes` folder. 
Save it, and come back to the terminal. 

On the terminal, you may now run `./wlog`, which will commit your reading, and push it to GitHub.


## Set up the dashboard via GitHub Pages

On your GitHub settings, set GitHub Pages to run from "main/docs" and save.

To quickly go to the settings page, run the following command from your terminal:

```bash
xdg-open https://github.com/$OWNER/$REPO/settings/pages
```

After a short time, you should be able to access your dashboard already via GitHub pages, at `$OWNER.github.io/$REPO`. 

```bash
xdg-open https://$OWNER.github.io/$REPO
```

Sometimes there is a bug on GH Pages and you'll have to wait for the initial page to show up. 
It should be fixed with time. 

Your dashboard will nevertheless be available quickly at

 ```bash
 xdg-open https://$OWNER.github.io/$REPO/index.html
 ```

# Continue reading

The SETUP is done! To know how you can actually use WikiBib effectively, please check the [USAGE.md](./USAGE.md) file for instructions.

# Credit

* This SETUP was adapted from Manubot's rootstock (<https://github.com/manubot/rootstock>), which you should definitely check out. 