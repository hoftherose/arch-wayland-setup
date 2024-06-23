# Setup nvim on my computer
There are many shortcuts and setup steps in neovim we need to setup, so much so that most will not be explained through this guide, but instead there will be references to where you can setup some of these features yourselves. If you want a quick intro on how to setup neovim, this video from the [Primeagen](https://www.youtube.com/watch?v=w7i4amO_zaE) although rushes though quite a few things, if you take it slowly it's a pretty good place to start.

## Steps to follow from video
From the Primeagen video make sure you learn how to do the following steps. The rest of the video assumes you have packer setup and can address basic shortcut settings.

Setup packer, sourcing and syncing packages
Setup Basic shortcuts
Setup telescope

## Integration with ranger
I'm not a big fan of neovims default fileexplorer, and instead I really like using ranger for this task, that said it's pretty difficult to have to transition between one and the other all the time. To avoid this we will try to join the two tools with [rnvimr](https://github.com/kevinhwang91/rnvimr).

Follow the instructions on the repo for arch installation.

The following pácker line should be set, source the file and sync.

```
use ({ 'kevinhwang91/rnvimr' })
```
