---
title: Worm, a new floating window manager written in Rust
date: 2021-10-30
tags: [Linux, Rust, WM]
---

## Introduction

[Worm](https://github.com/codic12/worm) is a brand new floating window manager
for X11 written in Rust by [codic12](https://github.com/codic12).

It's still in an early testing stage, but it's an intriguing wm afterall. While
worm is currently a floating window manager, it's planned to gain tiling
ability. Worm uses tags instead of workspaces, which is a concept borrowed from
DWM. A tag can contain different windows, and a window can belong to different
tags. However, currently worm does not support having more than one tag on
a window or viewing more than on tag at a time.

<!-- more -->

## Installation

### Build from source

```bash
# Build with cargo git clone https://github.com/codic12/worm cd worm
cargo build --release

# After building, copy the binary files to your PATH
sudo cp target/release/{worm,wormc} /usr/bin/

# If you are using a display manager, copy the desktop entry file to the
xsessions directory 
sudo cp assets/worm.desktop /usr/share/xsessions/
```

### Use AUR package

```
yay -S worm-git
```

## Configuration

### Autostart

Worm will execute the file '.config/worm/autostart' on startup, which is
supposed to be an executable shell script. An example is
[here](https://github.com/EdenQwQ/WormConfig/blob/main/autostart).

### Hotkey

Since worm does not have a build-in keyboard mapper, a hotkey daemon like
[sxhkd](https://github.com/baskerville/sxhkd) is needed. An example sxhkdrc
is [here](https://github.com/EdenQwQ/WormConfig/blob/main/sxhkdrc).

