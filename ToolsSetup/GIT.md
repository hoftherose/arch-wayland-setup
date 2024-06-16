# Setup git on your new computer

You should already have git installed, which means that there won't be any need for that. But if for what ever case you don't just install through 
`pacman -Syu git`. Most of the steps here will be about setting up your config, ssh connections and ssh keys to online repos (github, gitlab and bitbucket).

## Setting up git config
When you use git for anything other than pulling projects (e.g commiting) it will ask you to setup your user, which means setting email and name. For the most part you should use your typical online repo account email, but there are ways to have more than one email used for different projects. We won't give the instructions on how to set this up, but you can reference the steps [here](https://blog.hao.dev/how-to-use-different-git-emails-for-personal-and-work-repositories-on-the-same-machine)

If you have already used git (most probable) make sure you use the same name, but more importantly the same email as your account. If the name is different, even slightly, it will appear differently in git logging. To setup simply run the following commands.

```
git config --global user.email "email@mail.com"
git config --global user.name "Your Name"
```

Notice the global aspect of this command, make sure this is intentional and that you are not sharing/overwriting accounts. This short setup you should be able to commit and make change to git projets locally, and even remotely depending on the repo settings.

## Setting up SSH Keys
As of August 13, 2021, password authentication was removed from github, and overall is not recommended in any remote git setting. Although there are other alternatives, the best setup for ALL git sessions is to create and setup ssh keys for your system. The following steps assumes there are no restrictions on the algorithm choice or overall password needed, but we will show later how to debug any issues when connecting.

### Creating keys
To create your keys on linux, you just need to run the following command: `ssh-keygen -t ed25519 -C "email@mail.com"`. Make sure the email is the same used to setup git config earlier. The value after -t is to setup the generation algorithm, so if there are any specifications on which you should use, this is where you should set it. For general usage `-t ed25519` is fine, for legacy systems, try swapping to `-t rsa -b 4096`.

Once you enter the command you will be asked to confirm the location, as long as the file is stored in $HOME/.ssh/ the naming of the file is not important, but it is recommended to keep as default unless you have more keys, in which case, append your use case after the default name (e.g id_ed25519_gitlab).

Once named, you will be asked to create a password, although this adds to the security of the keys, if you don't want to enter your password continuosly, simply enter an empty password. If you do setup a password, do remember it as there will be no way of using the keys without it. New keys are usually not hard to make but the nontheless it should be avoided for something such as this.

Once the key is created, go to your folder $HOME/.ssh and find the .pub key. This is your public key which can be shown (try not to though). You will need this to follow the next steps.

### Setup keys on online repos
Setup is usually the same on all platforms, only the settings menu changes places. On github click on your profile picture top right and go to settings. In the "SSH and GPG keys" tab find the button "New SSH key". On gitlab click again on your profile picture top left, and go to preferences. In the "SSH Keys" tab click on "Add new key". From here the steps are mostly the same.

In the key section paste your .pub file, it should start with the algorithm used and end with your email. In the title section simply choose a name that will help you remember which device that key belongs to. On gitlab you can set an expiration date, by default it will expire in one year.
