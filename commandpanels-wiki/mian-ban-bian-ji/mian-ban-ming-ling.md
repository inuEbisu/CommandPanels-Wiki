---
description: 如何添加自定义命令以打开面板
---

# 面板命令

## **自定义命令**

执行命令 `/example` **或** `/ex` **或** `/e` 以打开面板。自定义命令可为每个面板随意更改。 与物品命令不同，这些命令位于面板顶部，靠近标题与第一行。 要自动注册命令，重启服务器以保存更改。

```
commands: 
- example
- ex
- e
```

要在命令中添加变量，比如创建一个封禁 GUI，可以通过使用 Placeholder 完成。只需在命令中放置 Placeholder，确保其以 `%cp-` 开头，别的随意。 （当然了，可以有多个 Placeholder，不过需要分别独立。）

```
commands: 
- ban %chosenPlayer%
```

据上面的样例，在输入命令时可以输入一个参数，即 `/ban <玩家名>`。于是，Placeholder `%cp-chosenPlayer` 可以在面板中随意使用。 只需记住，在使用 Placeholder 时，你需要在其开头加上 `cp-`，正如本例所示。
