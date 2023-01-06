---
description: 使用快捷栏中的物件打开面板
---

# 快捷栏物件

要使用快捷栏中的物件打开面板，请添加该项。物件需要具有 "material:"（材料）、"name:"（名称）、"lore:"（Lore）等特性。（确保其缩进按照以下的代码样例。）

可以使用 `example.yml` 样例面板，其在面板文件夹中没有面板时自动生成。

* `stationary`（固定）用于确定快捷栏中物件所在的槽位。取值范围为 `0 - 35`。如果无需将其永久置于快捷栏上，删除该项即可。使用 `0 - 8` 间的值以将物件置于快捷栏中；使用 `9 - 35` 将物件置于玩家背包物品栏中。
* `material`（材料）物件的类型；在此使用材质类型。
* `name`（名称）物件的名称。
* `lore`（Lore）物件的 Lore。如果无需 Lore，删除该项即可。
* `commands`（命令）如果向快捷栏物件中添加命令节，则其将不再自动打开面板。要打开面板，只需向其中添加打开面板的命令即可。

```yaml
open-with-item:
  material: CLOCK
  name: '&a生存面板'
  lore:
  - "&2打开面板"
  - "&2以治愈自身，同时改变游戏模式为生存模式"
  stationary: 4
  commands:
  - open= examplePanel
```

要在使用预加载命令初始化数据的同时使用面板快捷栏物件，可以直接在该物件中添加预加载命令，其将在物件创建之前运行。

```yaml
open-with-item:
  material: CLOCK
  name: '&a服务器选择器'
  lore:
  - '&7您的等级为 %cp-data-playerLevel%'
  pre-load-commands:
  - 'add-data= playerLevel 1'
```

{% hint style="info" %}
如果服务器中所有面板均不包含该功能，不需要的代码就不会运行，以加快服务器运行速度。
{% endhint %}
