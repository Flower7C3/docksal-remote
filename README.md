# Docksal on remote

## Installation

Install on local computer [Docksal](https://docksal.io/installation) and *fin remote* command:

```
bash <(curl -fsSL https://raw.githubusercontent.com/Flower7C3/docksal-remote/master/bin/install)
```

Uninstall from local computer:
```
bash <(curl -fsSL https://raw.githubusercontent.com/Flower7C3/docksal-remote/master/bin/uninstall)
```

## Configuration

First create program configuration with `fin remote config-setup` command. 
Next load configuration to shell with `eval $(fin remote config-dump)` command.

All configuration will be saved in `.env.docksal-remote` file.


## Usage

In project directory where Docksal configuration exist just type `fin remote` command.

> Do NOT use *fin project*, *fin start*, *fin stop*, etc. commands!

Main commands in this script:
* `fin remote project`, `fin remote p` - work with project:
    * `fin remote project up` - warmup Docksal project: setup NFS connection, configure env files and run *fin up*
    * `fin remote project down` - remove Docksal project: run *fin remove -f*, remove env files and cleanup NFS connection
    * `fin remote project reset` - reset Docksal project: run `fin remote project down`, then `fin remote project up` on local 
    * `fin remote project start` - start Docksal project: setup NFS connection, configure env files and run *fin start*
    * `fin remote project stop` - stop Docksal project: run *fin stop*, remote env files and cleanup NFS connection
    * `fin remote project restart` - restart Docksal project: run `fin remote project stop`, then `fin remote project start` on local 
    * `fin remote project open` - open public project URL with `open` command
* `fin remote proxy`, `fin remote x` - run docker-compose commands on nginx proxy, all extra parameters are same like in `docker-compose` command
* `fin remote config`, `fin remote cfg`, `fin remote c` - shows stack config
* `fin remote config-setup`, `fin remote cfg-setup` - save new config to .env.docksal-remote file
* `fin remote config-dump`, `fin remote cfg-dump` - display config from .env.docksal-remote file

Short commands in this script:
* `fin remote up` - alias to `fin remote project up`
* `fin remote down` - alias to `fin remote project down`
* `fin remote reset` - alias to `fin remote project reset`
* `fin remote start`, `fin remote s` - alias to `fin remote project start`
* `fin remote stop`, `fin remote e` - alias to `fin remote project stop`
* `fin remote restart` - alias to `fin remote project restart`
* `fin remote open`, `fin remote www` , `fin remote o` - alias to `fin remote project open`
