---
description: 可用于面板命令节的标签。
---

# 命令标签

## **命令标签**

样例命令：`console= gamemode creative %cp-player-name`

（`console=` 与命令中间必须有空格）

{% tabs %}
{% tab title="一般" %}
| 标签            | 描述                                                                                                                                                                                                                                                                                                                                 |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| open=         | <p>打开面板。<code>open= &#x3C;面板名> [Placeholder:值] {位置}</code></p><p>例如 <code>open= example_panel [cname:Rocky]</code> ​在面板中使用 <code>%cp-cname%</code> 将激活该 Placeholder。</p><p>要在玩家的物品栏区或快捷栏区打开另一个面板，使用位置设置，例如：<code>open= example_panel {Middle}</code></p><p>查阅"多个面板"页以获取更多信息。</p><p>这对于处理面板变量用处很大，查阅"面板变量"页以获取更多信息。不能用于已经打开的面板。</p> |
| close=        | <p>和 <code>cpc</code> 标签相似，不过可以选择关闭的位置。</p><ul><li>Top = 箱子位置</li><li>Middle = 玩家位置</li><li>Bottom = 快捷栏位置</li></ul><p>例如：<code>close= Middle</code> 将关闭中部的面板。</p>                                                                                                                                                                 |
| cpc           | 在命令节中使用该标签以关闭面板。如果该命令已被其他插件占用，使用 `commandpanelclose`。                                                                                                                                                                                                                                                                              |
| refresh       | 强制刷新面板。确保在点击物件时面板不会同时关闭。如果玩家的一般物品栏开放，也将刷新玩家的面板快捷栏物品。                                                                                                                                                                                                                                                                               |
| server=       | <p>在 BungeeCord 环境下传送玩家到特定的服务器。<code>server= [服务器名称]</code></p><p>玩家没有权限加入服务器时将不会传送。</p>                                                                                                                                                                                                                                           |
| force-server= | <p>在 BungeeCord 环境下强制传送玩家到特定的服务器。<code>force-server= [服务器名称]</code></p><p>不检查玩家的权限。</p>                                                                                                                                                                                                                                            |
| delay=        | <p>延迟特定命令。<code>delay= &#x3C;游戏刻> &#x3C;命令></code></p><p>例如，<code>delay= 20 msg= 这条消息需要 1 秒以显示。</code></p>                                                                                                                                                                                                                         |
| sudo=         | 以玩家身份执行只有玩家可以执行的命令。`sudo= [命令]`                                                                                                                                                                                                                                                                                                    |
| console=      | 在控制台中执行命令。                                                                                                                                                                                                                                                                                                                         |
| event=        | <p>触发附有消息的 PanelCommandEvent（面板命令事件）。</p><p>例如，<code>event= &#x3C;消息></code>。</p>                                                                                                                                                                                                                                                  |
| minimessage=  | 需要 Paper MiniMessage API。使用 `minimessage= <文本>` 以利用该 API。                                                                                                                                                                                                                                                                          |
| sequence=     | 使用命令序列，以对不同的物件设定相同的命令。`sequence= [YAML位置]`                                                                                                                                                                                                                                                                                         |
| op=           | 在命令前加上该标签，使玩家不需要任何权限即可执行命令。（不推荐使用）                                                                                                                                                                                                                                                                                                 |
| nopapi=       | 禁止 PlaceholderAPI 中的 Placeholder 执行。                                                                                                                                                                                                                                                                                               |
| title=        | <p>在玩家屏幕上显示标题。为了区分标题与副标题，要添加副标题，只需在标题与副标题之间加上这个东西：<code>/n/</code> </p><p><code>title= [玩家] [淡入] [维持] [淡出] [标题内容]</code></p>                                                                                                                                                                                                       |
{% endtab %}

{% tab title="支付门槛" %}
| 标签            | 描述                                                                                                                                                                                                                             |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| paywall=      | <p>玩家付费后才可执行物件命令列表中该条标签以下的命令。</p><p>样例：<code>paywall= [价格]</code></p>                                                                                                                                                          |
| data-paywall= | <p>使用 CommandPanels 数据值进行支付。数据值需为数值。</p><p>用法：<code>data-paywall= [数据] [价格]</code></p>                                                                                                                                         |
| item-paywall= | <p>玩家支付特定物品后才可执行命令列表中该条标签以下的命令。</p><p>用法：<code>item-paywall= [物品]</code></p><p>样例：<code>item-paywall= DIAMOND_SWORD 1</code></p><p>物品支付门槛也可以使用面板自定义命令。关于其解释，请查阅"面板编辑"页。</p><p>样例：<code>item-paywall= [自定义物件名称] [数量]</code></p> |
| xp-paywall=   | 玩家支付一定经验等级后才可执行物件命令列表中该条标签以下的命令。对于第二个参数，可选择 `level`（等级）或 `point`（经验点数）。                                                                                                                                                        |
| coinpaywall=  | 需要 `CoinsAPI` 插件。玩家支付代币后才可执行物件命令列表中该条标签以下的命令。`coinpaywall= [价格]`                                                                                                                                                               |
| tokenpaywall= | 玩家支付代币后才可执行物件命令列表中该条标签以下的命令。`tokenpaywall= [代币价格]`                                                                                                                                                                             |
{% endtab %}

{% tab title="玩家" %}
| 标签         | 描述                                                                                                                                                                                                                                                                         |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| sound=     | <p>使用 <code>sound= [音效名]</code> 在点击物件时播放音效。</p><p>音效名列表见<a href="https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Sound.html">此</a>。</p><p>使用 <code>sound= [音效名] [音量] [音高]</code> 自定义音量与音高。默认值均为 1；音量的取值范围为 <code>0.0 - 1.0</code>，音高的取值范围为 <code>0.5 - 2.0</code>。</p> |
| stopsound= | <p>使用 <code>stopsound= [音效名]</code> 在点击物件时停止播放音效。</p><p>音效名列表见<a href="https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Sound.html">此</a>。</p>                                                                                                                          |
| teleport=  | <p>传送玩家。</p><p>样例：<code>teleport= [x] [y] [z] [可选玩家名称]</code> 或 <code>teleport= [x] [y] [z] [yaw(偏航角)] [pitch(俯仰角)]</code></p>                                                                                                                                             |
| send=      | 以玩家身份发送全局聊天信息。使用 `send= [信息]`。                                                                                                                                                                                                                                             |
| msg=       | 玩家执行命令时发送消息。                                                                                                                                                                                                                                                               |
{% endtab %}

{% tab title="购入与售出" %}
| 标签               | 描述                                                                                                                                                                                                                                            |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| buy=             | <p>玩家将购买物品。例如，以 3 元的价格购入 12 个草方块：<code>buy= 3 WOOL 12 id:15</code></p><p>用法：<code>buy= [价格] [材料] [数量] [id:材质 ID (颜色什么的)]</code> (需要 Vault)</p>                                                                                                |
| sell=            | <p>玩家将售出物品。例如，以 3 元的售价售出 12 个草方块：<code>sell= 3 WOOL 12 id:15</code></p><p>用法：<code>sell= [返还价格] [材料] [数量] [id:材质 ID (颜色什么的)]</code> (需要 Vault)</p><p>对于药水，需要添加 PotionEffectType 药水效果类型，如下： <code>sell= 1 IRON_INGOT 45 potion:HEAL</code></p> |
| buycommand=      | <p>玩家将购买命令。用法：<code>buycommand= [价格] [命令]</code></p><p>要在控制台执行，以下是一个含玩家名的样例：<code>buycommand= 100 console= gamemode creative %cp-player-name%</code></p>                                                                                      |
| tokenbuy=        | <p>玩家将购买物品。例如，以 3 代币的价格购入 12 个草方块：<code>tokenbuy= 3 WOOL 12 id:15</code></p><p>用法：<code>tokenbuy= [代币价格] [材料] [数量] [id:材质 ID (颜色什么的)]</code> (需要 Vault)</p>                                                                                   |
| coinbuy=         | <p>使用 CoinsAPI 购买物品。例如，以 3 硬币的价格购入 12 个草方块：<code>coinbuy= 3 WOOL 12 id:15</code></p><p>用法：<code>coinbuy= [硬币价格] [材料] [数量] [id:材质 ID (颜色什么的)]</code></p>                                                                                       |
| tokensell=       | <p>玩家将售出物品。例如，以 3 代币的价格售出 12 个草方块：<code>tokenbuy= 3 WOOL 12 id:15</code></p><p>用法：<code>tokensell= [返还的代币价格] [材料] [数量] [id:材质 ID (颜色什么的)]</code> (需要 Vault)</p>                                                                               |
| coinsell=        | <p>使用 CoinsAPI 售出物品。例如，以 3 硬币的价格售出 12 个草方块：<code>coinbuy= 3 WOOL 12 id:15</code></p><p>用法：<code>coinbuy= [返还的硬币价格] [材料] [数量] [id:材质 ID (颜色什么的)]</code></p>                                                                                    |
| tokenbuycommand= | <p>玩家将购买命令。用法：<code>tokenbuycommand= [代币价格] [命令]</code></p><p>要在控制台执行，以下是一个含玩家名的样例：<code>tokenbuycommand= 100 console= gamemode creative %cp-player-name%</code></p>                                                                          |
{% endtab %}

{% tab title="物件" %}
| 标签         | 描述                                                                                                                                                                                                                                                        |
| ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| setitem=   | <p>用于将面板槽位中的物件设置为其他东西。对于 <code>placeable</code>（可放置）物件槽很好用。</p><p>样例：<code>setitem= &#x3C;自定义物件名> &#x3C;槽位> &#x3C;位置></code>。</p><p>要了解如何创建自定义物件，请查阅本 Wiki 的"面板编辑"部分。</p><p>位置可为 <code>Top</code>（顶部）、<code>Middle</code>（中部）、<code>Bottom</code>（底部）</p> |
| give-item= | 用于给予玩家自定义物件。用法：`give-item= <自定义物件>`                                                                                                                                                                                                                       |
{% endtab %}

{% tab title="数据" %}
| 标签               | 描述                                                                                                                                                                                               |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| placeholder=     | <p>与 <code>open=</code> 相似，不过用于在当前面板编辑 Placeholder。例如：<code>placeholder= [placeholder:值]</code>。</p><p>参见"面板变量"页以获取教程。</p>                                                                       |
| add-placeholder= | <p>同上；不过当 Placeholder 不存在时会自动添加该 Placeholder。</p><p><code>add-placeholder= [placeholder:值]</code></p>                                                                                            |
| set-data=        | `set-data= <数据名> <值> [玩家名]` 设置玩家数据为给定值。值只能为一个单词长（即不能有空格）。玩家名可选。                                                                                                                                  |
| add-data=        | `add-data <数据名> <值> [玩家名]` 设置玩家数据为给定值。值只能为一个单词长（即不能有空格）。不覆盖原本数据；故如该玩家已有特定数据，将跳过。玩家名可选。                                                                                                           |
| math-data=       | <p>用于更改数值数据。用法：<code>math-data &#x3C;数据名> &#x3C;操作> [玩家名]</code>。</p><p>有四种操作符：加( + )、减( - )、乘( * )、除( / )。应以操作符开始、数字结束；</p><p>以下是一些操作样例：+1、+0.1、-15、*3、/5。</p><p>将使用当前所存储的数值，并加以指定操作。玩家名可选。</p> |
| del-data=        | `del-data= <数据名> [玩家名]` 为玩家删除数据。玩家名可选。                                                                                                                                                           |
| clear-data=      | `clear-data= <玩家名>` 为玩家清除所有数据。                                                                                                                                                                   |
{% endtab %}
{% endtabs %}

## **点击标签**

点击标签必须放在常规的命令标签前。在点击标签、其他标签、命令之间需要空格隔开。点击标签仅用于物件中的常规命令。

```
commands:
- 'msg= &c该条信息将在任意类型的点击后出现。'
- 'right= msg= 右键物件！'
```

| 标签          | 描述                    |
| ----------- | --------------------- |
| right=      | 玩家需要右键以执行命令           |
| rightshift= | 玩家需要 Shift + 右键以执行命令。 |
| left=       | 玩家需要左键以执行命令           |
| leftshift=  | 玩家需要 Shift + 左键以执行命令。 |
| middle=     | 玩家需要中键以执行命令           |
