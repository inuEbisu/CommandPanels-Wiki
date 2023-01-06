---
description: 无论是否为自定义物件，都有这些设置项。
---

# 物件设置

## **材料**

物件的材料。

```
# 常规材料
material: IRON_INGOT

# 自定义标签材料
material: cps= self
```

要使用自定义材料，请使用以下的材料标签之一。

| 标签                   | 描述                                                                                                                                                                                                                                                                                                                    |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| cps=                 | <p>用于头颅。 使用 <code>cps= self</code> 表示玩家自己的头颅。</p><ul><li>使用 https://minecraft-heads.com/custom-heads 找一个很奈斯的自定义头颅吧</li><li>查找头颅时滚动到页面底部，会看到一个名为 "Other"（其他）的部分，你可以复制名为 "Value:"（值：）的代码。</li><li>可用 <code>cps= &#x3C;值></code> 来使用该功能。</li></ul><p>也可以使用 <code>cps= &#x3C;用户名></code> 表示指定玩家的头颅。注意：这可能比上述方法效果差一点儿。</p> |
| cpi=                 | 用于面板自定义物件。只需使用 `cpi= <自定义物件>` 便可更改其材料。查阅"面板设置"页并导航至自定义物件，以获取更多关于其制作方法的信息。                                                                                                                                                                                                                                             |
| hdb=                 | 使用 Head Database（头颅数据库）将头颅加入面板。只需在数据库中找到头颅，并获取其编号。 例如：`hdb= <编号>`                                                                                                                                                                                                                                                     |
| mmo=                 | 使用 MMOItems 在面板槽位中制作物件。只需使用以下的材料模板：`mmo= <物件类型> <物件id>`                                                                                                                                                                                                                                                               |
| book=                | 创建一个“可写的书”物件。用法：`book= <作者>`；无需填写确切的用户名。在物件中添加一个部分，其和 Lore 相似，不过叫做 Write（写）；其将成为书的内容。                                                                                                                                                                                                                                 |
| cui=                 | 需要插件 Custom Items。要在面板中使用来自 Custom Items 的物件，使用：`cui= <物件名>`                                                                                                                                                                                                                                                          |
| %cp-player-online-1% | 数字 1 可以改为任何数值。检查服务器槽位，并找到位于该槽位的玩家。如果只有你在线，并且数值为 1，将显示为你自己。如果数值设置为 2，将显示为离线，毕竟你是唯一一个在线的。                                                                                                                                                                                                                               |

## **物件类型**

为物件设置特殊类型。

* `placeable`（可放置）：允许玩家拿走该物件，并在该槽位放置其他物件。
* `noAttributes`（无属性）：阻止物件属性自动隐藏。
* `noNBT`（无NBT）：删除面板中物件的 NBT 属性；如果从 GUI 中取出物件，NBT 又会回来。对于面板自定义物件用处很大：面板关闭时，物件不会被删除。
* `dropItem`（掉落物品）：关闭面板时，在当前槽位的物品将会掉落。与 `placeable` 一同使用时功能强大。
* `removeItem`（删除物品）：关闭面板时，在当前槽位的物品将会回到玩家的物品栏中。

```
itemType:
- placeable
- noAttributes
- noNBT
- dropItem
- removeItem
```

## **物件 ID**

材料ID。写 0 就好，除非你知道你在干什么，比如想整点彩色羊毛之类的物件啥的。 该项仅限 Minecraft 旧版。

```
ID: '0'
```

## **物件名称**

物件的名称。如果不需要名称（即空名称），写 `'&f'` 即可。

```
name: '&a生存'
```

## **物件堆叠组**

物件堆叠组中物品的数量。该项不存在时不堆叠（为 1）。

```
stack: 1
```

## **附魔**

设置为 `true` 以附魔物件。删除该项以设置为 `false`。可以添加特定的附魔，例如：`enchanted: KNOCKBACK 3`。

```
enchanted: true
```

列举多项附魔也 OK，样例如下：

```
enchanted:
- KNOCKBACK 3
- SHARPNESS 4
```

## **物件 NBT 数据**

为物件添加各种 NBT 数据。NBT 标签需要键值对：一个键(标题)与一个值。在下方例子中，搜索 NBT 标签 `example` 将输出 `test`。

```
nbt:
  example: test
```

## **自定义模型数据**

可为物件随意设置自定义模型数据。

```
customdata: 1000001
```

## **物件耐久**

设置物件的耐久损失量。在非旧版 Minecraft 中，将其设置为 `-1` 以使其无法破坏。

```
damage: 10
```

## **盔甲颜色**

改变皮革盔甲的颜色。 可以使用 RGB 颜色，也可以使用在 Spigot API 中给定的颜色。

```
leatherarmor: 136,0,255
# 或
leatherarmor: CYAN
```

## **药水效果**

在物件中使用下述方法以更改药水效果。 要查阅各种药水名称，在 Spigot API 中找到 PotionType。对于所有可以有药水效果的物件均可以使用(例如：药箭)。 `[extended?]` 处应设置为 `true` 或 `false`，取决于药水效果是否为延长版本。 `[upgraded?]` 处应设置为 `true` 或 `false`，取决于药水效果是否为增强版本。 （旧版 Minecraft 不这么玩儿，而是使用物品 ID）

```
potion: HEAL [extended?] [upgraded?]
```

## **物件 Lore**

这就是物件的 Lore，想写多少行都可以。也可以使用换行符  换行。

```
lore:
- '&2治疗自身'
- '&2同时改变游戏模式为生存模式'
```

## **物件命令**

玩家点击物件时执行的命令。从上至下按顺序执行；如果玩家没有权限，命令将不能执行。 命令节中可以使用面板命令标签！

```
commands:
- heal
- gamemode survival
```

## **物件刷新命令**

刷新命令将于面板物件刷新时执行。如果命令在 Has 节下，则仅在通过 Has 节后执行。

```
refresh-commands:
- "cpc"
- "msg= 太久未操作，自动关闭！"
```

## **复制物件**

要在面板上复制物件至其他槽，可使用 `duplicate` 方法，只需在物件上添加下述内容。 注意，仅为外观复制，不会复制物件上的命令。

下面的例子将复制物件到槽位 0 至 9、13、17 至 27。

```
duplicate: "0-9,13,17-27"
```