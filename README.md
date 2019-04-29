# Docksal on remote

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

Before run `fin remote` command in project, You have to setup `DOCKSAL_ENVIRONMENT` and `DOCKSAL_HOST` variables.
First variable will setup valid environment for variables and docker-compose configuration, second indicates which server will be used (just write valid IP and PORT)
```
export DOCKSAL_ENVIRONMENT="remote-web-xip"
export DOCKSAL_HOST="tcp://IP:PORT"
```

In `docksal.env` file You can configure optional variables:
* `DEVELOPER_MACHINE_HOSTNAME` - local machine IP for remote NFS connection; default value is local machine IP
* `PROJECT_INACTIVITY_TIMEOUT` - defines the timeout of inactivity after which the project stack will be stopped; default 0.5h

## Usage

In project directory where Docksal configuration exist just type `fin remote` command.

> Do NOT use *fin project*, *fin start*, *fin stop*, etc. commands!

Main commands in this script:
* `fin remote project`, `fin remote p` - work with project:
    * `fin remote project up` - warmup Docksal project: setup NFS connection, configure env files and run *fin up*
    * `fin remote project start` - start Docksal project: setup NFS connection, configure env files and run *fin start*
    * `fin remote project stop` - stop Docksal project: run *fin stop*, remote env files and cleanup NFS connection
    * `fin remote project down` - remove Docksal project: run *fin remove -f*, remove env files and cleanup NFS connection
    * `fin remote project restart` - restart Docksal project: run `fin remote project stop`, then `fin remote project start` on local 
    * `fin remote project open` - open public project URL with `open` command
* `fin remote proxy`, `fin remote x` - run docker-compose commands on nginx proxy, all extra parameters are same like in `docker-compose` command
* `fin remote config`, `fin remote c` - shows stack config

Short commands in this script:
* `fin remote up` - alias to `fin remote project up`
* `fin remote start` - alias to `fin remote project start`
* `fin remote restart` - alias to `fin remote project restart`
* `fin remote stop` - alias to `fin remote project stop`
* `fin remote down` - alias to `fin remote project down`
* `fin remote open` - alias to `fin remote project open`
