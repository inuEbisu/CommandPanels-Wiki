---
description: 通过使用聊天栏，玩家可以为命令添加输入
---

# 玩家输入

## 点击物件

要让玩家在聊天栏输入命令，可使用以下样例。如你所见，命令也在 `player-input` 下，而不是在 `commands` 下。这些命令将在玩家输入后运行，所以使用输入 Placeholder 仅在该列表下有效。样例中的命令列表仍然可以使用，并且命令将在点击物件后立即执行。

```
'4':
  material: GRASS_BLOCK
  name: "样例物件"
  player-input:
  - "msg= Input --> %cp-player-input%" # 将使用消息替换 Placeholder
  - "msg= another message" # 总在上一条消息之后执行
  commands:
  - "cpc" # 面板自动关闭
```

## 最大字符数

使用 `%cp-player-input-[数值]%` Placeholder 可从输入中选择单词。例如，玩家输入 `no thanks` 且 Placeholder 的数值为 1，则最终输出为 `no`。

以下样例应置于主面板中，而不是在特定的物件中。作为参考，缩进应与面板标题或行数相同。

从以下样例可以看出，也可以添加最大输入长度设置，并添加玩家输入过长时发送的自定义消息。

```
max-input-length: 1
custom-messages:
  input: '&b自定义最大字符数消息！'
```
