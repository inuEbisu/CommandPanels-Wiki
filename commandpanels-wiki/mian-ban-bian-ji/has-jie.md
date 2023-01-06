---
description: 以下是物件中有需求的各种节，以确定应该显示或使用哪一个物件。
---

# Has 节

## **如何使用节**

通过使用页面底部的节，可以很容易地将其添加至物件。例如，请看下述脚本，其有一个物件。

```
'20': # 节 1
  material: RED_WOOL
  name: "您的用户名不是 RockyHawk"
  has0: # 节 2
    value0: RockyHawk
    compare0: '%cp-player-name%'
    material: LIME_WOOL
    name: "您的用户名是 RockyHawk"
    has0: # 节 3
      value0: '%cp-player-name% HASPERM'
      compare0: gamemode.creative
      material: BLACK_WOOL
      name: "您的用户名是 RockyHawk，您可以执行 /gamemode"
    has1: # 节 4
      value0: '%cp-player-name% HASPERM'
      compare0: essentials.fly
      material: BLACK_WOOL
      name: "您的用户名是 RockyHawk，您可以执行 /fly"
```

## **不同的节**

上方的物件有一个默认节1(缺省物件)，为红色羊毛；节 1 里塞了一个节 2 ，节 2 里面又塞了节 3 和节 4。 如你所见，节 2 只在玩家名称为 RockyHawk 时显示，否则显示节 1 的红色羊毛。仅当玩家名为 RockyHawk 时，才会检查节 2 中的节 3 与节 4。 需要在一个节中使用常规的物件设置，例如 `material`（材料），因为如果该节需要使用，则需具有一个可以正常创建的物件。

## **同一位置的多个节**

你可能注意到了，在上面的节 2 中有两个节。在同一个节中不能有重名的节，所以需要给每一个节编上不同的号，比如 has0 和 has1。如果两个节均可使用，则优先使用编号小的。

## **输出值**

如果你想反着来，比如在玩家没有权限时启用某个节，只需在节中加一行 `output: false`，就会取得相反的效果。

{% hint style="info" %}
任何只包含物件节而没有外部内容的物件将无法正常使用。在任何节之外总要有一个默认的缺省材料。
{% endhint %}

## **节参数**

### **OR 或**

要比较两个不同值，可以使用 `OR` 操作符。二者中只有其一等于比较字时，返回 `true`。

下例中，如果玩家名为 RockyHawk 或 TinyTank800 或 Notch，则显示金块。

```
has0:
  value0: 'RockyHawk OR TinyTank800 OR Notch'
  compare0: '%cp-player-name%'
  material: GOLD_BLOCK
```

### **NOT 非**

如果需要相反的效果，可以使用 `NOT` 操作符。

下例中，如果玩家名不是 RockyHawk，则显示金块。

```
has0:
  value0: 'NOT RockyHawk'
  compare0: '%cp-player-name%'
  material: GOLD_BLOCK
```

### **AND 和**

要检查并保证多个参数均为 `true`，可使用 `AND` 操作符。这就是 `value0` 和 `compare0` 末尾有 `0` 的原因。

如果需要另一个参数，也可使用 `value1` 与 `compare1`。读取顺序由数值从低至高。 下例中，仅当该玩家至少有 500 元余额、且玩家名为 RockyHawk 时为 `true`。

```
has0:
  value0: '%cp-player-balance% ISGREATER'
  compare0: '500 AND'
  value1: '%cp-player-name%'
  compare1: 'RockyHawk'
```

### **Permissions 权限**

用于检查玩家是否有指定权限。如果并不是想检查使用面板的玩家的权限，也可以将玩家名改为别的什么东西。

```
has0:
  value0: '%cp-player-name% HASPERM'
  compare0: essentials.gamemode
```

### **Compare Values 比较**

当两个值相等时显示该节。将比较 `value0` 与 `compare0` 的值，并检查二者是否相等。不解析颜色代码。

```
has0:
  value0: RockyHawk
  compare0: '%cp-player-name%'
```

### **Is Greater 大于（或等于）**

用于检测数值是否大于等于另一个数值。 下例中，如果玩家余额为 500 或以上，则为 `true`。

```
has0:
  value0: '%cp-player-balance% ISGREATER'
  compare0: 500
```
