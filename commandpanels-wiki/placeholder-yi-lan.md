---
description: Placeholder 列表。
---

# Placeholder 一览

## 内建 Placeholder

要将 CommandPanels 的 Placeholder 嵌套于其他 Placeholder 中，可以使用配置文件中的二级符号。样例：%cp-data-bans,{cp-player-name}%

要为特定的面板修改 Placeholder 的符号，下面是一个例子。将下面这串配置加入面板，可单独为其改变符号。

{% code lineNumbers="true" %}
```yaml
placeholders:
  primary:
    start: $
    end: $
  secondary:
    start: '{'
    end: '}'
```
{% endcode %}

{% tabs %}
{% tab title="玩家" %}
| Placeholder             | 描述                                                                                      |
| ----------------------- | --------------------------------------------------------------------------------------- |
| %cp-player-displayname% | 玩家显示名称                                                                                  |
| %cp-player-name%        | 玩家用户名                                                                                   |
| %cp-player-x%           | 玩家 X 轴坐标                                                                                |
| %cp-player-y%           | 玩家 Y 轴坐标                                                                                |
| %cp-player-z%           | 玩家 Z 轴坐标                                                                                |
| %cp-player-input%       | 与 玩家输入命令 一节搭配使用                                                                         |
| %cp-player-world%       | 玩家所在的世界名                                                                                |
| %cp-player-balance%     | 玩家余额(需要 Vault 及一款经济插件)                                                                  |
| %cp-player-online-1%    | 数字 1 可以改为任何数值。检查服务器槽位，并找到位于该槽位的玩家。如果只有你在线，并且数值为 1，将显示为你自己。如果数值设置为 2，将显示为离线，毕竟你是唯一一个在线的。 |
{% endtab %}

{% tab title="材料" %}
| Placeholder                 | 描述                                                                                      |
| --------------------------- | --------------------------------------------------------------------------------------- |
| %cp-material-<槽位>%          | 在面板中选择相应序号的槽位，返回槽位中放置物品的材料。如果您的 Minecraft 版本是旧版本(1.12 及以下)，返回的字符串末尾会附上其ID。就像这样：`WOOD:5` |
| %cp-nbt-<槽位:键>%             | 在面板中选择相应序号的槽位，在 Placeholder 中的键部分选择 NBT 标签的键(标题)，以输出 NBT 标签的值。                          |
| %cp-stack-<槽位>%             | 在面板中选择相应序号的槽位，返回该槽位的堆叠数。                                                                |
| %cp-damaged-<槽位>%           | 在面板中选择相应序号的槽位，如果该物件耐久值有损耗则返回 `true`，反之返回 `false`。                                       |
| %cp-modeldata-<槽位>%         | 返回在 GUI 中选定的物件的模型数据值。                                                                   |
| %cp-identical-<自定义物品>,<槽位>% | 用于确定面板中的物件是否与面板自定义物件部分中的物件相符。                                                           |
{% endtab %}

{% tab title="数据与数学" %}
| Placeholder               | 描述                                                                                                |
| ------------------------- | ------------------------------------------------------------------------------------------------- |
| %cp-data-<数据名>%           | 获取玩家数据的值。如该玩家并没有存储为该名称的数据，Placeholder 将原封不动，不会被替换为数值。                                             |
| %cp-data-<数据名>,<玩家名>%     | 获取玩家数据的值。大致同上，但有一个 <玩家名> 部分，可以指定所查看的玩家。                                                           |
| %cp-setdata-<数据名>,<数据值>%  | 通过 Placeholder 改变数据值。通过该方法，无需点击物件即可改动数据。(与 `set-data=` 命令相似。) 样例：`%cp-setdata-playerTeam,yellow%` |
| %cp-mathdata-<数据名>,<数据值>% | 通过 Placeholder 对数据值进行数学运算。(与 `math-data=` 命令相似。) 样例：`%cp-setdata-playerMoney,+1%`                 |
| %cp-random-<最小值>,<最大值>%   | 输出在指定闭区间内的随机数。样例：`%cp-random-1,10%`                                                               |
{% endtab %}

{% tab title="杂项" %}
| Placeholder            | 描述                                 |
| ---------------------- | ---------------------------------- |
| %cp-online-players%    | 在线人数                               |
| %cp-panel-position%    | 返回该 Placeholder 所在面板的位置（顶部/中部/底部）。 |
| %cp-clicked%           | 该物件是否已被点击过。(仅在命令节使用)               |
| %cp-tag%               | 显示插件的消息标签。默认为 \[CommandPanels]。    |
| %cp-server-\<IP>:<端口>% | 如果指定服务器在线，返回 true。如果离线，返回 false。   |
{% endtab %}

{% tab title="其他插件" %}
| Placeholder               | 描述                          |
| ------------------------- | --------------------------- |
| %cp-tokenmanager-balance% | 玩家代币余额 (需要 TokenManager)    |
| %cp-votingplugin-points%  | 玩家所有的投票点数 (需要 VotingPlugin) |
{% endtab %}
{% endtabs %}

## 扩展 Placeholder

如果需要于其他插件中使用上述内建 Placeholder，请阅读以下指南。

该方法需要 Placeholder API 以正常运作；其他插件也需要支持 Placeholder API。

只需要复制上述 Placeholder，再改一下形式。样例：

前: `%cp-data-example%`&#x20;

后: `%commandpanels_data-example%`

前: `%cp-setdata-example,test1%`&#x20;

后: `%commandpanels_setdata-example,test1%`

如你所见，你只需要将 Placeholder 中的 `cp-` 替换为 `commandpanels_`。
