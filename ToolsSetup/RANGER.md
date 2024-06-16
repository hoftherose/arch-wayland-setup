# Setup Ranger on your new computer
Ranger is going to be our terminal filemanager. This means that we need some setting up to do. Other than downloading optional dependencies, we will add an alias for moving folders with your ranger view.

## Setting up ranger folder sync
To setup your folder sync, you must set the following command aliased to the command ranger, this will "overwrite" it to automatically follow your ranger folder. Even though we are going to be using fish, i'll leave the command for zsh as well.

```
# For zsh
alias ranger='ranger --choosedir=$HOME/.rangerdir; LASTDIR=`cat $HOME/.rangerdir`; cd "$LASTDIR"'
# For fish
alias ranger='ranger --choosedir=$HOME/.rangerdir; set LASTDIR $(cat $HOME/.rangerdir); cd "$LASTDIR"'
```
