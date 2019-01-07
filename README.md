# PiCN-systemd-service

This repository provides instructions and configuration files to run PiCN executables as systemd services.

## Installation

* Clone PiCN, if not yet available on your system: `git clone https://github.com/cn-uofbasel/PiCN.git`

* Download the [service definitions](services) to `/etc/systemd/system`

* Adjust the path in the downloaded files to the location of PiCN

* Adjust the user in the downloaded files (optional, recommended) 

## Usage

Available systemd services are:

* `picn-forwarder`
* todo: nfn relay and others

The follow examples explain how to manage a PiCN forwarder. All other services are handled equally.

### Starting and Stopping

todo

### Enabling and Disabling

todo

### Status monitoring

todo
