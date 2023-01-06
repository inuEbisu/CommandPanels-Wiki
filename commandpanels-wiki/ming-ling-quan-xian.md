---
description: 插件中的命令与权限列表。
---

# 命令权限

| 命令                                                                       | 权限                         | 描述                                                                                                                          |
| ------------------------------------------------------------------------ | -------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| /cp                                                                      | -                          | 在游戏内显示命令列表                                                                                                                  |
| /cp \[面板]                                                                | commandpanel.panel.\[面板权限] | 打开指定面板。                                                                                                                     |
| /cp \[面板] \[玩家名]                                                         | commandpanel.other         | 为其他玩家打开面板，并给予玩家面板快捷栏物品。                                                                                                     |
| /cp \[面板] item \[可选玩家名]                                                  | commandpanel.item.\[面板权限]  | 获取用于在快捷栏中打开面板的物品。                                                                                                           |
| /cpl                                                                     | commandpanel.list          | 列出当前已加载的面板。                                                                                                                 |
| /cpg \[rows]                                                             | commandpanel.generate      | 生成指定行数(1 - 6)的面板                                                                                                            |
| /cpr                                                                     | commandpanel.reload        | 重载插件配置。                                                                                                                     |
| /cpv                                                                     | commandpanel.version       | 检查插件版本。                                                                                                                     |
| /cpv latest                                                              | commandpanel.update        | 下载 CommandPanels 的最新版本，并于服务器下一次启动时自动安装。                                                                                     |
| /cpv \[版本]                                                               | commandpanel.update        | <p>在服务器重载/重启时，强制下载指定版本的 CommandPanels。</p><p>样例：<code>/cpv 3.14.2.0</code></p><p>输入 <code>/cpv cancel</code> 以取消计划中的下载。</p> |
| /cpi \[文件名] \[链接]                                                        | commandpanel.import        | 用于自动在线导入原始文本至服务器。                                                                                                           |
| /cpdata \[set(设置):add(添加):get(获取):remove(删除):clear(清除)] \[玩家] \[数据] \[值] | commandpanel.data          | 用于为玩家调整面板数据。要屏蔽返回信息，可使用`/cpdata -s <参数>`。                                                                                   |
| /cpd                                                                     | commandpanel.debug         | 通过控制台详细浏览存在的错误。启用该功能后，面板将随其文件自动更新。                                                                                          |
| /cpe \[面板]                                                               | commandpanel.edit          | 打开编辑器。输入面板名作为参数时，可快捷编辑指定面板。                                                                                                 |
| /cpb add \[面板]                                                           | commandpanel.block.add     | 允许玩家通过右键方块打开面板。                                                                                                             |
| /cpb remove                                                              | commandpanel.block.remove  | 移除您看向（十字准心指向）的方块上绑定的面板。                                                                                                     |
| /cpb list                                                                | commandpanel.block.list    | 列出有绑定面板的方块的位置。                                                                                                              |
| -                                                                        | commandpanel.\*            | 允许执行 CommandPanel 的所有命令。                                                                                                    |

