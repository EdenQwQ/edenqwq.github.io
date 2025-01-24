---
title: NixOS 治好了我的发行版跳跃症
date: 2025-01-05
tags: [Linux, NixOS, Distro, OS]
---

> 自从我开始用 Linux，就一直在 distro hopping。
> 我用过不下 **20** 个 Linux 发行版，其中大多数都是实装并日用过的。
> **NixOS** 治好了我的发行版跳跃症，让我连想 distro hop 的心思都没有了。
> 因为 NixOS 实在太完美了……

<!-- more -->

## 为什么要安装 NixOS

我用过不下 **20** 个 Linux 发行版，其中大多数都是实装并日用过的。
在最爱折腾的那个时期，我会每隔**几周甚至几天**就换一个发行版，不厌其烦地在各种发行版里复刻自己的配置。
曾经我下定决心，要找到一个非常让我满意的发行版，从此不再 distro hop。
Artix、Void、Fedora 都几乎做到了这点，但最多也就持续了一年不到。

我喜欢通过不断地 distro hop 来体验各种迥异的发行版，发掘它们的内在共性和各自的特色，
但我会更愿意日用某些特定类型的 distro。
现在看来，能让我日用地比较舒服的 distro 需要满足以下条件：

1. 足够 **bleeding edge**：作为一个 professional beta tester，我需要一个能够让我及时获取最新软件包的 distro。
   显然 Arch-based distros、Void、Fedora 在这点上都够格，尤其是 Fedora Rawhide。

2. 足够 **stable**：当然谁都不希望自己的系统时不时出问题。这一点好像和 bleeding edge 有点冲突，比如 Arch 系大多不够 stable。
   所以我在 roll 失败多次后放弃了 Arch，选择了更稳定的 Void 和 Fedora。

3. 足够 **vanilla**：也就是说自带的东西不能太多，因为我喜欢自己折腾，不需要你给我都安排好。
   一开始探索的时候会更喜欢 Zorin、Garuda、Archcraft 等这种~~花里胡哨~~开箱即用的 distro。
   后来逐渐形成了自己的配置体系了，就什么都想自己干了。
   显然一直在说的这三款在这方面都做得不错。

那么目前看来，Void 和 Fedora 完全可以满足我的日用需求，为什么我还要换成 NixOS 呢？

**因为我无聊了。**
上大学后，用来折腾 Linux 的时间少了很多。
曾经我可以花一整天时间浪费在折腾系统配置上，而随着探索的深入，我越来越接近理想的配置，
也越来越被已有的配置固化，于是越来越少的有折腾的欲望。

直到有一天，在我的 Fedora Rawhide（~~不是，真的有人日用 Fedora Rawhide 啊~~）更新了一个 GNOME 版本后，
出现了很多莫名其妙的 bug。And I was like,
"You know what, _I'm done. I'm gonna try **NixOS**._"

为什么是 NixOS？因为我馋了。时不时在 Unixporn 等地方看到 NixOS 用户，感觉 NixOS 是不是已经准备取代 Arch 的 **btw** 地位了。
就像 Gentoo 一样，NixOS 有点被**神化**了，这两个东西对我来说曾是遥不可及的两座大山。
成功[日用 Gentoo](https://eden.is-a.dev/posts/Why-gentoo-so-popular) 后，我克服了对这些被神化的东西的畏惧。
当年第一次接触 NixOS 的时候，我都不知道怎么安装它。
现在可好了，现在 NixOS 都用上 Calamares Installer 了，安装起来比 Arch 都简单。

我有一种预感，NixOS 会重新激发我折腾系统的热情，事实证明这个预感是对的。

<div style="text-align:center;">

![btw I use NixOS](/images/btw-i-use-nixos.png)

</div>

_图源：[https://www.reddit.com/r/NixOS/comments/1dpc0ea/title](https://www.reddit.com/r/NixOS/comments/1dpc0ea/title)_

## NixOS 到底好在哪

到现在为止，我竟然已经用了**一年多**的 NixOS 了。
而且现在我完全没有尝试别的发行版的欲望。因为 NixOS 已经可以满足我的几乎所有需求了。

首先，显然 NixOS 满足了我上面提到的三个日用需求。
要 **bleeding edge** 是吧，那就用 `nixpkgs-unstable` 吧，这玩意在某些层面上比 Fedora Rawhide 还狠。
要 **stable** 是吧，bro，在 NixOS 上你随时可以安装一个最新版本的软件，让它和旧版本共存，体验完觉得不舒服直接删掉就行。
**vanilla** 就更不用说了，NixOS 的 base system 基本上啥都没有，which means everything can be customized as you like.

那么接下来再让我细说一些 NixOS 的独特的好处。

### 无敌的重构

In case you don't know, NixOS 的一切系统配置都使用 **Nix 语言**写的**配置文件**来描述的。
只要你用同样的配置文件，就可以重构出一模一样的系统。
现在还是 **flakes** 的时代，有 lock 机制，完全可以保证系统的一比一重构。
所以如果要装新系统，或者重装系统，要保留系统配置的话留一个配置文件就行了。
拿着配置文件，运行一行命令，马上就可以重构出一个一模一样的系统。

每一次“系统更新”都是一次基于新的配置文件的重构，而不是一次“升级”。
新构建出来的整个系统与旧的整个系统是**完全独立**的，所以随时可以**回滚**到旧的系统。
This is true **atomic upgrade**.

哦我们还有 [**home-manager**](https://github.com/nix-community/home-manager)，可以用 Nix 来管理你的 home 目录，这样你的 home 目录也可以随时重构。
这样就不用折腾什么 dotfile manager 了，
一个文件，一行命令，开箱即用，极其省心。

### 明明很简单

有人说，啊，NixOS 太难了，学不会，配置一个系统还得学一门语言。
我说，那你用别的系统不也得用 shell 命令配置吗？

一开始我也感觉 NixOS 很难，但用了没多久就会发现，NixOS 是把大多数问题变得太**简单**了。
比如说，我想在别的系统里用 fcitx5 来输入中文，我得先装 fcitx5 这个软件包，然后装一些 fcitx5 插件，然后配置一些环境变量。
这好麻烦，每次换系统都得重新配置一遍，记不住环境变量每次都得查。
而 NixOS 里呢，我只需要在配置文件里写：

```nix
i18n.inputMethod = {
  enable = true;
  type = "fcitx5";
  fcitx5.addons = with pkgs; [
    fcitx5-chinese-addons
  ];
  fcitx5.waylandFrontend = true;
};
```

非常的简单明了，看一眼就知道在做什么。不需要你去担心环境变量什么的，NixOS 都会帮你配置好。
这就是**声明式配置**的好处。

配置 Void 的时候，缺少自带的音频服务，得自己装。每次都被 alsa、pulseaudio、pipewire 搞得头大。
NixOS 里，我只需要写 `services.pipewire.enable = true;` 就好了。

这些 options 如此方便，因为定义这些 options 的人已经帮你把背后的复杂配置都处理好了。
要装什么软件包，有什么依赖，配置什么 systemd 服务，定义什么环境变量，很多时候这些都**不需要你来纠结**。

至于 Nix 语言，作为声明式、函数式语言，它的**自解释性**很强，很容易看懂，不需要学也能轻松上手。
至于一些更高级用法，也可以慢慢学，把握它的各种特性，可以写出更优雅的配置。

### 大

NixOS 太**大**了。
这里是指很多个层面。

比如说 [**nixpkgs**](https://github.com/NixOS/nixpkgs)，作为 NixOS 的软件仓库，它的软件包数量是其他任何软件仓库难以比拟的。
见下图，完全是遥遥领先。

<div style="text-align:center;">

![repology graph](/images/repology-graph.png)

</div>

_图源：[https://repology.org/repositories/graphs](https://repology.org/repositories/graphs)_

再比如说，**NixOS 社区**。
NixOS 社区的活跃程度和体量完全不亚于 Arch。
我目前为止碰到的几乎所有问题，基本都可以在 [**NixOS Discourse**](https://discourse.nixos.org) 上找到答案。
nixpkgs 的维护者们也是非常活跃的，否则哪来的这么多软件包和这么多有用的 options。

还有，**NixOS 的生态**。
一旦染上了 NixOS，~~这辈子就有了~~你很可能会想用 Nix 来 **declare everything**。
Luckily，Nix 提供了很多工具来帮你实现这个愿望。
你可以用 home-manager 声明你的 home 目录，可以用 [nixvim](https://github.com/nix-community/nixvim) 声明你的 neovim 配置，
你可以用 nix shell 来管理开发环境……

## 为什么不应该用 NixOS

NixOS 太好了，NixOS 无敌了，都有 NixOS 了，其他系统还有存在的必要吗？为什么不能让所有人都用 NixOS？
我的脑子曾经想过这些问题，但其实还是有很多不应该用 NixOS 的理由。

NixOS 的**学习曲线比较陡**。
学习使用 NixOS、Nix 语言等给我的感受和学习 Vim 差不多，就是一开始感觉好难，后面悟到精髓以后就越学越起劲。
和学 Vim 的感受类似，**用了 NixOS 后的唯一后悔的是没有早点开始用 NixOS**。
但是，其实还是得有一个铺垫的过程，才能更好地上手和理解 NixOS。
如果你刚开始用 Linux，或许不应该马上尝试 NixOS。
你得先用别的 distro 学会 Linux 的基本逻辑才能用 NixOS 用得得心应手。
而且有一说一，配置 NixOS，把已有的配置迁移到 home-manager 等很多事情是很花时间的，说白了就是你得愿意花时间和精力去折腾。
如果你只是想用系统工作、浏览网络、打游戏什么的，NixOS 对你可能也没什么用，反而会浪费你的时间

NixOS **不是 FHS 兼容**的。也就是说，NixOS 的根目录结构和正常的 distro 很不一样，很多正常 distro 上能跑的命令，能运行的程序
在 NixOS 上可能就不能用了。
当然 NixOS 提供了很多应对这些问题的方法，比如 nix shell、buildFHSEnv 等。
你得意识到 NixOS 和正常的 distro 是很不一样的，要有心理准备这些问题可能出现，出现后要**积极尝试解决**。
比如我想创建一个 wayland session，但 NixOS 根本没有 `/usr/share`，就得上网查解决方法，
当然这种基础问题的解决方法一般都能在 NixOS Discourse 上找到。
有些时候实在没办法，或解决办法太麻烦的时候，我就会用 [**distrobox**](https://distrobox.it)。
distrobox 太好了，我直接在容器里跑一个 Fedora，很多问题就解决了。

还有一些很被诟病的问题，比如 NixOS 的文档超级烂，Nix 重构的输出相当难读，NixOS 用着用着磁盘就满了等等。
还是那句话，社区的力量是伟大的，很多问题问社区基本就可以解决了（~~但是文档是真的很烂~~）。
比如 [nh](https://github.com/viperML/nh) 就提供了更易读的重构输出以及简单的磁盘清理方法。
你得相信你遇到的问题，很多人都遇到过，而且很可能已经被解决了。
实在不行你自己去问就行了，社区里的人都很热心。

对于我来说，瑕不掩瑜，NixOS 的优点远远大于缺点，而且很多不足之处都有弥补方式，所以我很满足于 NixOS。
