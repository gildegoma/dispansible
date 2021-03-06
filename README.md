# dispansible [![Build Status](https://travis-ci.org/dispansible/dispansible.svg?branch=master)](https://travis-ci.org/dispansible/dispansible)

Setup all the things on your workstation with Ansible.

**Warning:** this project is currently in *alpha* state.

## "Supported" Platforms

The targeted Operating Systems are currently:

* **Debian / Ubuntu / Linux Mint** Linux distributions (mainly based on apt/ppa packaging, but also on [Linuxbrew](http://linuxbrew.sh/). Currently focused on Ubuntu 14.04 generation.
* **Mac OS X 10.10+** (mainly based on [Homebrew](http://brew.sh/) and [Homebrew Cask](https://caskroom.github.io/) packages)

### Possible Future Targets

Pending on dispansible community size and interests

* [Arch Linux](https://www.archlinux.org/)
* [Korora Linux](https://kororaproject.org/) _a nice looking Fedora-based distribution_ with goals similar to Linux Mint.
* [Redox OS](http://www.redox-os.org/) _a Unix-like Operating System written in Rust_
* Open/Free/Net BSD

## Credits

This project initially began as a fork of https://github.com/spencergibb/ansible-osx, but my approach rapidly diverged from [battleschool](https://github.com/spencergibb/battleschool) design. During this alpha/beta development phase, I don't aim at keeping this project merge-compatible with `battleschool`, but I'm keeping this topic in mind, and would love to discuss it further.

## Dependencies

* [Ansible](http://ansible.com) 1.8+
* The additional module `mac_pkg` is taken from Spencer Gibb's [battleschool](https://github.com/spencergibb/battleschool/blob/v0.4.0/share/library/mac_pkg)
* Some Ansible core modules are overridden (which implies to use most recent version of Ansible):
  * [`apt_repository`](https://github.com/ansible/ansible-modules-core/pull/190) to be able to add PPA repository for LinuxMint
  * [`command`](https://github.com/ansible/ansible-modules-core/pull/513) to be able to add an idempotence condition for Vagrant plugins setup

## About the name

### TL;DR

`dispansible` aims at brings you more **available** time for doing amazing things, but of course this tool is not **indispensable**, as you can always install your software manually. Mmmh, really?

### Ethymological Roots

* **dispensible**: *obsolete adjective, alternative form of dispensable*
* **[dispensable](http://en.wiktionary.org/wiki/dispensable)**: 
  1. Able to be done without; able to be expended; easily replaced.
  1. Capable of being dispensed; distributable.
  1. ...
* **[disposable](http://www.thefreedictionary.com/disposable)**:
  1. Designed to be disposed of after use
  1. Free for use; available

### Design Philosophy

`dispansible` approach follows the design principles of **[ansible (software)](http://en.wikipedia.org/wiki/Ansible_(software))**:

  1. Minimal in nature. Manage your software installations should not impose additional dependencies on the environment. See the [Dependencies Section]() above.
  1. Highly reliable. The ansible idempotent resource model is applied to prevent side-effects from re-running scripts.
  1. Low learning curve.

Quoting Mitchell Hashimoto in his Book "Vagrant: Up and Running":

> Vagrant lowers development environment setup time, increases development/production parity, and brings the idea of disposable compute resources down to the desktop.

Let's say that `dispansible` aims at lowers *workstation* setup time, increases *operating systems* parity, and brings the idea of disposable computing down to *personal computer setup* (but please don't get me wrong: **don't throw your hardware**, too frequently at least).

## Setup

**WARNING:** During alpha phase the configuration file names and locations are unstable and this documentation might not be up to date.

* Clone via `git` or Download as tarball this repository (or your own fork)
* Install Ansible (latest release is usually recommended). You can use one of the `bootsrap_<platform>` scripts in the `scripts` directory for that purpose.
* Optionally update the following configuration files:
  * [`ansible/galaxy.yml`](https://github.com/dispansible/dispansible/blob/master/ansible/galaxy.yml) to change the external roles that you are depending on. If you change this file, you most probably will need to modify `ansible/playbook.yml` as well.
  * [`settings.yml`](https://github.com/dispansible/dispansible/blob/master/settings.yml) to customize your software configuration and optionally unselect applications (using the `skipped_roles` list)
* Execute `./dispansible all`
* Enjoy a drink (while keeping an eye on your screen, since [the sudo password could be prompted](https://github.com/dispansible/dispansible/issues/2) during the setup procedure)

## Usage

### dispansible tool

Install everything that is enabled in `settings.yml`:

```shell
./dispansible all
```

or

```shell
./dispansible
```

Install specific software:

```shell
./dispansible vagrant,virtualbox
```

### rubber tool

*upcoming...* (including a possible name change)

## Similar Projects

* [Boxen](https://boxen.github.com/) (based on [Puppet](http://puppetlabs.com/))
* [Kitchenplan](http://kitchenplan.github.io/kitchenplan/) (based on [Chef](https://www.chef.io/))
* [battleschool](https://github.com/spencergibb/battleschool) (also based on Ansible and mainly focused on Mac support)
* [OSXC](https://github.com/osxc) is a configuration tool for Mac OS X, also based on Ansible
* [The Munki Project](https://www.munki.org/) is home to several projects that are focused on improving the experience of managing OS X for both the admin and the end user.

