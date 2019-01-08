# PiCN-systemd-service

This repository provides instructions and configuration files to run PiCN executables as systemd services.

## Installation

* Clone PiCN, if not yet available on your system: `git clone https://github.com/cn-uofbasel/PiCN.git`

* Download the [service definitions](services) to `/etc/systemd/system`

* Adjust the path in the downloaded files to the location of PiCN

* Add a new user `picn` which runs the PiCN instances: `useradd --system picn`. Alternatively, you can set `User` in the downloaded file to an existing user (not recommended).

## Usage

Available systemd services are:

* `picn-forwarder`
* todo: nfn relay and others

The follow examples explain how to manage a PiCN forwarder. All other services are handled equally.

### Starting and Stopping

A PiCN forwarder (default configuration) is started and stopped with following commands:
```console
you@machine:~$ systemctl start picn-forwarder@none
you@machine:~$ systemctl stop picn-forwarder@none
```

To change default arguments, the path of a configuration file can be passed instead of `none`:
```console
you@machine:~$ systemctl start picn-forwarder@-path-to-config-file
you@machine:~$ systemctl stop picn-forwarder@-path-to-config-file
```

The configuration file path must be escaped. The tool `systemd-escape` helps to generate escaped paths:
```console
you@machine:~$ systemd-escape '/path/to/config/file'
-path-to-config-file
```

My using multiple configuration files, more than one instance can be started as systemd services.

### Enabling and Disabling

todo

### Status monitoring

todo
