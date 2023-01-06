---
description: 主要配置文件及其食用方法
---

# 配置文件

## 配置文件 config.yml

{% code lineNumbers="true" %}
```yaml
# |------------------------------------------------------------------------
# | CommandPanels 配置文件
# | By RockyHawk v5.2
# | 汉化: inuEbisu
# | Spigot MC: https://www.spigotmc.org/resources/command-panels-custom-guis.67788/
# | MCBBS: https://www.mcbbs.net/thread-1412767-1-1.html
# | 强烈建议开启自动更新 (auto-update) 与 小更新 (minor-updates-only)
# |------------------------------------------------------------------------

config:
  # 如果为 true，面板中的 Placeholder 会自动刷新
  # 改动后需要重启服务器
  refresh-panels: true
  
  # 如果不需要 /cpb 指令，禁用以优化性能
  # 改动后需要重启服务器
  panel-blocks: true
  
  # 该项为 false 时禁用游戏内编辑器
  # 改动后需要重启服务器
  ingame-editor: true
  
  # 该项为 false 时禁用快捷栏物品
  # 改动后需要重启服务器
  hotbar-items: true
  
  # 该项为 false 时禁用自定义命令
  # 改动后需要重启服务器
  custom-commands: true
  
  # 该项为 false 时，禁止插件自动注册面板自定义的命令
  # 先前已经注册了的自定义命令不会从 command.yml 中删除
  auto-register-commands: true
  
  # 该项为 true 时，打开的面板会随文件的更新而自动更新
  # 启用时，如果某些以 CommandPanels 为依赖的插件未将其面板与文件相联系，则可能会出问题
  auto-update-panels: false
  
  # 自动刷新的周期（单位：游戏刻）（20 游戏刻 = 1 秒）
  refresh-delay: 20
  
  # Placeholder %cp-server-<IP>:<PORT>% 的连接超时判定时间。（单位：毫秒）
  # 译者注：使用该 Placeholder 时，若指定服务器的 ping 值大于该值，则判定该服务器离线。
  # 对于本地网络，填 10 就好。不建议大于 500 的值。
  # 该值过低可能会导致错误的负面结果；该值过高可能会导致延迟卡顿
  server-ping-timeout: 10
  
  # 面板关闭时是否停止 "sound-on-open" 声音
  stop-sound: true
  
  # 玩家试图在被禁用面板的世界中打开面板时，插件是否发送提示消息
  disabled-world-message: true
  
  # 该值为 false 时，您不会收到更新提示
  update-notifications: true
  
  # 该值为 true 时，玩家打开或关闭面板时，控制台会向其发送消息
  panel-snooper: false
  
  format:
    # 提示消息前缀
    tag: '&6[&bCommandPanels&6] '
    
    # 没有权限时的提示消息
    perms: '&c您没有权限。'
    
    # 重载插件的提示消息
    reload: '&a插件重载成功。'
    
    # 面板不存在时的提示消息
    nopanel: '&c面板不存在。'
    
    # 面板中没有用于打开的物件
    noitem: '&c面板中没有可点击的物件。'
    
    # 找不到玩家时的提示消息
    notitem: '&c找不到该玩家。'
    
    # 默认的错误代码消息
    error: '&c配置文件中存在错误：'
    
    # 当玩家离线时，Placeholder %cp-player-online-1-find% 返回的玩家名
    offline: Offline
    
    # 当玩家离线时，Placeholder %cp-player-online-1-find% 返回的头部值
    offlineHeadValue: eyJ0ZXh0d...

# 根据该配置，玩家进入时如果在世界 world1 中，就自动打开面板 example
# 可以添加多个世界
# 只在玩家所处世界改变时运作
open-on-join:
  world1: example

# 同上，不过是在玩家登录成功时
open-on-login:
  world1: example  

input:
  # 当玩家取消 %cp-player-input% 的输入时，需要输入的关键词
  input-cancel: cancel
  
  # 玩家取消输入时显示的消息
  input-cancelled: '&c取消输入！'  
  
  # 最大输入长度的默认值。
  # 如果不需要最大值，设为 -1 即可。
  max-input-length: -1
  
  # 让玩家输入时显示的信息。
  # 使用 Placeholder %cp-tag% 表示插件标签，%cp-args% 表示取消输入的关键词。
  input-message:
  - '%cp-tag%&a请输入。'
  - '&c输入 &4%cp-args% &c以取消命令。'

# 十六进制颜色编码的格式
# 根据该配置，使用时应写成 #ff0000 的形式
# 如果设置 start_tag 为 '{#'、end_tag 为 '}'，则应写成 {#ff0000} 的形式
hexcodes:
    start_tag: '#'
    end_tag: ''

# 选择用于 CommandPanels 内建 Placeholder 的符号
# start 参数即为 Placeholder 的第一个字符，end 参数即最后一个字符
# secondary 二级符号用于 Placeholder 中嵌套的 Placeholder（二级 Placeholder）
# 也可以将其放置于面板中，用于面板指定的自定义 Placeholder
placeholders:
  primary:
    start: '%'
    end: '%'
  secondary:
    start: '{'
    end: '}'

updater:
    # 推荐开启，在服务器重启时自动更新
    auto-update: true
    
    # 该项为 true 时，只自动更新一些小更新（bug修复与一些小的特性）
    minor-updates-only: true
    
    # 该项为 true 时，若插件需要更新，则在加入时发送消息。
    # 更改后，重启服务器以生效
    update-checks: true

# 在面板中购入/售出时发送的消息
# 其中的 Placeholder %cp-args% 会被替换为金额或物品类型
purchase:
  currency:
    enable: true
    success: '&a成功以 $%cp-args% 购入。'
    failure: '&c资金不足。'
  data:
    enable: true
    success: '&a成功以 $%cp-args% 购入。'
    failure: '&c资金不足。'    
  tokens:
    enable: true
    success: '&a成功以 %cp-args% 代币购入。'
    failure: '&c代币不足！'
  item:
    enable: true
    success: '&a成功售出 %cp-args%.'
    failure: '&c物品不足!'
  xp:
    enable: true
    success: '&a成功以 %cp-args% 点经验购入。'
    failure: '&c经验值不足!'
```
{% endcode %}

## 插件内建面板

### **template.yml**

```yaml
# |------------------------------------------------------------------------
# | CommandPanels 模板文件
# | By RockyHawk v3.1
# | 汉化: inuEbisu
# | Spigot MC: https://www.spigotmc.org/resources/command-panels-custom-guis.67788/
# | MCBBS: https://www.mcbbs.net/thread-1412767-1-1.html
# |------------------------------------------------------------------------

panels:
  template:
    perm: admin
    rows: 1
    title: '&8模板面板'
    empty: GLASS_PANE
    item:
      '4':
        material: COBBLESTONE
        stack: 1
        name: '&f点我！'
        commands:
        - msg= 你点击了物件！
        - cpc
```

### **example\_top.yml**

```yaml
# |------------------------------------------------------------------------
# | CommandPanels 样例文件
# | By RockyHawk v3.1
# | 汉化: inuEbisu
# | Spigot MC: https://www.spigotmc.org/resources/command-panels-custom-guis.67788/
# | MCBBS: https://www.mcbbs.net/thread-1412767-1-1.html
# |------------------------------------------------------------------------

panels:
  example:
    perm: admin
    rows: 6
    title: '&6&l[&b&l样例&6&l]&r 你好 %cp-player-name%!'
    sound-on-open: BLOCK_NOTE_BLOCK_CHIME
    pre-load-commands:
    - placeholder= [item:APPLE]
    - add-data= example_item false
    commands-on-open:
    - open= example_middle_one {Middle}
    - open= example_bottom {Bottom}
    commands:
    - example_panel
    empty: LIGHT_BLUE_STAINED_GLASS_PANE
    custom-item:
      bread:
        material: BREAD
        name: '&f唔姆……好吃'
    item:
      '1':
        material: cps= eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvYjc3MTY1YzlkYjc2M2E5YWNkMTNjMDYyMjBlOTJkM2M5NzBkZmEzNmRhYzU2ZTU5NTdkMDJkMzZmNWE5ZjBiOCJ9fX0=
        name: '&e&lE'
      '2':
        material: cps= eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvNTVkNWM3NWY2Njc1ZWRjMjkyZWEzNzg0NjA3Nzk3MGQyMjZmYmQ1MjRlN2ZkNjgwOGYzYTQ3ODFhNTQ5YjA4YyJ9fX0=
        name: '&e&lX'
      '3':
        material: cps= eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvYTUxN2I0ODI5YjgzMTkyYmQ3MjcxMTI3N2E4ZWZjNDE5NjcxMWU0MTgwYzIyYjNlMmI4MTY2YmVhMWE5ZGUxOSJ9fX0=
        name: '&e&lA'
      '4':
        material: cps= eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvMWQ3MTYyNTZkNzI3YmExZGYxOGY4MjZmMTE5MDUxYzMzYTM5NDIwOWE5NWJlODM3Y2NmNmZhZTllZTZiODcxYiJ9fX0=
        name: '&e&lM'
      '5':
        material: cps= eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvYjU1MzE0MWFhYmU4OWE4YTU4MDRhMTcyMTMzYjQzZDVkMGVlMDU0OWNjMTlkYjAzODU2ODQwNDNjZmE5NDZhNSJ9fX0=
        name: '&e&lP'
      '6':
        material: cps= eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvMjA2YmM0MTdlM2MwNmIyMjczNWQ1MzlmOWM2YzhmZDdjMWVmZDE5MjM2ZTJjMzgxNTM0MDUxZDlkNmJlZTgwNCJ9fX0=
        name: '&e&lL'
      '7':
        material: cps= eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvYjc3MTY1YzlkYjc2M2E5YWNkMTNjMDYyMjBlOTJkM2M5NzBkZmEzNmRhYzU2ZTU5NTdkMDJkMzZmNWE5ZjBiOCJ9fX0=
        name: '&e&lE'
      '15':
        material: IRON_SWORD
        name: '&f这把剑的耐久有损耗'
        damage: 20
      '17':
        material: LEATHER_HELMET
        name: '&a绿&f头盔'
        leatherarmor: GREEN
      '18':
        material: BREAD
        name: '&f面包的价格是二十块钱'
        commands:
        - paywall= 20
        - give-item= bread
      '19':
        material: APPLE
        name: '&f点击改变物件'
        commands:
        - placeholder= [item:GOLDEN_APPLE]
        - refresh
        has0:
          material: GOLDEN_APPLE
          compare0: '%cp-item%'
          value0: GOLDEN_APPLE
          name: '&f点击改变物件'
          commands:
          - placeholder= [item:APPLE]
          - refresh
      '21':
        material: POTION
        name: '&f点击治疗玩家'
        potion: INSTANT_HEAL
        lore:
        - '&7使用 /heal 命令'
        - '&7需要玩家有权限'
        commands:
        - heal
      '24':
        material: BOW
        name: '&f这是一把附魔弓'
        enchanted: true
      '26':
        material: LEATHER_CHESTPLATE
        name: '&e黄&f胸甲'
        leatherarmor: YELLOW
      '27':
        material: COOKED_BEEF
        name: '&f补充饥饿条'
        lore:
        - '&7使用 /feed 命令'
        commands:
        - feed
      '28':
        material: COOKED_PORKCHOP
        name: '&f发送信息'
        lore:
        - '&7每个玩家只能使用一次'
        commands:
        - set-data= example_item true
        - msg= &f该信息只能发送一次
        - refresh
        has0:
          compare0: '%cp-data-example_item%'
          value0: true
          material: BARRIER
          name: '&c物件已经用过啦！'
      '30':
        material: COMPASS
        name: '&f传送至家'
        commands:
        - home
        - cpc
        - title= %cp-player-name% 20 60 20 &e欢迎回家！/n/&2%cp-player-displayname%
      '33':
        material: ARROW
        name: '&f可堆叠的物件'
        stack: 16
      '35':
        material: LEATHER_LEGGINGS
        name: '&c红&f护腿'
        leatherarmor: RED
      '42':
        material: IRON_AXE
        name: '#4eabd1疯狂#b6d1ea颜色'
        lore:
        - '&7在 1.16+ 可以使用十六进制颜色编码！'
      '44':
        material: LEATHER_BOOTS
        name: '&6橘&f靴子'
        leatherarmor: ORANGE
      '45':
        material: RED_WOOL
        name: '&c最小化面板'
        commands:
        - close= Middle
        - close= Bottom
      '46':
        material: LIME_WOOL
        name: '&a重置面板底部'
        commands:
        - open= example_middle_one {Middle}
        - open= example_bottom {Bottom}
```

### **example\_middle\_one.yml**

```yaml
# |------------------------------------------------------------------------
# | CommandPanels 样例文件
# | By RockyHawk v3.1
# | 汉化: inuEbisu
# | Spigot MC: https://www.spigotmc.org/resources/command-panels-custom-guis.67788/
# | MCBBS: https://www.mcbbs.net/thread-1412767-1-1.html
# |------------------------------------------------------------------------

panels:
  example_middle_one:
    perm: default
    rows: 3
    title: 样例
    animatevalue: 15
    refresh-delay: 5
    panelType:
    - nocommand
    empty: YELLOW_STAINED_GLASS_PANE
    item:
      '0':
        material: AIR
        stack: 1
        name: ''
        animate0:
          material: PUFFERFISH
          name: '&e河豚 Rhys'
      '1':
        material: AIR
        stack: 1
        name: ''
        animate1:
          material: PUFFERFISH
          name: '&e河豚 Rhys'
      '2':
        material: AIR
        stack: 1
        name: ''
        animate2:
          material: PUFFERFISH
          name: '&e河豚 Rhys'
      '3':
        material: AIR
        stack: 1
        name: ''
        animate3:
          material: PUFFERFISH
          name: '&e河豚 Rhys'
      '5':
        material: AIR
        stack: 1
        name: ''
        animate9:
          material: PUFFERFISH
          name: '&e河豚 Rhys'
      '6':
        material: AIR
        stack: 1
        name: ''
        animate10:
          material: PUFFERFISH
          name: '&e河豚 Rhys'
      '7':
        material: AIR
        stack: 1
        name: ''
        animate11:
          material: PUFFERFISH
          name: '&e河豚 Rhys'
      '12':
        material: AIR
        stack: 1
        name: ''
        animate4:
          material: PUFFERFISH
          name: '&e河豚 Rhys'
      '14':
        material: AIR
        stack: 1
        name: ''
        animate8:
          material: PUFFERFISH
          name: '&e河豚 Rhys'
      '16':
        material: AIR
        stack: 1
        name: ''
        animate12:
          material: PUFFERFISH
          name: '&e河豚 Rhys'
      '21':
        material: AIR
        stack: 1
        name: ''
        animate5:
          material: PUFFERFISH
          name: '&e河豚 Rhys'
      '22':
        material: AIR
        stack: 1
        name: ''
        animate6:
          material: PUFFERFISH
          name: '&e河豚 Rhys'
      '23':
        material: AIR
        stack: 1
        name: ''
        animate7:
          material: PUFFERFISH
          name: '&e河豚 Rhys'
      '25':
        material: AIR
        stack: 1
        name: ''
        animate13:
          material: PUFFERFISH
          name: '&e河豚 Rhys'
      '26':
        material: AIR
        stack: 1
        name: ''
        animate14:
          material: PUFFERFISH
          name: '&e河豚 Rhys'
```

### **example\_middle\_two.yml**

```yaml
# |------------------------------------------------------------------------
# | CommandPanels 样例文件
# | By RockyHawk v3.1
# | 汉化: inuEbisu
# | Spigot MC: https://www.spigotmc.org/resources/command-panels-custom-guis.67788/
# | MCBBS: https://www.mcbbs.net/thread-1412767-1-1.html
# |------------------------------------------------------------------------

panels:
  example_middle_two:
    perm: default
    rows: 4
    title: '&e&l在线浏览 - 第 $cp-data-nextpage$ 页'
    empty: LIGHT_BLUE_STAINED_GLASS_PANE
    panelType:
    - nocommand
    placeholders:
      primary:
        start: $
        end: $
      secondary:
        start: '{'
        end: '}'
    pre-load-commands:
    - add-data= onlinepage 0
    - add-data= nextpage 1
    item:
      '10':
        material: cps= $cp-player-online-%math_1+14*{cp-data-onlinepage}%$
        name: '&e$cp-player-online-%math_1+14*{cp-data-onlinepage}%$'
        has0:
          compare0: $cp-player-online-%math_1+14*{cp-data-onlinepage}%$
          value0: Offline
          material: cps= eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvZmMyNzEwNTI3MTllZjY0MDc5ZWU4YzE0OTg5NTEyMzhhNzRkYWM0YzI3Yjk1NjQwZGI2ZmJkZGMyZDZiNWI2ZSJ9fX0=
          stack: 1
          name: '&7&l????'
      '11':
        material: cps= $cp-player-online-%math_2+14*{cp-data-onlinepage}%$
        name: '&e$cp-player-online-%math_2+14*{cp-data-onlinepage}%$'
        has0:
          compare0: '&e$cp-player-online-%math_2+14*{cp-data-onlinepage}%$'
          value0: Offline
          material: cps= eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvZmMyNzEwNTI3MTllZjY0MDc5ZWU4YzE0OTg5NTEyMzhhNzRkYWM0YzI3Yjk1NjQwZGI2ZmJkZGMyZDZiNWI2ZSJ9fX0=
          stack: 1
          name: '&7&l????'
      '12':
        material: cps= $cp-player-online-%math_3+14*{cp-data-onlinepage}%$
        name: '&e$cp-player-online-%math_3+14*{cp-data-onlinepage}%$'
        has0:
          compare0: '&e$cp-player-online-%math_3+14*{cp-data-onlinepage}%$'
          value0: Offline
          material: cps= eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvZmMyNzEwNTI3MTllZjY0MDc5ZWU4YzE0OTg5NTEyMzhhNzRkYWM0YzI3Yjk1NjQwZGI2ZmJkZGMyZDZiNWI2ZSJ9fX0=
          stack: 1
          name: '&7&l????'
      '13':
        material: cps= $cp-player-online-%math_4+14*{cp-data-onlinepage}%$
        name: '&e$cp-player-online-%math_4+14*{cp-data-onlinepage}%$'
        has0:
          compare0: '&e$cp-player-online-%math_4+14*{cp-data-onlinepage}%$'
          value0: Offline
          material: cps= eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvZmMyNzEwNTI3MTllZjY0MDc5ZWU4YzE0OTg5NTEyMzhhNzRkYWM0YzI3Yjk1NjQwZGI2ZmJkZGMyZDZiNWI2ZSJ9fX0=
          stack: 1
          name: '&7&l????'
      '14':
        material: cps= $cp-player-online-%math_5+14*{cp-data-onlinepage}%$
        name: '&e$cp-player-online-%math_5+14*{cp-data-onlinepage}%$'
        has0:
          compare0: '&e$cp-player-online-%math_5+14*{cp-data-onlinepage}%$'
          value0: Offline
          material: cps= eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvZmMyNzEwNTI3MTllZjY0MDc5ZWU4YzE0OTg5NTEyMzhhNzRkYWM0YzI3Yjk1NjQwZGI2ZmJkZGMyZDZiNWI2ZSJ9fX0=
          stack: 1
          name: '&7&l????'
      '15':
        material: cps= $cp-player-online-%math_6+14*{cp-data-onlinepage}%$
        name: '&e$cp-player-online-%math_6+14*{cp-data-onlinepage}%$'
        has0:
          compare0: '&e$cp-player-online-%math_6+14*{cp-data-onlinepage}%$'
          value0: Offline
          material: cps= eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvZmMyNzEwNTI3MTllZjY0MDc5ZWU4YzE0OTg5NTEyMzhhNzRkYWM0YzI3Yjk1NjQwZGI2ZmJkZGMyZDZiNWI2ZSJ9fX0=
          stack: 1
          name: '&7&l????'
      '16':
        material: cps= $cp-player-online-%math_7+14*{cp-data-onlinepage}%$
        name: '&e$cp-player-online-%math_7+14*{cp-data-onlinepage}%$'
        has0:
          compare0: '&e$cp-player-online-%math_7+14*{cp-data-onlinepage}%$'
          value0: Offline
          material: cps= eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvZmMyNzEwNTI3MTllZjY0MDc5ZWU4YzE0OTg5NTEyMzhhNzRkYWM0YzI3Yjk1NjQwZGI2ZmJkZGMyZDZiNWI2ZSJ9fX0=
          stack: 1
          name: '&7&l????'
      '19':
        material: cps= $cp-player-online-%math_8+14*{cp-data-onlinepage}%$
        name: '&e$cp-player-online-%math_8+14*{cp-data-onlinepage}%$'
        has0:
          compare0: '&e$cp-player-online-%math_8+14*{cp-data-onlinepage}%$'
          value0: Offline
          material: cps= eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvZmMyNzEwNTI3MTllZjY0MDc5ZWU4YzE0OTg5NTEyMzhhNzRkYWM0YzI3Yjk1NjQwZGI2ZmJkZGMyZDZiNWI2ZSJ9fX0=
          stack: 1
          name: '&7&l????'
      '20':
        material: cps= $cp-player-online-%math_9+14*{cp-data-onlinepage}%$
        name: '&e$cp-player-online-%math_9+14*{cp-data-onlinepage}%$'
        has0:
          compare0: '&e$cp-player-online-%math_9+14*{cp-data-onlinepage}%$'
          value0: Offline
          material: cps= eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvZmMyNzEwNTI3MTllZjY0MDc5ZWU4YzE0OTg5NTEyMzhhNzRkYWM0YzI3Yjk1NjQwZGI2ZmJkZGMyZDZiNWI2ZSJ9fX0=
          stack: 1
          name: '&7&l????'
      '21':
        material: cps= $cp-player-online-%math_10+14*{cp-data-onlinepage}%$
        name: '&e$cp-player-online-%math_10+14*{cp-data-onlinepage}%$'
        has0:
          compare0: '&e$cp-player-online-%math_10+14*{cp-data-onlinepage}%$'
          value0: Offline
          material: cps= eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvZmMyNzEwNTI3MTllZjY0MDc5ZWU4YzE0OTg5NTEyMzhhNzRkYWM0YzI3Yjk1NjQwZGI2ZmJkZGMyZDZiNWI2ZSJ9fX0=
          stack: 1
          name: '&7&l????'
      '22':
        material: cps= $cp-player-online-%math_11+14*{cp-data-onlinepage}%$
        name: '&e$cp-player-online-%math_11+14*{cp-data-onlinepage}%$'
        has0:
          compare0: '&e$cp-player-online-%math_11+14*{cp-data-onlinepage}%$'
          value0: Offline
          material: cps= eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvZmMyNzEwNTI3MTllZjY0MDc5ZWU4YzE0OTg5NTEyMzhhNzRkYWM0YzI3Yjk1NjQwZGI2ZmJkZGMyZDZiNWI2ZSJ9fX0=
          stack: 1
          name: '&7&l????'
      '23':
        material: cps= $cp-player-online-%math_12+14*{cp-data-onlinepage}%$
        name: '&e$cp-player-online-%math_12+14*{cp-data-onlinepage}%$'
        has0:
          compare0: '&e$cp-player-online-%math_12+14*{cp-data-onlinepage}%$'
          value0: Offline
          material: cps= eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvZmMyNzEwNTI3MTllZjY0MDc5ZWU4YzE0OTg5NTEyMzhhNzRkYWM0YzI3Yjk1NjQwZGI2ZmJkZGMyZDZiNWI2ZSJ9fX0=
          stack: 1
          name: '&7&l????'
      '24':
        material: cps= $cp-player-online-%math_13+14*{cp-data-onlinepage}%$
        name: '&e$cp-player-online-%math_13+14*{cp-data-onlinepage}%$'
        has0:
          compare0: '&e$cp-player-online-%math_13+14*{cp-data-onlinepage}%$'
          value0: Offline
          material: cps= eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvZmMyNzEwNTI3MTllZjY0MDc5ZWU4YzE0OTg5NTEyMzhhNzRkYWM0YzI3Yjk1NjQwZGI2ZmJkZGMyZDZiNWI2ZSJ9fX0=
          stack: 1
          name: '&7&l????'
      '25':
        material: cps= $cp-player-online-%math_14+14*{cp-data-onlinepage}%$
        name: '&e$cp-player-online-%math_14+14*{cp-data-onlinepage}%$'
        has0:
          compare0: '&e$cp-player-online-%math_14+14*{cp-data-onlinepage}%$'
          value0: Offline
          material: cps= eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvZmMyNzEwNTI3MTllZjY0MDc5ZWU4YzE0OTg5NTEyMzhhNzRkYWM0YzI3Yjk1NjQwZGI2ZmJkZGMyZDZiNWI2ZSJ9fX0=
          stack: 1
          name: '&7&l????'
      '2':
        material: LIGHT_BLUE_STAINED_GLASS_PANE
        name: '&f'
        has0:
          value0: NOT 0 ISGREATER
          compare0: $cp-data-onlinepage$
          material: STICK
          stack: 1
          name: '&c&l最后一页'
          commands:
          - math-data= onlinepage -1
          - math-data= nextpage -1
          - refresh
      '6':
        material: ARROW
        stack: 1
        name: '&e&l下一页'
        commands:
        - math-data= onlinepage +1
        - math-data= nextpage +1
        - refresh
      '4':
        material: OAK_SIGN
        name: '&e&l在线玩家'
        lore:
        - '&b$cp-online-players$'
        - ''
        - '&8玩家浏览器'
        - '&8by: TinyTank800'
```

### **example\_bottom.yml**

```yaml
# |------------------------------------------------------------------------
# | CommandPanels 样例文件
# | By RockyHawk v3.1
# | 汉化: inuEbisu
# | Spigot MC: https://www.spigotmc.org/resources/command-panels-custom-guis.67788/
# | MCBBS: https://www.mcbbs.net/thread-1412767-1-1.html
# |------------------------------------------------------------------------

panels:
  example_bottom:
    perm: default
    rows: 3
    title: 样例
    empty: LIGHT_BLUE_STAINED_GLASS_PANE
    panelType:
    - nocommand
    item:
      '0':
        material: BARRIER
        name: '&c关闭面板'
        commands:
        - cpc
      '4':
        material: cps= self
        name: '&7名称: &eRockyHawk'
        lore:
        - ''
        - '&8样例面板'
        - '&8by: RockyHawk'
      '8':
        material: ENDER_PEARL
        name: '&b打开玩家浏览器'
        lore:
        - '&7玩家浏览器需要'
        - '&7由 Math 扩展的 PlaceholderAPI'
        has1:
          compare0: '%math_0:_1+1%'
          value0: '2'
          material: ENDER_PEARL
          name: '&b打开玩家浏览器'
          commands:
          - open= example_middle_two {Middle}
        has0:
          compare0: '%cp-data-example_item%'
          value0: true
          material: COOKED_PORKCHOP
          name: '&f秘密物件'
          lore:
          - '&7点我，我准你再次'
          - '&7使用只有一次的消息'
          commands:
          - set-data= example_item false
          - refresh
```
