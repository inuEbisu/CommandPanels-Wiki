---
description: 施工中
---

# 开发者 API

## API 方法

### **介绍**

Command Panels 可以作为依赖，来为你的插件创建 GUI。使用 File 对象（推荐）或 YamlConfiguration 的面板，可在你的插件中存储 YML 文件并将其作为 GUI 使用。

当然，无论是 YML 文件还是 YamlConfiguration，都需要与其他面板一样遵循相同的语法。然而，存储面板的位置并不一定要在面板文件夹，其也可以在你的插件代码里。

要在点击物件时使用自己的代码，需要使用 `event= <消息>` 标签作为物件 YAML 文件中的命令，这将导致该物件触发 PanelCommandEvent 事件；也就是说，你可以为该事件上一个 Listener，然后检查以确保消息与在物件中所用消息的相等。

```java
// 获取 Command Panels API
CommandPanelsAPI api = CommandPanels.getAPI();
```

在使用以上代码初始化 API 之后，便可执行以下方法：

| 方法                                                        | 返回值       | 描述                                                                                                 |
| --------------------------------------------------------- | --------- | -------------------------------------------------------------------------------------------------- |
| api.isPanelOpen(Player p);                                | Boolean   | 检查玩家是否有面板打开。                                                                                       |
| api.getOpenPanel(Player p, PanelPosition position); Panel | Panel     | 获取玩家当前打开的面板的 Panel 对象。面板位置 PanelPosition 可为 Top, Middle 或 Bottom，分别代表物品栏区域中的顶部（箱子）、中部（玩家）、底部（快捷栏）。 |
| api.getPanelsLoaded();                                    | List      | 获取 CommandPanels 插件加载的所有面板。                                                                        |
| api.addPanel(Panel panel);                                | -         | 在加载了 CommandPanels 的插件中添加面板。                                                                       |
| api.makeItem(ConfigurationSection item)                   | ItemStack | 获取物件的配置节，例如面板中一个物件的节。然后插件将制作一个自定义物件并返回其 ItemStack。                                                 |
| api.removePanel(Panel panel);                             | -         | 在加载了 CommandPanels 的插件中删除面板。                                                                       |
| api.hasNormalInventory(Player p);                         | boolean   | 如果玩家物品栏中有面板，且其并非正常物品栏，则返回 false。                                                                   |
| api.getPanel(String panelName);                           | Panel     | 获取给定名称的一个已加载面板。                                                                                    |

### **物件槽位是否放置了固定物件**

在物品栏中的特定槽位上，Command Panels 可能有用于点击打开面板的物件，无法移动。 以下方法将返回一个 int ArrayList，其中列出所有 Command Panels 使用的槽位。`0 - 8` 为快捷栏， `9 - 33` 为物品栏。

```java
CommandPanelsAPI api = CommandPanels.getAPI();
api.getHotbarItems();
```

## 处理面板

可以创建面板对象。以下是创建面板之后可进行的操作。

### **制作面板**

要制作面板，首先获取面板的 File 或 YamlConfiguration。更推荐 File，因为在 Command Panels 中，File 可加入已加载的面板。

```java
File file = new File("panel.yml");
String panelName = "example";
Panel panel = new Panel(file, panelName);
```

### **面板方法**

{% tabs %}
{% tab title="一般" %}
| 方法                                             | 返回值       | 描述                                            |
| ---------------------------------------------- | --------- | --------------------------------------------- |
| panel.open(Player p, PanelPosition position);  | -         | 为玩家打开面板。确保该面板还没有打开。如果还没有面板打开，使用 Top （顶部）面板位置。 |
| panel.getHotbarItem(Player p)                  | ItemStack | 获取面板快捷栏物件。                                    |
| panel.hasHotbarItem()                          | Boolean   | 检查面板是否有快捷栏物件。                                 |
| panel.getInventory()                           | Inventory | 获取面板的普通物品栏形式。                                 |
| panel.getCustomItem(Player p, String itemName) | ItemStack | 获取一个面板的自定义物件。                                 |
| panel.getItem(Player p, int slot)              | ItemStack | 通过槽位获取面板中的物件。                                 |
{% endtab %}

{% tab title="获取值" %}
| 方法                | 返回值                  | 描述                          |
| ----------------- | -------------------- | --------------------------- |
| panel.getName()   | String               | 获取面板名。                      |
| panel.getConfig() | ConfigurationSection | 获取面板的 ConfigurationSection。 |
| panel.getFile()   | File                 | 获取面板文件。                     |
{% endtab %}

{% tab title="设置值" %}
| 方法                                            | 返回值 | 描述         |
| --------------------------------------------- | --- | ---------- |
| panel.setName(String name);                   | -   | 为面板设置新的名称。 |
| panel.setFile(File file);                     | -   | 为面板设置新的文件。 |
| panel.setConfig(ConfigurationSection config); | -   | 为面板设置新的配置。 |
{% endtab %}
{% endtabs %}

### **玩家是否有面板打开**

要检查玩家是否有面板打开，首先获取 API 并赋值给一个变量，然后便可以使用 API，见下例。

下例中，如果指定的玩家有面板打开，则返回 true，反之返回 false。

```java
CommandPanelsAPI api = CommandPanels.getAPI();
api.isPanelOpen(Player p);
```

下例会返回一个面板对象，通过它可以查看玩家打开了哪一个面板。通过面板对象，可以查看面板内的所有东西、储存位置，甚至可以再次打开面板。

```java
CommandPanelsAPI api = CommandPanels.getAPI();
api.getPanel(Player p);
```

## API 事件

### **PanelOpenedEvent 面板打开事件**

打开面板时，该事件被调用。以下是一个样例类，其中包含事件。可以对其使用多种方法，例如取消事件，即阻止面板打开。

```java
public class Utils implements Listener {
    @EventHandler
    public void onPanelOpen(PanelOpenedEvent e){
        // 搞事
    }
```

`e.getPlayer();` 获取打开面板的玩家。

`e.getPanelName();` 返回所打开面板的名称，类型为字符串。

`e.getPanel.getConfig();` 返回一个 ConfigurationSection，其中包含各项面板设置。例如，要获取面板标题，可使用 `e.getPanel.getConfig().getString("title")`。

`e.isCancelled()` 事件是否已取消

`e.setCancelled()` 取消事件，以阻止面板打开。

### **PanelClosedEvent 面板关闭事件**

关闭面板时，该事件被调用。以下是一个样例类，其中包含事件。可以对其使用多种方法。

```java
public class Utils implements Listener {
    @EventHandler
    public void onPanelClose(PanelClosedEvent e){
        // 搞事
    }
```

`e.getPlayer();` 获取打开面板的玩家。

`e.getPanelName();` 返回一个字符串，即所打开面板的名称。

`e.getPanel.getConfig();` 返回一个 ConfigurationSection，其中包含各项面板设置。例如，要获取面板标题，可使用 `e.getPanel.getConfig().getString("title")`。

### **PanelCommandEvent 面板命令事件**

在面板内使用命令标签 `event= <信息>`时，该事件被调用。以下是一个样例类，其中包含事件。可以查看从面板内部留下的参数/信息。

```java
public class Utils implements Listener {
    @EventHandler
    public void onPanelCommand(PanelCommandEvent e){
        // 搞事
    }
```

`e.getPlayer();` 获取打开面板的玩家。

`e.getMessage();` 返回一个字符串，即在命令标签之后留下的信息。

