## Installation

Install on local computer:
```
bash <(curl -fsSL https://raw.githubusercontent.com/Flower7C3/docksal-remote/master/bin/install)
```

Uninstall from local computer:
```
bash <(curl -fsSL https://raw.githubusercontent.com/Flower7C3/docksal-remote/master/bin/uninstall)
```

## Configuration

In `docksal.env` file You have to configure following variables:
* `REMOTE_MACHINE_HOSTNAME` - remote server IP/hostname
* `REMOTE_MACHINE_SSH_USER` - remote user name for SSH login

> Configuration do not store remote SSH user password. Script will ask You for password on each SSH connection, but You can configure passwordless connection with SSH keys.

There are also optional variables:
* `REMOTE_MOUNT_NFS_VERSION` - mount command NFS version; default value is 3
* `REMOTE_MACHINE_SSH_PORT` - remote server port; default value is 22
* `DEVELOPER_MACHINE_HOSTNAME` - local machine IP for remote NFS connection; default value is local machine IP

You can save this configuration in project or globally. The easiest way is to execute `fin config set` command. Eg:

* `fin config set REMOTE_MACHINE_SSH_USER=john.doe` - will save `REMOTE_MACHINE_SSH_USER` variable with *john.doe* value in project `.docksal/docksal.env` file 
* `fin config set --global REMOTE_MACHINE_SSH_USER=jane.doe` - will save `REMOTE_MACHINE_SSH_USER` variable with *jane.doe* value in global `~/.docksal/docksal.env` file 

## Usage

In project directory where Docksal configuration exist just type `fin remote` command.
There are several commands in this script:
* `project`, `p` - work with project
    * `up` - warmup Docksal project; mount project on remote server, configure env files and run `fin up` on remote server
    * `start` - start Docksal project; mount project on remote server, configure env files and run `fin start` on remote server
    * `stop` - stop Docksal project; run `fin stop` on remote server, remote env files and umount project on remote server
    * `down` - remove Docksal project; run `fin remove -f` on remote server, remote env files and umount project on remote server
    * `restart` - restart Docksal project; run `fin remote project stop`, then `fin remote project start` on local 
    * `open` - open public project URL with `open` command
* `mount`, `m` - work with mountpoints
    * `up` - add valid path to `/etc/exports` file on local and mount project directory on remote server
    * `down` - umount directory on remote server and remove path from exports file on local
* `proxy`, `x` - run docker-compose commands on nginx proxy, all extra parameters are same like in `docker-compose` command
* `server`, `s` - run `fin` command in project directory on remote server
* `config`, `c` - shows config
* `up` - shortcut to `fin remote project up`
* `start` - shortcut to `fin remote project start`
* `restart` - shortcut to `fin remote project restart`
* `stop` - shortcut to `fin remote project stop`
* `down` - shortcut to `fin remote project down`
* `open` - shortcut to `fin remote project open`
