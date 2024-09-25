---
title: 'Guide: Install developer tools on macOS'
toc: true
---

<script>
$().ready(function() {
    var elems = document.getElementsByClassName('language-console');
    for (const elem of elems) elem.className += ' console-mac';
});
</script>

These are the instructions for installing the development tools on macOS. We peppered the installation instructions with <i class="fa fa-check-square-o fa-lg"></i> __Check__ steps that confirm your progress through the steps. Use each to validate a step before moving on.  If you hit a snag, stop and reach out (forum, office hours) and we can help you out!

## Install Xcode

To ease the installation process, we are using Homebrew.
[Homebrew](http://brew.sh/) is a popular [package
manager](https://en.wikipedia.org/wiki/Package_manager) for OS X.

If you already use Homebrew, skip to the next section; otherwise follow these steps.

- Homebrew requires the Xcode command line tools. Install these by running the command below.
    ```console
    $ xcode-select --install
    ```

- Install Homebrew by running the command below.
    ```console
    $ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
    ```

{% include checkstep.html content="confirm Homebrew installation" %}
```console
$ brew -v
Homebrew 4.2.0
```
Fine if your version number is newer.

## Install riscv-unknown-elf toolchain
We use a cross-compiler toolchain to compile programs for the Mango Pi.

- Install our custom brew formula containing the cross-compile tools.
    ```console
    $ brew install cs107e/cs107e/riscv-gnu-toolchain-13
    ```

{% include checkstep.html content="confirm compiler" %}
```console?prompt=$
$ brew info riscv-gnu-toolchain-13
==> cs107e/cs107e/riscv-gnu-toolchain-13: stable 13-2024q1-cs107e
Pre-built RISC-V GNU toolchain for CS107e

$ riscv64-unknown-elf-gcc --version
riscv64-unknown-elf-gcc (gc891d8dc2-dirty) 13.2.0
Copyright (C) 2023 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

## Install xfel
Xfel was installed as part of the toolchain installation. You can confirm that it is installed by running the command below.

{% include checkstep.html content="confirm xfel" %}

```console
$ xfel
xfel(v1.3.2) - https://github.com/xboot/xfel
usage:
    xfel version                            - Show chip version
    xfel hexdump address length             - Dumps memory region in hex
    xfel dump address length                - Binary memory dump to stdout
    ...
```


## Installation complete

Nice job! Head back to the [main installation guide](../devtools) to do one last set of checks.