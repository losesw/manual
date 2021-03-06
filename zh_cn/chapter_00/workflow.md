# 工作机制

![Chinese](../resources/chinese.svg) [![English](../resources/english.svg)](https://www.v2ray.com/en/get_started/workflow.html)

## 个人使用

和其它的翻墙工具一样，你需要在一台墙外的 VPS 中配置 V2Ray 服务器，然后在需要翻墙的设备上安装 V2Ray 客户端，然后即可流畅地访问互联网。

![](../resources/direct.svg)

一个 V2Ray 服务器可同时支持多台设备，使用不同的代理协议访问。同时，经过合理的配置，V2Ray 可以识别并区分墙内和墙外的流量，墙内的流量不需要经过墙外绕一圈再回来。

## 多人共享

V2Ray 也支持中转模式，比如你可以在墙内配置一台 V2Ray 服务器，供多人同时使用，每位用户可使用浏览器或手机中自带的代理协议连接这台服务器。而这台 V2Ray 服务器和墙外的另一台服务器相连，以达到翻墙的目的。

![](../resources/relay.svg)

## 工作原理

在配置 V2Ray 之前，不妨先来看一下 V2Ray 的工作原理，以下是单个 V2Ray 进程的内部结构示意图。多个 V2Ray 之间互相独立，互不影响。

![](../resources/internal.svg)

* 需要配置至少一个传入协议（Inbound）和一个传出协议（Outbound）才可以正常工作。[协议列表](../chapter_02/02_protocols.md)见第二章节。
  * 传入协议负责与客户端（如浏览器）通信：
    * 传入协议通常可以配置用户认证，如 ID 和密码等；
    * 传入协议收到数据之后，会交给分发器（Dispatcher）进行分发；
  * 传出协议负责将数据发给服务器，如另一台主机上的 V2Ray。
* 当有多个传出协议时，可以配置路由（Routing）来指定某一类流量由某一个传出协议发出。
  * 路由会在必要时查询 DNS 以获取更多信息来进行判断。

具体的配置格式详见[第二章节](chapter_02/01_overview.md)。
