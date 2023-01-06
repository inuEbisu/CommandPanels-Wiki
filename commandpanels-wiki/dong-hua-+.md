---
description: CommandPanels 的动画
---

# 动画 +

## 如何为物件制作动画

要为物件制作动画，需要在面板顶部添加以下代码，如下例所示：（在最后一行）

```yaml
panels:
  animationTester:
    perm: default
    rows: 1
    title: '&a测试动画'
    empty: BLACK_STAINED_GLASS_PANE
    animatevalue: 6 <-- 添加该行
```

例如，如果数值为 6，则从 0 至 6 循环；所以在该样例中，动画被划分为 6 阶段。 要调整从 0 至 6 循环的速度，在主要配置文件 `config.yml` 中找到 `refresh-delay` 项并调整。

```yaml
item:
  '2':
    material: BARRIER
    name: 这是默认物件
    animate0:
      material: PURPLE_STAINED_GLASS_PANE
      name: '&5彩虹颜色!'
    animate1:
      material: RED_STAINED_GLASS_PANE
      name: '&c彩虹颜色!'
    animate2:
      material: ORANGE_STAINED_GLASS_PANE
      name: '&6彩虹颜色!'
    animate3:
      material: YELLOW_STAINED_GLASS_PANE
      name: '&e彩虹颜色!'
    animate4:
      material: LIME_STAINED_GLASS_PANE
      name: '&a彩虹颜色!'
    animate5:
      material: LIGHT_BLUE_STAINED_GLASS_PANE
      name: '&9彩虹颜色!'
    animate6:
      material: MAGENTA_STAINED_GLASS_PANE
      name: '&d彩虹颜色!'
```

在上例中，其将从 0 至 6 循环 7 个动画值。如果缺少某个值，例如 3，则当其循环到 3 时，其只显示默认物件。

除了快捷栏物件，任何物件都可以加入动画标签。也可以在 Has 节中加入动画。
