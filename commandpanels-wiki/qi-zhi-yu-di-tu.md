---
description: 为特殊物件使用自定义方法。
---

# 旗帜与地图

## 自定义地图

(i) 自定义地图将使用覆盖地图 ID #0，故需要确保创建的第一张地图未被使用。如果已被使用，可以在地图 0 区域创建新地图，使用新的 ID。

### **如何为自定义地图设置图片**

只需几步，即可在为 CommandPanels 保存图片时找到自定义地图的图片。 需要新建文件夹 `maps`，如下图所示。在该文件夹中可放置图片，图片可随意命名。

![](https://pic.imgdb.cn/item/63b6ebd3be43e0d30ea81625.png)

![](https://pic.imgdb.cn/item/63b6ebd3be43e0d30ea815c3.png)

在 `maps` 文件夹中放置图片后，即可在快捷栏物件中使用图片。需要保证物件材质为 `FILLED_MAP`（地图），且使用图片名称创建一个名如 `map: map1.png` 的新节。下图阐述了物件样例。 注意，地图图片文件需为 `128x128` 像素。如果过大，Minecraft 将渲染得过大；如果过小，则不会填满地图。

![配置文件中的物件名称样例](https://pic.imgdb.cn/item/63b6ebd3be43e0d30ea81507.png)

## 自定义旗帜

### **如何使用自定义旗帜**

第一步，也是最简单的一步：只需将自定义旗帜拖入并置于游戏内编辑器。或者，只需在面板中添加旗帜节，如下：

```yaml
'1':
  material: RED_BANNER
  banner:
  - WHITE,STRIPE_MIDDLE
  - BLACK,SKULL
```

{% embed url="https://hub.spigotmc.org/javadocs/spigot/org/bukkit/block/banner/PatternType.html" %}

PatternTypes（旗帜图案类型）页面包含各种可供使用的旗帜图案，从上至下排列，上方的图案覆盖下方的。该列表想要多长要多长，不过请按格式：`颜色,样式`
