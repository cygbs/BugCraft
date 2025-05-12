---
date: 2024-09-11
category:
  - Minecraft
tag:
  - Minecraft
sticky: 1
---

# 正确地为 Minecraft 服务器配置 SRV 解析

配置 SRV 的方法。

<!-- 更多 -->

## 引言

很多时候我们没有办法为 Minecraft 服务器使用 `25565` 端口，因为这个端口可能已被占用，或者由于使用 FRP 服务等。再譬如说，我们的一个域名（例如 `bugcraft.org`）已经被 Web 服务占用了，而我们不想使用二级域名。在这种情况下，使用 SRV 服务器解析服务器记录就是一种很好的选择。

## 步骤

### 前置条件

我们首先需要一台 Minecraft 服务器、一个域名才能进行接下来的步骤。这台 Minecraft 服务器的地址可以是域名、IPv4 或者 IPv6。如果是 IPv4 和 IPv6 地址，请先为它们设置 A 记录、AAAA 记录（如果是动态 IP，请额外配置 DDNS）。通过这个步骤，可以获得一个二级域名，它指向我们的 Minecraft 服务器所在的 IP。

### 具体操作

接下来，我们假设服务器的地址是 `play.bugcraft.org`，端口是 25575，显然我们需要连接 `play.bugcraft.org:25575` 才能加入服务器。接下来，打开您的 DNS 管理页面，添加一个 SRV 解析记录。

假如我们想要将这个域名而不是它的子域名直接指向我们的 Minecraft 服务器，那么在名称处填写 `_minecraft._tcp` 。如果想要将子域名指向 Minecraft 服务器，将 `_minecraft._tcp` 修改为 `_minecraft._tcp.example` 即可。这样，如果主域名是 `bugcraft.org`，那么 `example.bugcraft.org` 届时将可以连接服务器。

优先级和权重都可以填写「0」。TTL 保持默认。端口填写目标服务器上对应的 MInecraft 监听端口。目标项直接填写我们之前设置好的域名。最后点击「保存」按钮，随后稍等一下，我们的解析记录即可生效。打开 MInecraft Java 版客户端，填入 SRV 的解析域名（如果之前设置的是子域名，直接填写子域名）。

## 效果

恭喜你！这个时候便已经可以通过 SRV 解析记录来连接服务器了。这为主域名已有 A 或 AAAA 解析记录的服务器或者非 25565 端口的服务器提供了一个更好的选择。需要注意的是，该方法仅限于 Minecraft Java 版本，基岩版仅极少版本支持，且需要更复杂的方法来完成。
