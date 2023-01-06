---
description: 使用变量操作面板。
---

# 面板变量

## 面板变量是什么？

面板变量是一些自定义 Placeholder，或者可以跨面板使用的数据。事实上，面板变量可以从一个面板跨越至另一面板，或者永久保存，以便在下次打开面板时插件能够记住数据。

### Placeholder 变量

#### **创建 Placeholder**

要定义 Placeholder 及其值，使用以下命令。需要输入所打开的面板名称，然后按以下格式输入：`[placeholder:值]`。Placeholder 值可以包含空格；Placeholder 本身应不含大写字母。

```
'0':
  material: STONE
  commands:
  - open= panel-3 [example1:Placeholder 值] [mat:STONE]
  - msg= 该 Placeholder 的值为 %cp-example1%
```

在定义 Placeholder 后，在你想打开的面板内随意使用。

在以上样例中，Placeholder 为 `example1`；也就是说，可以使用 `%cp-example1%`。

#### **编辑 Placeholder**

要在当前面板中编辑 Placeholder，不可如上所述使用 `open=`。将 `open=` 改为 `placeholder=`，便可在当前面板中编辑 Placeholder。

只需定义要编辑的特定的 Placeholder，其他没有添加的 Placeholder 将保持原状。例如，使用以上样例时，如果打开 `panel-3`，且需要一个物件更改 Placeholder `%cp-mat%` 为 `BEACON`，使用以下命令：

```
'7':
  material: BEACON
  commands:
  - placeholder= [%cp-mat%:BEACON]
```

### 数据变量

#### **创建数据变量**

要永久存储数据，比起 Placeholder 变量，数据变量更好用。数据值将永久存储至文件中，服务器重启时也会保留不丢失。需要用以下命令标签之一以设置值。

{% tabs %}
{% tab title="添加值" %}
`add-data= [数据名] [值] [可选玩家]`

不会覆盖旧数据，不过如果玩家没有该数据名的数据值，则会写入值。对于面板的 `commands-on-open` （打开时命令）很好用，可以确保在使用面板前已设置数据。
{% endtab %}

{% tab title="设置值" %}
`set-data= [数据名] [值] [可选玩家]`

用于覆盖该数据名之下的已有值，设置数据为新的值。
{% endtab %}

{% tab title="删除值" %}
`del-data= [数据名] [可选玩家]`

用于为玩家永久删除特定数据值。删除之后可以使用 `add-data` 标签，因为对于玩家，指定的数据名下已经没有数据存在了。

`clear-data= [player name]`

清除玩家保存的所有数据。使用 `%cp-player-name%` 以指定打开面板的玩家。
{% endtab %}

{% tab title="使用数学" %}
`math-data= [数据名] [操作] [可选玩家]`

用于更改数值数据。用法：`math-data <数据名> <操作> [玩家名]`。

有四种操作符：加( + )、减( - )、乘( \* )、除( / )。应以操作符开始、数字结束；

以下是一些操作样例：+1、+0.1、-15、\*3、/5。

将使用当前所存储的数值，并加以指定操作。玩家名可选。
{% endtab %}
{% endtabs %}

#### **查看数据变量**

要查看数据变量，只需使用以下 Placeholder。

`%cp-data-[数据名]%` 将 \[数据名] 替换为要查看的数据名。

`%cp-data-[数据名],[玩家名]%` 以查看其他玩家的数据变量。

#### **使用 Placeholder 设置数据变量**

可以使用 Placeholder 操作变量，见以下 Placeholder。

`%cp-setdata-[数据名],[新值]%` 将 \[数据名] 替换为要编辑的数据名。

### 小贴士

如果直接打开面板而变量没有定义，则会直接显示原始 Placeholder 而没有任何值。&#x20;

要使用 Placeholder 值以更改物件外观，使用 `hasvalue` 节以将物件改为别的东西。&#x20;

数据名与数据值不能包含大写字母。
