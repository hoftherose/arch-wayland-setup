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
