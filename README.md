# Ansible Role: Android SDK

[![Build Status](https://travis-ci.org/nickpack/ansible-role-android-sdk.svg?branch=master)](https://travis-ci.org/nickpack/ansible-role-android-sdk)

An Ansible Role that installs the Android SDK tools, SDK packages and dependencies on Ubuntu and RedHat based OS'.

## Requirements

A recent version of Ubuntu.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    android_sdk_download_location: https://dl.google.com/android/repository/sdk-tools-linux-4333796.zip

The location to the Android SDK tools package to be downloaded.

    android_sdk_install_location: /opt
    
The location to the Android SDK tools package to be installed.

    android_sdk_install_catalog: android-sdk-linux

The name of catalog  on disk where you'd like to SDK to be installed.

    ubuntu_dependency_packages:
      - "libncurses5"
      - "libstdc++6"
      - "zlib1g"
      - "imagemagick"
      - "expect"
      - "gradle"
      - "ant"
      - "ccache"
      - "autoconf"
      - "automake"
      - "ant"
      - "ccache"
      - "python-dev"
      - "zlibc"

A list of aptitude installable build dependency packages.

    ubuntu_precise_dependency_packages:
      - "libgd2-xpm"
      - "libgphoto2-2"
      - "libsane"
      - "ia32-libs-multiarch"

A list of aptitude installable build dependencies for Ubuntu Precise.

    rh_dependency_packages:
      - expect

A list of yum installable build dependencies for RedHat based OS.

    android_sdk_update_path: true

Whether or not the role should update the PATH in /etc/environment with the relevant android SDK locations

    android_sdk_base_buildtools_version: 28.0.3

The main build tools version from the SDK to use, mainly useful for PATH updates.

    android_sdk_tools_to_install:
      - build-tools;28.0.3
      - platform-tools
      - extras;android;m2repository
      - extras;m2repository;com;android;support;constraint;constraint-layout;1.0.2
    android_sdks_to_install:
      - platforms;android-28


The actual Android SDK packages to install using the SDK manager.

## Example Playbook

    - hosts: appbuild
      vars_files:
        - vars/main.yml
      roles:
        - { role: nickpack.android_sdk }

## License

BSD

## Author Information

This role was created in 2015 by [Nick Pack](https://github.com/nickpack).

## Contributors

* @timdaman - Fixed defect in variable loading
* @ojechev-broadsoft - OSX Support
* @rodrigdav - Fixed bare variables that broke 2.2 compatibility
* @halkeye - Seperated SDK tools, fixed 64bit environment
* @edunham - Fixed 32bit support
* @peterjanes - Added RedHat family support
* @conorsch - Changed conditionals to allow > 14.04 support
* @mateuszmroz93 -  Fixed problem with installation newest version SDK (28.0.0) for CentOS
