---
author: Ygbs
date: 2025-05-17
category:
  - Minecraft
tag:
  - Geyser
  - Server
sticky: 1
---

# Geyser 的安装和使用

通过配置 Geyser 提供基岩版支持。

<!-- 更多 -->

# 这是什么

[Geyser](https://geysermc.org/) 是一个提供基岩版到 Java 版兼容的服务端插件，也可以独立作为代理运行。如果配合 Floodgate 使用，则不需要正版账号即可登录服务器。

它的主要功能是让基岩版能够加入 Java 版服务器，如果你想要让 Java 版加入基岩版服务器，可以使用 [ViaBedrock](https://github.com/RaphiMC/ViaBedrock)，它被包含于 ViaProxy 和 ViaFabricPlus 中，它们为 ViaBedrock 提供了图形化配置。

Geyser 分为多个版本，如 `Geyser-Spigot`、`Geyser-Velocity` 和 `Geyser-Standalone` 等，可以根据使用场景和具体情况选择。

## 安装

在安装之前，至少需要 [安装 Java](https://nitwikit.8aka.org/preparation/java/choose-and-download-and-install-java)。如果要在现有的服务端或代理上安装，则则还应该确保服务端或代理可以正常运行。

在[官网下载页面](https://geysermc.org/download)下载 Geyser 和 Floodgate（可选），注意不同的版本适用于不同的服务端和环境。选择对应版本的 Geyser 和 Floodgate 下载，完成后将它们放置于 `plugins` 或者 `mods` 文件夹中，重启服务器生效。对于独立版本的 Geyser（Geyser-Standalone），使用命令在终端中启动即可：

```bash
java -jar Geyser-Standalone.jar
```

不论是什么版本的 Geyser 和 Floodgate，它们的配置文件都是一样的。在代理上安装时，Geyser 只需在代理上安装，而 Floodgate 应该在代理和它所有后端服务器上安装，并且将代理上 `plugins/floodgate/key.pem` 文件复制到后端服务器的 Floodgate 文件夹，即可完成安装。在安装完成后，需重启代理及全部后端服务器。

## 配置

Geyser 的 `config.yml` 文件可以完成大部分配置，其中包含服务器名称等配置。在默认情况下，Geyser 会在 `19132` 端口上监听，此时使用基岩版客户端连接对应的服务器地址即可。一般而言这样做就足以让基岩版客户端加入 Java 版服务器，如果不行则应该检查服务器防火墙配置。

特别地，在旧版本服务器上，Geyser 需要配合 [ViaVersion](https://ci.viaversion.com/) 才能正常使用，并且在更新 Geyser 的同时也要更新 ViaVersion，否则基岩版玩家可能在游戏中遇到一些问题。

## 账户

如果一个基岩版玩家也拥有 Java 正版账户，那么他可以在 [Global Linking](https://link.geysermc.org/) 上绑定他的基岩版和 Java 版账户，这样不论是基岩版还是 Java 版登录时他都会在服务器上以同一个身份登录。但这样做会在关联账户后丢失基岩版账户在服务器上的游戏进度，例如背包和经验全部丢失，但 Java 版账户不受影响。

## 插件

Geyser 本身缺少一些功能，如果使用一些扩展插件，那么就可以提升基岩版玩家的体验。

### [BedrockPlayerSupport](https://modrinth.com/plugin/bedrockplayersupport)

- 为基岩版玩家提供 TPA、Home 等服务器功能的基岩版菜单。

### [GeyserExtras](https://modrinth.com/plugin/geyserextras)

- 扩展 Geyser 的功能。

### [KcLoginGui](https://modrinth.com/plugin/kclogingui)

- 提供 AuthMe 的基岩版菜单。

还有更多插件可以改善基岩版体验，在此不一一例举。
