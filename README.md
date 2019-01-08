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
* `picn-nfn`

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

By using multiple configuration files, more than one instance of a PiCN executable can be started as systemd services.

### Enabling and Disabling

A service can be enabled to start when the system boots:
```console
you@machine:~$ systemctl enable picn-forwarder@none
```

Note that this does not start the service immediately. The service can be started as described in the previous section (if not yet running) or will start on reboot. A service can be disabled as following:
```console
you@machine:~$ systemctl disable picn-forwarder@none
```

### Status Monitoring

The following command shows status information of a service and logging output that PiCN instance:
```console
you@machine:~$ systemctl status picn-forwarder@none
...
```

All PiCN-related services are listed as following:
```console
you@machine:~$ systemctl list-units --type service | grep 'picn'
...
```

