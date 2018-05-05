### git config
Git comes with a tool called `git config` that lets your get and set configuration variables that controls alla spects of how Git looks and operates.
1. `/etc/gitconfig` file: Contains values applied to every user on the system and all their repositories. If you pass the option `--system` to `git config`, it reads and writes from this file specifically. (Because this is a system configuration file, you would need administrative or superuser privilege to make changes to it.)

2. `~/.gitconfig` or `~/.config/git/config` file: Values specific personally to you, the user. You can make Git read and write to this file specifically by passing the `--global` option.

3. `config` file in the Git directory (that is, `.git/config`) of whatever repository you’re currently using: Specific to that single repository.

Each level overrides values in the previous level, so values in .git/config trump those in /etc/gitconfig.

### Few basic settings
* Your identity: You should set your username and email address. This is important because every Git commit uses this informationn, and it's immutably baked into the commits:
```bash
$ git config --global user.name "Tony Xu"
$ git config --global user.email tony@lixu.ca
```
Again, you need to do this only once if you pass the --global option, because then Git will always use that information for anything you do on that system. If you want to override this with a different name or email address for specific projects, you can run the command without the --global option when you’re in that project.

* Your editor:
```bash
$ git config --global core.editor emacs
```
That's it! These are the basic settings you need to get started!

### Check your settings
```bash
$ git config --list
core.excludesfile=~/.gitignore
core.legacyheaders=false
core.quotepath=false
mergetool.keepbackup=true
push.default=simple
color.ui=auto
color.interactive=auto
...
```
You may see keys more than once, because Git reads the same key from different files (`/etc/gitconfig`, `~/.gitconfig`, and `project/.git/config`). In this case, Git uses the last value for each unique key.

You can also check what Git thinks a specific key’s value is by typing `git config <key>`:
```bash
$ git config user.name
Tony Li Xu
```