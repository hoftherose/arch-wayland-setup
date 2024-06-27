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

### Use ranger on startup
Because nvim uses netwr on startup, we won't really have the benefits of using ranger until after we use the command to open ranger. Since we won't be using netwr anyways, we can disable it and enable ranger instead. There are multiple global variables in the repo that can be placed in .config/nvim/init.lua. The very first variable here will give us ranger on startup instead of netwr.

## List of Packages
packer              # Plugin manager
telescope           # Search utility for files/folders
rnvimr              # Integrating TUI file explorer
lazygit             # Integrating TUI git utility
lazydocker          # Integrating TUI docker utility
k9s                 # Integrating TUI k8s utility (use self maintained version)
cyberdream          # Color Theme
treesitter          # Text parsing generator
harpoon             # File quick swap navigation tool
gitsigns            # Color coded git changes in vim signcolumn
better_escape       # Adds quick escape shortcut for insert mode
obsidian            # Note taking app utilities
lsp-zero            # Setup lsp server for various languages
mason               # LSP, linter and formater manager that works with lsp-zero (installed indirectly)

## Hidden dependencies
As they come I will be posting hidden dependencies here, some are obvious but others (e.g rg) are not so much. Some of the previous plugins will not work, or will work limitedly without these.

ripgrep             # Needed by telescope
obsidian            # Needed by obsidian
lazygit             # Needed by lazygit
lazydocker          # Needed by lazydocker
k9s                 # Needed by k9s
git                 # Needed by lazygit and gitsigns
docker              # Needed by lazydocker
