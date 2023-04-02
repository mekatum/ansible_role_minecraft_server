# Ansible role for deploy self-hosted vanilla minecraft server

This Ansible role deploy self-hosted [minecraft](https://www.minecraft.net)
server with
[minecraft-client-rs](https://github.com/willroberts/minecraft-client-rs)
for control.

## System requirements

So to run the playbook you will need:
* Ansible 2.12 on management node
* Alpine Linux >= 3.17 with python3 installed on managed node

If you don't want to use compiled minecraft-cli binary,
you can compile it yourself from the project sources
([minecraft-client-rs](https://github.com/willroberts/minecraft-client-rs))
and put it to role files.

## How to use it

Create the playbook `minecraft.yaml` like below and override some variables

```yaml
- hosts: minecraft.your-domain.local
  roles:
    - minecraft
  become: True
  become_method: su
  vars:
      #CHANGE_THIS_PASSWORDS
    - minecraft_rcon_pass: rc0n_Pas$w0rd
```

And run this playbook with `ansible-playbook`
```console
user@host:~$ ansible-playbook minecraft.yaml
```

## Default vars


* `minecraft_path` — path to server files
* `minecraft_user` — user which will run server
* `minecraft_group` — group which will run serve
* `minecraft_jvm_max_ram` — max RAM size in MB which will be used by JVM
* `minecraft_jvm_init_ram` — start RAM size in MB which will be used by JVM
* `minecraft_jvm_extra_opts` — extra options to JVM
* `minecraft_server_url` — URL to server jar-file
* `minecraft_server_ip` — server IP
* `minecraft_rcon_port` — RCON port
* `minecraft_rcon_pass` — RCON password
* `minecraft_minecraft_cli_path` — path to minecraft-cli binary
* `minecraft_server_shutdown_message` — notification before server shutdown
* `minecraft_server_shutdown_delay` — delay before server shutdown
