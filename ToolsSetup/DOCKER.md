# Setup docker on your new computer
Docker is not installed by default on arch, so that will be our first step to setting up docker. After we will setup users to allow us to use docker without sudo, add login credentials for dockerhub and setup tools like docker compose.

## Installing
Installing docker on arch is as simple as `sudo pacman -Syu docker`, that said, it is not enabled by default, so to use and startup on boot, you must run the following systemctl commands.

```
sudo systemctl start docker.service
sudo systemctl enable docker.service
```
With this you should be able to run `docker ps`, but only with sudo. The next step is to setup your user to be able to run docker without sudo.
