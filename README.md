# git-deploy

A simple Git deployment Bash script.

## Create a bin directory

Create `bin` in the main user directory by navigating to `~` (which is a shortcut for current user home directory, or `/Users/username`).

```bash
cd ~      # this takes us to /Users/username
mkdir bin # this creates /Users/username/bin
```
## Export your bin directory to the PATH

Open `.bash_profile`, which will be located at `/Users/username/.bash_profile`, and add this line to the file. If `.bash_profile` doesn't exist, create it.

```bash
export PATH=$PATH:/Users/tania/bin
```

If you don't see hidden files and directories, or those that begin with a `.`

## Create a script file and make it executable

Go to your `bin` folder located in `/Users/username`.

```bash
cd bin
```

Create a file called `git-deploy` (no extension) in this folder.

```bash
touch git-deploy
```

Open the file in your text editor of choice and type the following.

```bash
#!/usr/bin/bash
```

A bash script must always begin with #!/bin/bash to signify that the script should run with bash as opposed to any other shell. This is called a "shebang". You can confirm where the bash interpreter is located with which bash.

```bash
which bash
```

Now edit the `git-deploy` file

```bash
#!/usr/bin/bash

read -r -p 'Commit message: ' desc  # prompt user for commit message
git add .                           # track all files
git add -u                          # track deletes
git commit -m "$desc"               # commit with message
git push origin master              # push to origin
```

Make it an executable file by changing the permissions.

```bash
chmod u+x git-deploy
```

Then just run the command.