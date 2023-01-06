---
description: 常见问题一览
---

# FAQ

## 🤔某些命令只显示 CommandPanels 帮助？

如果服务器上的命令只显示 CommandPanels 命令列表，而不是正常运行，请继续阅读。发生该种情况的原因是 CommandPanels 已经自动注册该命令，将该命令设置为打开面板。

要在面板上更改这一点，添加以下代码，以禁用自动注册命令；不过已经注册的命令可能还在 `commands.yml` 里。编辑 `commands.yml`，删除需要修复的命令，比如 `/kit`。然后输入 `/cpr` 并重启服务器。（`command.yml` 文件在服务器根目录下，与 CommandPanels 无关。）

```
panelType:
- nocommandregister
```

## 🤔如何正确更新 CommandPanels？

​一些小更新可能并不会发布至 Spigot。要将 CommandPanels 更新至最新版本，只需输入命令 `/cpv latest`，然后重启服务器，从而强制下载最新版本并安装至服务器。

## 🤔如何实现通过点击物件关闭面板？

​要使用物件关闭面板，可以添加命令 `commandpanelclose` 或 `cpc` 至物件命令。

## 🤔打开面板时聊天框提示出现错误，如何修复？

​使用命令 `/cpd` 以启用调试模式。在下一次尝试打开面板时，详细报错将会输出至服务器控制台。如果你看不懂报错，可以在 Discord 服务器中联系开发者或其他成员。

## 🤔CommandPanels 导致服务器卡顿，如何修复？

​要排除故障、消除服务器卡顿，以下是可供尝试的简单步骤。

* 如果有面板使用快捷栏物品（打开面板物品），暂时删除，并测试 TPS 是否更高。
* 如果完全不用面板方块（打开面板的方块 `/cpb`），在 `config.yml` 中将 `panel-blocks` 项设置为 `false`。
* 如果面板打开时均没有动画或动态更新（例如面板打开时物件改变），可在 `config.yml` 中将 `refresh-panels` 项设置为 `false`。如果需要刷新，考虑将 `refresh-delay` 项设置得更高，比如40 或 60（单位：游戏刻）。 ​

## 🤔没找到答案？

如果 FAQ 中并没有你要的答案，可以查阅该页面，其包含了所有的现有问题，或正在解决，或已经解决。https://github.com/rockyhawk64/CommandPanels/issues

以及，还有一个寻求建议的简单方法：在 Discord 服务器中与我们取得联系。
