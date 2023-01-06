---
description: 如何为命令使用序列。
---

# 命令序列

## **如何使用 `sequence= [位置]` 序列标签**

序列标签只是用于以 YAML 文件的形式将同样的命令置于不同的地方，实现命令复用。下面是一个例子。 通过使用 `sendMessage` ，将在文件中检查该位置是否有文件中的列表。一旦找到，无论序列在哪里，都将把命令插入该物件的命令中。

```
panels:
  adminPanel:
    perm: default
    rows: 5
    title: '&6&l管理面板'
    commands:
    - mod
    empty: 'Black_Stained_glass_pane'
    sendMessage:
    - commandpanels:commandpanelclose
    - console= title %cp-player-name% times 20 60 20
    - console= title %cp-player-name% subtitle {"text":"已被惩罚","color":"green"}
    - console= title %cp-player-name% title {"text":"%cp-player-input%"}
    item:
      '22':
        material: COMPASS
        name: '&b封禁'
        commands:
        - 'console= ban %cp-player-input%'
        - 'sequence= sendMessage'
      '20':
        material: BOOK
        name: '&4踢出'
        commands:
        - 'console= kick %cp-player-input%'
        - 'sequence= sendMessage'
      '24':
        material: orange_dye
        name: '&6警告'
        commands:
        - 'console= warn %cp-player-input%'
        - 'sequence= sendMessage'
```

![Porkchop\_64 已被惩罚](https://pic.imgdb.cn/item/63b5898bbe43e0d30e776db5.png)
