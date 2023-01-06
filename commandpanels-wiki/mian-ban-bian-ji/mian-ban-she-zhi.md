---
description: 置于面板根目录下的设置。
---

# 面板设置

## **面板权限**

打开面板需要的权限。填 `default` 以使所有人都有权限；如果填 `creative`，权限节点即为 `commandpanel.panel.creative`。

```
perm: default
```

## **面板行数**

面板的行高度。填 3 即为小箱子，填 6 即为大箱子。 如果想要特殊的 GUI（工作台、熔炉、漏斗之类的），你需要查阅 [物品栏类型](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/event/inventory/InventoryType.html)。

不过也不是所有类型都 OK，还请自行尝试。

```
# 标准一行 GUI
rows: 1

# 特殊 GUI（漏斗）
rows: HOPPER
```

## **面板标题**

面板顶部的标题。支持 Placeholder 与颜色代码。注意：对于 Minecraft 的某些旧版本，标题的长度限制可能更短；所以如果标题被截断了，还请缩短一下标题。

```
title: '&8样例 GUI'
```

## **面板类型**

用于确定面板类型。以下是支持的类型：

* `static`（静态）：面板打开后，禁用物件变化；例如，动画不会变化。
* `nocommand`（无命令）：禁止以 `/cp <面板名>` 打开面板。
* `nocommandregister`（无命令注册）：禁止面板自动注册其自定义命令至 `commands.yml` 文件。
* `unmovable`（不可移动）：面板打开时，阻止玩家移动自身物品栏中的物品。
* `unclosable`（不可关闭）：阻止玩家关闭面板。需要在面板中添加带 `cpc` 命令标签的物件以关闭面板。

```
panelType:
- static
- nocommand
- nocommandregister
- unmovable
- unclosable
```

## **面板消息**

将其加入物件以选择自定义消息。以下样例显示了不同的可加入物件的自定义信息。

```
custom-messages:
  player-input:
  - '&b在该自定义消息下输入文本！'
  input: '&c自定义最大字符数消息！' # 用于玩家输入
  perms: '&c自定义无权限消息！' # 没有点击物件的权限
```

## **刷新面板**

添加该项以覆盖 `config.yml` 中的 `refresh-panels` 项，为该面板单独设置特定值。

```
refresh-delay: 1
```

## **面板音效**

使用该项，以在玩家打开面板时播放音效。不支持 Minecraft 1.8。 可以播放音乐，关闭面板时会自动停止播放。

```
sound-on-open: BLOCK_NOTE_BLOCK_PLING
```

## **面板之外的命令**

这些是玩家点击面板之外时执行的命令。"面板之外"即 Minecraft GUI 区域四周的空区域。

```
outside-commands:
- 'placeholder= [name:您的名字是：]'
- 'msg= %cp-name% %cp-player-name%'
```

## **面板打开与关闭的命令**

面板打开或关闭时执行的命令。执行顺序从上至下。 `Pre-load`（预加载命令）于面板打开前执行（例如在面板加载和设置物件名称前），`commands-on-open`（打开时命令）于此后执行。 建议使用 `commands-on-open`，仅在为面板 Placeholder 设定数值等操作时使用 `Pre-load`。

```
pre-load-commands:
- 'placeholder= [text:您的名字是：]'
- 'msg= %cp-text% %cp-player-name%'
```

```
commands-on-open:
- 'msg= 面板打开!'
- 'gamemode creative'
```

```
commands-on-close:
- 'msg= Panel Closed!'
- 'gamemode creative'
```

## **自定义物件**

在面板中可添加自定义物件，将用于各种功能，例如物品支付门槛以及使用 `setitem=` 时。 自定义物件的语法与面板中的常规物件相同，参见以下样例片段。 在该样例中，有三个样例物件。要自定义物件，参见"物件设置"页。

```
custom-item:
  example1:
    material: AIR
  example2:
    material: DIAMOND
    name: 'A custom name for the diamond'
  itemThree:
    material: GLOWSTONE
    name: 'Glow Boy'
    lore:
    - 'This is the lore!'
    enchanted: true
    stack: 34    
```

## **禁用或启用世界**

`disabled-worlds`（世界黑名单）禁止处于特定世界的玩家访问面板。如果该面板有快捷栏物件，且使用了 Multiverse-Inventories 之类的插件实现了不同世界不同背包的功能，该快捷栏物件将不会在禁用世界中出现。 也可以使用 `enabled-worlds`（世界白名单），只在列表中的世界启用面板。

```
disabled-worlds:
- world_nether
- world_the_end
#OR
enabled-worlds:
- world
```

## **空物件槽**

该物件将自动填充于面板中无物件的空位。 如果想用自定义物件，输入面板中自定义物件的名称。

```
empty: STAINED_GLASS_PANE
# 或者
empty: custom_item_name
```

将其设置为颜色 ID。如果不需要，设置为 0。（Minecraft 1.12 及以下版本）

```
emptyID: '15'
```
