# Docksal on remote

Allow to run fin on remote server with custom remote domain.


## Installation

Install on local computer:
1. [Docksal](https://docksal.io/installation)
2. *fin remote* command:

```
bash <(curl -fsSL https://raw.githubusercontent.com/Flower7C3/docksal-remote/master/bin/install)
```

Uninstall from local computer:
```
bash <(curl -fsSL https://raw.githubusercontent.com/Flower7C3/docksal-remote/master/bin/uninstall)
```

## Configuration

First create program configuration with `fin remote config set` command. 
Next load configuration to shell with `eval $(fin remote config get)` command.

All configuration will be saved in `.env.docksal-remote` file.


## Usage

In project directory where Docksal configuration exist just type `fin remote` command.

> Do NOT use *fin project*, *fin start*, *fin stop*, etc. commands!

Main commands in this script:
* `fin remote project|p` - work with project:
    * `fin remote project up` - warmup Docksal project: setup NFS connection, configure env files and run *fin up*
    * `fin remote project down (-f|--force)` - remove Docksal project: run *fin remove -f*, remove env files and cleanup NFS connection
    * `fin remote project reset (-f|--force)` - reset Docksal project: run `fin remote project down`, then `fin remote project up` on local 
    * `fin remote project start|s` - start Docksal project: setup NFS connection, configure env files and run *fin start*
    * `fin remote project stop|e` - stop Docksal project: run *fin stop*, remote env files and cleanup NFS connection
    * `fin remote project restart|r` - restart Docksal project: run `fin remote project stop`, then `fin remote project start` on local 
    * `fin remote project open|o|www` - open public project URL with `open` command
* `fin remote proxy|x` - run docker-compose commands on nginx proxy, all extra parameters are same like in `docker-compose` command
* `fin remote config|cfg|c` - shows stack config
    * `fin remote config setup|set (-f|--force)` - save new config to *.env.docksal-remote* file
    * `fin remote config variables|get` - display config from *.env.docksal-remote* file
    * `fin remote config check|k` - check if config is loaded to shell
    * `fin remote config docksal|d` - Docksal configuration
    * `fin remote config ngnix|www|w` - Ngnix server configuration
    * `fin remote config containers|container|c` - Docker containers configuration
    * `fin remote config networks|network|net|n` - Docker networks configuration
    * `fin remote config volumes|volume|vol|v` - Docker volumes server configuration
* `eval $(fin remote config-dump)` - export config from *.env.docksal-remote* file to current shell

Short commands in this script:
* `fin remote up` - alias to `fin remote project up`
* `fin remote down` - alias to `fin remote project down`
* `fin remote reset` - alias to `fin remote project reset`
* `fin remote start`, `fin remote s` - alias to `fin remote project start`
* `fin remote stop`, `fin remote e` - alias to `fin remote project stop`
* `fin remote restart` - alias to `fin remote project restart`
* `fin remote open|www|o` - alias to `fin remote project open`
