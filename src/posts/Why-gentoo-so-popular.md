---
title: 我与Gentoo——为什么Gentoo如此吸引Linux爱好者
date: 2023-7-17
tags: [Linux, Gentoo, Distro, OS]
---

> <@insomnia> it only takes three commands to install Gentoo
>
> <@insomnia> `cfdisk /dev/hda && mkfs.xfs /dev/hda1 && mount /dev/hda1 /mnt/gentoo/ && chroot /mnt/gentoo/ && env-update && . /etc/profile && emerge sync && cd /usr/portage && scripts/bootsrap.sh && emerge system && emerge vim && vi /etc/fstab && emerge gentoo-dev-sources && cd /usr/src/linux && make menuconfig && make install modules_install && emerge gnome mozilla-firefox openoffice && emerge grub && cp /boot/grub/grub.conf.sample /boot/grub/grub.conf && vi /boot/grub/grub.conf && grub && init 6`
>
> <@insomnia> that’s the first one

<!-- more -->

如果你装过Gentoo，你肯定会马上看出来引文中的命令是**不太对**的。
而且当你看到`/usr/src/linux`以及`emerge gnome mozilla-firefox openoffice`，你就会知道如果这个命令真的能跑的话，它能跑多久（一整天？难说……）。

Gentoo在Linux及自由软件爱好者群体中已经成为了一个梗，而Gentoo的meme化很大程度上是因为Gentoo闻名遐迩（~~臭名昭著~~）的安装之**困难和费时**。

![random gentoo meme](../images/3a4yepx08v4b1.jpg)
*才4小时？*

## 我与Gentoo

我最开始接触到Gentoo，是通过distrowatch.com上的随机distro随机到的。
简单浏览了Gentoo的官网后，我得出了一个结论：**为时过早**。
当年的我还是一个安于使用Ubuntu-based distro的单纯孩子，哪里受得了Gentoo官网的冲击（~~它甚至没有放截图！~~）。

然而，随着我对Linux的了解逐渐深入，我愈发意识到自己对Gentoo**耿耿于怀**。
终于我在某个无聊的周末尝试装了Gentoo。
当时并没有直接按照amd64 handbook来，而是照着[这个视频](https://www.youtube.com/watch?v=J7W9MItUSGw)来。
由于使用了现有的已经配置好的系统，在配置网络和分配硬盘上节省了很多时间。
做好准备后就跟着handbook一步步来，最后还尝试了编译内核，总共也就用了6小时吧……

初次安装后没过几天，我就由于难以忍受各种问题而卸掉了Gentoo。
初次使用Gentoo的经历并不是很愉快，然而这并没有打消我**日用Gentoo的“梦想”**。

接下来的很长一段时间，我都对Gentoo怀有**极其强烈的兴趣**，并在自己没有日用Gentoo的经验的情况下疯狂向别人安利Gentoo。
终于在这个暑假，我又~~因为过于无聊而~~手痒了，再次打开Gentoo amd64 handbook，开始安装这个我**梦想中的distro**。
这次我已经熟门熟路（~~然而还是跳过了编译内核选择了kernel-bin~~），竟然在两小时内就完成了安装。
现在是我将Gentoo作为主系统日用的第五天，我已经深深爱上了这个**特别而奇妙**的发行版。

![gentoo rui](../images/9zkccddff81b1.png)
*随处可见的Gentoo*

## Why Gentoo？

所以为什么我会对Gentoo这么感兴趣呢？或者说，为什么Gentoo如此吸引Linux爱好者呢？
我想这可以从很多层面展开讨论。

### Philosophy

> Our tools should be a joy to use, and should help the user to appreciate the richness of the Linux and free software community, and the **flexibility** of free software. This is only possible when the tool is designed to **reflect and transmit the will of the user**, and leave the possibilities open as to the final form of the raw materials (the source code.) If the tool forces the user to do things a particular way, then the tool is working against, rather than for, the user. 

或许大多初次接触Gentoo的人都会被它的哲学思想所吸引。
Linux爱好者使用Linux而非Windows、MacOS，大概很大程度上是为了“掌控自己的电脑”，而不是让电脑掌控自己。
类似的，我们使用FOSS，也很大程度上是为了“**掌控自己的软件**”。

但事实上，在大多数系统上，我们只能**选择我们的软件**。
因为大多数发行版的包管理程序提供的是**二进制文件**，这让我们难以对软件本体进行定制。
这样的坏处是，为了使得软件可以供大多数用户使用，这些发行版提供的软件包可能包含很多对个体用户来说**冗余的功能**。
比如一个提供图形界面的软件可能同时带有GNOME和KDE支持，而用户可能甚至不使用桌面环境。
再比如大多数发行版的自带内核很可能有非常多**冗余的硬件驱动**。

Gentoo**基于源代码的软件包管理方式**使得用户天然的可以对软件本身进行高度定制。
当然，最高度的定制应当是自己下载源代码并自己编译，但这样未免非常麻烦，而且需要对相应的源代码有一定的了解。
Gentoo则通过包管理程序**portage**和**USE flags**提供了高度**自动化、全局化**的软件定制方法。
这使得我们可以更自由也更方便地掌控我们的软件：
想要完全抛弃X，改用Wayland？只需要在`make.conf`中的设置全局USE flag `USE="-X wayland"`；
想要针对自己的显卡对所有软件进行优化？只需要设置显卡选项`VIDEO_CARDS=nvidia`……

Gentoo的哲学**并非让用户感到困难**，而是尽可能**让用户感到舒适**。
也就是，在提供尽可能多的定制空间的同时，保证这些定制的便捷。

当然实际使用Gentoo后，才会发现Gentoo的包管理和各种特有的配置方式具有**较陡的学习曲线**。
这就是一个Linux语境下常见的trade-off，其实学习使用Gentoo和学习使用vim、make、shell scripting等是同一个道理，都是**用短时间较多的精力得到长时间更舒适的体验**。

### 洁癖福音

很多深入了解过Linux的人会走到这样一个阶段：
突然听说或意识到systemd、GNOME、glibc等这些常用的东西非常**臃肿**，于是竭力想要避开这些所谓臃肿的东西。
于是这些人（比如说我）就会开始使用各种Window manager来替代庞大的桌面环境，
寻找不用systemd作为init system的发行版（比如artix、void等），尝试用musl替代glibc，用busybox替代GNU coreutils……

伴随着对臃肿的排斥，还有**对免费开源软件的高度推崇**和对收费专利软件的极端厌恶。

这样的阶段，我愿称之为**软件洁癖**。
虽然现在我佛了很多，但或多或少还保留着这样的洁癖。
而Gentoo一定会是软件洁癖患者的福音。

从安装阶段开始，Gentoo就允许用户指定**profile**。
如果不想要庞大的桌面环境，选择不带有GNOME或KDE的profile就行。
如果不想要systemd，选择不带有systemd的profile就行。
不想要glibc，选择不带有glibc的profile就行……
即使安装完成，用户也可以随时切换profile，切换后只需要一次全面系统更新就可以。

Gentoo坚持**无必要，不自带**的原则，将大多数的选择权给到了用户。
比较典型的例子是，Gentoo是不自带`sudo`的。
Gentoo贴心地考虑了觉得`sudo`也实在臃肿，必须要用`doas`的人（比如我）。

Gentoo的包管理机制也可以让洁癖**非常省心**。
不想要什么东西，直接在全局USE flag里禁用它就好了。
只想用开源证书的软件包，直接在`package.license`里指定就好了。

### 中庸之道

Gentoo把大多数选择权交给用户，所以提供了很多的选择。
某些**极端的**发行版会把一些“好东西” **强行塞给用户**，这反而让用户失去了选择权。
比如Alpine Linux、GNU guix等都是这类。
Gentoo从来不是极端的，而是**中庸的**。
也就是说，Gentoo即能满足传统用户需求，也能满足各种洁癖患者的需求。

Gentoo会告诉你**OpenRC**是个很好用很轻量的init system，但它也允许你使用systemd。
Gentoo会推荐你定制自己的内核来充分开发电脑性能，但它也允许你使用kernel-bin来**节省时间**和保持更新。

### 虽不能至，心向往之

无可非议的一点是，Gentoo的安装和使用的确比“正常的”发行版要困难许多。
然而对于很多Linux爱好者，我们并不害怕困难，我们甚至**乐于迎接调整，突破困难**。

刚认识到vim的时候，我感觉这个小小的编辑器简直颠覆我的世界观。
我知道学习它肯定会**要花费很多精力**，但我也知道学会了它能为我带来巨大的**效率提升**（~~还能装逼~~）。
于是我尝试去学习它的基本概念，并通过实践和解决实践中遇到的问题不断积累经验，最终基本掌握了它。

这样的**学习和解决问题的过程**让我感到**由衷的快乐**。

Gentoo对我来说也是这样的存在，它是很大的挑战，所以也是很大的**快乐源泉**。

>! 为什么听起来这么像m

另一方面，正是因为Gentoo对于一个newbie来说如此“高深莫测”，所以会激起ta强烈的**好奇心以及敬畏感**。
这样的好奇心让我愿意去探索Gentoo这座大山，感叹它的奇崛，享受**登高望远**。
这样的敬畏心又让我深知自己能力之渺小，让我在这座大山乃至更多更高的大山下**保持谦卑**。

总之，Gentoo努力**让用户得到最舒服的体验**，这样的**哲学宗旨**让它成为了**洁癖的福音**，
也让无数日用过它、安装过它、了解过它、听说过它的人**心向往之**。
