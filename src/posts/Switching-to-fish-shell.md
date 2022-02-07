---
title: Switching to fish shell
date: 2021-11-13
tags: Linux
---

A philosopher named Luke Smith once said,
> Setting fish as your default shell is like setting python as your default shell.

So.. Why not? Let's try fish.

<!-- more -->

There are many reasons I can think of for giving fish a try:

* Fish loads faster compared to zsh with oh-my-zsh 

* Fish has many built-in functions while zsh needs extensions to use the same
functions 

* Fish is way more user-friendly with its simple syntax and web based
configuration

The web based configuration is too easy to be explained here, so let's talk
about something else that might be helpful.

### 1. vimode


Fish has built-in vimode that allows you to edit the command input with vi
keybindings. To enable vimode, simply run <code>fish_vi_key_bindings</code> in
fish. 'Normally' we are in insert mode, and press ESC to enter 'normal' mode,
just as expected XD.

### 2. pywal support

Fish do not have a built-in pywal support and pywal do not have a official fish
support :). But with pywal's **template** feature, it's not hard to achieve
this.

Check [this
comment](https://github.com/dylanaraps/pywal/issues/384#issuecomment-505801129)
under a pywal issue.

```bash
vim ~/.config/wal/templates/colors.fish
```

Add lines in the file that look like <code>set fish_color_normal
{foreground.strip}</code>. Source the output file in your config.fish.
```bash
source ~/.cache/wal/colors.fish
```
