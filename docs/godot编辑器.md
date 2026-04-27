# 编辑器

## 项目结构

**Godot 命名规范** 遵循 GDScript 风格指南，核心原则是**一致性**。
主要规则：文件和节点使用蛇形命名法（snake_case），类名使用帕斯卡命名法（PascalCase），变量/函数使用蛇形命名法（snake_case）。

**具体规范如下：**

- **文件与文件夹：** **采用** `snake_case.ext`。例如：`player_controller.gd`, `main_menu.tscn`。
- **类名 (Class_name)：** **采用** `PascalCase`（大驼峰）。例如：`PlayerController`。
- **节点 (Nodes)：** **采用** `snake_case` **或** `PascalCase`（主要基于个人喜好，但建议小写字母开头），例如：`player_sprite` **或** `PlayerSprite`。
- **变量与函数：** **采用** `snake_case`（小写下划线）。例如：`player_speed`, `get_damage()`。
- **常量与枚举：** **采用** `SCREAMING_SNAKE_CASE`（全大写下划线）。例如：`MAX_HEALTH`, `STATE_IDLE`。
- **信号 (Signals)：** **采用** `snake_case`，过去式。例如：`health_changed`, `button_clicked`。

参考，后期持续迭代优化

```plaintext
Project/
├── build/                              # 构建输出目录（忽略）
├── export_presets.cfg                  # 导出预设配置
├── .gitignore                          # git忽略
├── .editorconfig                       # 编辑器代码风格配置
├── .godot/                             # Godot 引擎缓存（忽略）
├── docs/                               # 项目文档
├── assets/                             # 游戏资源目录
│   ├── fonts/                          # 字体文件
│   ├── sounds/                         # 音乐音效文件
│   └── sprites/                        # 精灵图集
├── scenes/                             # 场景文件
│   ├── player/                         # 玩家场景
│   │   ├── player.tscn                 # 玩家场景实例
│   │   ├── player.gd                   # 玩家场景脚本
│   │   └── player.gd.uid               # 玩家场景脚本uid
│   ├── mob/                            # 敌人场景
│   │   ├── mob.tscn                    # 敌人场景实例
│   │   ├── mob.gd                      # 敌人场景脚本
│   │   └── mob.gd.uid                  # 敌人场景脚本uid
│   ├── hud/                            # 记分板场景
│   │   ├── hud.tscn                    # 记分板场景实例
│   │   ├── hud.gd                      # 记分板场景脚本
│   │   └── hud.gd.uid                  # 记分板场景脚本uid
│   ├── main.tscn                       # 主场景实例
│   ├── main.gd                         # 主逻辑脚本
│   └── main.gd.uid                     # 主逻辑脚本uid
├── icon.svg                            # 项目图标
├── project.godot                       # 项目配置文件
└── README.md                           # 项目说明
```

.

# [Node](https://docs.godotengine.org/zh-cn/4.x/classes/class_node.html#class-node)

检查器配置

![1777254535880](image/godot编辑器/1777254535880.png)

## [CanvasItem](https://docs.godotengine.org/zh-cn/4.x/classes/class_canvasitem.html#class-canvasitem)

检查器配置

![1777254897548](image/godot编辑器/1777254897548.png)

### [Node2D](https://docs.godotengine.org/zh-cn/4.x/classes/class_node2d.html#class-node2d)

检查器配置

![1777254858609](image/godot编辑器/1777254858609.png)

#### [AnimatedSprite2D](https://docs.godotengine.org/zh-cn/4.x/classes/class_animatedsprite2d.html)

检查器配置

![1777255113634](image/godot编辑器/1777255113634.png)

#### [CollisionShape2D](https://docs.godotengine.org/zh-cn/4.x/classes/class_collisionshape2d.html)

检查器配置

![1777255358354](image/godot编辑器/1777255358354.png)

#### [CollisionObject2D](https://docs.godotengine.org/zh-cn/4.x/classes/class_collisionobject2d.html#class-collisionobject2d)

检查器配置

![1777254828653](image/godot编辑器/1777254828653.png)

##### [Area2D](https://docs.godotengine.org/zh-cn/4.x/classes/class_area2d.html#class-area2d)

检查器配置

![1777254760207](image/godot编辑器/1777254760207.png)

##### [RigidBody2D](https://docs.godotengine.org/zh-cn/4.x/classes/class_rigidbody2d.html)

父类：PhysicsBody2D https://docs.godotengine.org/zh-cn/4.x/classes/class_physicsbody2d.html

检查器配置

![1777256493310](image/godot编辑器/1777256493310.png)

#### [GPUParticles2D](https://docs.godotengine.org/zh-cn/4.x/classes/class_gpuparticles2d.html)

检查器配置

![1777255515600](image/godot编辑器/1777255515600.png)

#### [VisibleOnScreenNotifier2D](https://docs.godotengine.org/zh-cn/4.x/classes/class_visibleonscreennotifier2d.html)

检查器配置

![1777255711948](image/godot编辑器/1777255711948.png)

#### Marker2D

https://docs.godotengine.org/zh-cn/4.x/classes/class_marker2d.html

检查器配置

![1777257398256](image/godot编辑器/1777257398256.png)

#### Path2D

https://docs.godotengine.org/zh-cn/4.x/classes/class_path2d.html

检查器配置

![1777257480128](image/godot编辑器/1777257480128.png)

#### PathFollow2D

https://docs.godotengine.org/zh-cn/4.x/classes/class_pathfollow2d.html

检查器配置

![1777257532245](image/godot编辑器/1777257532245.png)

### [Control](https://docs.godotengine.org/zh-cn/4.x/classes/class_control.html)

检查器配置

![1777256875564](image/godot编辑器/1777256875564.png)

#### [Label](https://docs.godotengine.org/zh-cn/4.x/classes/class_label.html)

检查器配置

![1777256900413](image/godot编辑器/1777256900413.png)

#### BaseButton

https://docs.godotengine.org/zh-cn/4.x/classes/class_basebutton.html

检查器配置

![1777257161270](image/godot编辑器/1777257161270.png)

##### Button

https://docs.godotengine.org/zh-cn/4.x/classes/class_button.html

检查器配置

![1777257139775](image/godot编辑器/1777257139775.png)

#### ColorRect

https://docs.godotengine.org/zh-cn/4.x/classes/class_colorrect.html

检查器配置

![1777257317831](image/godot编辑器/1777257317831.png)

## [CanvasLayer](https://docs.godotengine.org/zh-cn/4.x/classes/class_canvaslayer.html)

检查器配置

![1777255845054](image/godot编辑器/1777255845054.png)

## Timer

https://docs.godotengine.org/zh-cn/4.x/classes/class_timer.html

检查器配置

![1777257218382](image/godot编辑器/1777257218382.png)

## AudioStreamPlayer

https://docs.godotengine.org/zh-cn/4.x/classes/class_audiostreamplayer.html

检查器配置

![1777257628888](image/godot编辑器/1777257628888.png)
