# Setup Ranger on your new computer
Ranger is going to be our terminal filemanager. This means that we need some setting up to do. Other than downloading optional dependencies, we will add an alias for moving folders with your ranger view.

## Creating config files
By default ranger's files are stored somewhere in root, but if configs are set then it will use those instead. Best practice is to copy the defaults and build from there. To do this you need to run the following in the `.config/ranger` folder. NOTE if you did the below step first then ranger will need to be run directly, as the extra parameters in the alias don't let you copy the config over.

```
ranger --copy-config=all
```

## Setting up ranger folder sync
To setup your folder sync, you must set the following command aliased to the command ranger, this will "overwrite" it to automatically follow your ranger folder. Even though we are going to be using fish, i'll leave the command for zsh as well.

```
# For zsh
alias ranger='ranger --choosedir=$HOME/.rangerdir; LASTDIR=`cat $HOME/.rangerdir`; cd "$LASTDIR"'
# For fish
alias ranger='ranger --choosedir=$HOME/.rangerdir; set LASTDIR $(cat $HOME/.rangerdir); cd "$LASTDIR"'
```
