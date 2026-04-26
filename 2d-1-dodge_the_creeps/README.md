# Dodge the Creeps 2D assets

Used by the "Your first 2D game" tutorial:

https://docs.godotengine.org/en/latest/getting_started/first_2d_game/index.html

## 项目目录结构

```
2d-1-dodge_the_creeps/
├── .editorconfig       # 编辑器代码风格配置（缩进、换行等）
├── .godot/             # Godot 引擎缓存（已忽略，不跨环境同步）
│   ├── imported/        # 导入的资源缓存
│   └── editor/          # 编辑器临时文件
├── art/                # 游戏美术资源
│   ├── enemyFlyingAlt_1.png  # 飞行敌怪帧1
│   ├── enemyFlyingAlt_2.png  # 飞行敌怪帧2
│   ├── enemySwimming_1.png  # 游泳敌怪帧1
│   ├── enemySwimming_2.png  # 游泳敌怪帧2
│   ├── enemyWalking_1.png   # 行走敌怪帧1
│   ├── enemyWalking_2.png   # 行走敌怪帧2
│   ├── playerGrey_up1.png   # 玩家站立帧1
│   ├── playerGrey_up2.png   # 玩家站立帧2
│   ├── playerGrey_walk1.png # 玩家行走帧1
│   ├── playerGrey_walk2.png # 玩家行走帧2
│   ├── House In a Forest Loop.ogg  # 背景音乐
│   └── gameover.wav         # 游戏结束音效
├── fonts/              # 字体资源
│   ├── Xolonium-Regular.ttf  # 主字体文件
│   ├── FONTLOG.txt          # 字体日志
│   └── LICENSE.txt          # 字体许可证
├── build/              # 构建输出目录（已忽略）
├── main.tscn          # 主场景
├── main.gd             # 主逻辑脚本
├── main.gd.uid        # 脚本 UID
├── player.tscn        # 玩家场景
├── player.gd          # 玩家脚本
├── player.gd.uid      # 脚本 UID
├── mob.tscn           # 敌怪场景
├── mob.gd             # 敌怪脚本
├── mob.gd.uid         # 脚本 UID
├── hud.tscn           # HUD 场景
├── hud.gd             # HUD 脚本
├── hud.gd.uid         # 脚本 UID
├── icon.svg            # 项目图标
├── export_presets.cfg # 导出预设配置
└── project.godot       # 项目配置文件（必须提交）
```

## 创建项目

![1777208480764](image/README/1777208480764.png)

素材包：https://github.com/godotengine/godot-docs-project-starters/releases/download/latest-4.x/dodge_the_creeps_2d_assets.zip

包含贴图，字体和音乐

### 项目配置

![1777208645792](image/README/1777208645792.png)

### 键盘映射

![1777208691488](image/README/1777208691488.png)

![1777208845800](image/README/1777208845800.png)

![1777208887424](image/README/1777208887424.png)

按键盘自动添加事件

![1777208908758](image/README/1777208908758.png)

## 1.Player场景

### 节点Area2D

https://docs.godotengine.org/zh-cn/4.x/classes/class_area2d.html#class-area2d

可以检测到与玩家重叠或进入玩家内的物体

![1777209046309](image/README/1777209046309.png)

配置

![1777210691018](image/README/1777210691018.png)

信号，脚本使用

![1777209981552](image/README/1777209981552.png)

#### 精灵动画AnimatedSprite2D

https://docs.godotengine.org/zh-cn/4.x/classes/class_animatedsprite2d.html#class-animatedsprite2d

为我们的玩家处理外观和动画

![1777209148749](image/README/1777209148749.png)

一个 `AnimatedSprite2D`需要一个 [SpriteFrames](https://docs.godotengine.org/zh-cn/4.x/classes/class_spriteframes.html#class-spriteframes) 资源，这是它可以显示的动画的列表。

![1777209622286](image/README/1777209622286.png)

点击添加动画

![1777209686969](image/README/1777209686969.png)

缩小图像，Scale改成0.5

![1777209728439](image/README/1777209728439.png)

#### 碰撞[CollisionShape2D](https://docs.godotengine.org/zh-cn/4.x/classes/class_collisionshape2d.html#class-collisionshape2d)

https://docs.godotengine.org/zh-cn/4.x/classes/class_collisionshape2d.html#class-collisionshape2d


![1777209816390](image/README/1777209816390.png)

配置形状CapsuleShape2D

![1777209895118](image/README/1777209895118.png)

#### 粒子特效GPUParticles2D

![1777210079765](image/README/1777210079765.png)

配置1

![1777210147430](image/README/1777210147430.png)

Time

![1777210178743](image/README/1777210178743.png)

Drawing

![1777210223165](image/README/1777210223165.png)

Process Material 

![1777210268250](image/README/1777210268250.png)

Gravity

![1777210305438](image/README/1777210305438.png)

Scale Curve

![1777210329976](image/README/1777210329976.png)

Curve

![1777210360295](image/README/1777210360295.png)

Color Ramp

![1777210400159](image/README/1777210400159.png)

Colors

![1777210441597](image/README/1777210441597.png)

0: ffffff80

1: ffffff00

Transform和Ordering

![1777210523270](image/README/1777210523270.png)

### 玩家脚本

```plaintext
extends Area2D

signal hit

@export var speed = 400 # How fast the player will move (pixels/sec).
var screen_size # Size of the game window.

func _ready():
	screen_size = get_viewport_rect().size
	hide()


func _process(delta):
	var velocity = Vector2.ZERO # The player's movement vector.
	if Input.is_action_pressed(&"move_right"):
		velocity.x += 1
	if Input.is_action_pressed(&"move_left"):
		velocity.x -= 1
	if Input.is_action_pressed(&"move_down"):
		velocity.y += 1
	if Input.is_action_pressed(&"move_up"):
		velocity.y -= 1

	if velocity.length() > 0:
		velocity = velocity.normalized() * speed
		$AnimatedSprite2D.play()
	else:
		$AnimatedSprite2D.stop()

	position += velocity * delta
	position = position.clamp(Vector2.ZERO, screen_size)

	if velocity.x != 0:
		$AnimatedSprite2D.animation = &"right"
		$AnimatedSprite2D.flip_v = false
		$Trail.rotation = 0
		$AnimatedSprite2D.flip_h = velocity.x < 0
	elif velocity.y != 0:
		$AnimatedSprite2D.animation = &"up"
		rotation = PI if velocity.y > 0 else 0


func start(pos):
	position = pos
	rotation = 0
	show()
	$CollisionShape2D.disabled = false


func _on_body_entered(_body):
	hide() # Player disappears after being hit.
	hit.emit()
	# Must be deferred as we can't change physics properties on a physics callback.
	$CollisionShape2D.set_deferred(&"disabled", true)

```

## 2.Mob敌人场景RigidBody2D

https://docs.godotengine.org/zh-cn/4.x/classes/class_rigidbody2d.html#class-rigidbody2d

由物理仿真进行移动的 2D 物理体。

![1777211481049](image/README/1777211481049.png)

配置以防止怪物向下坠落

![1777211567347](image/README/1777211567347.png)

确保怪物们不会相互碰撞

![1777211628263](image/README/1777211628263.png)


### 精灵动画AnimatedSprite2D

![1777211903950](image/README/1777211903950.png)


### 碰撞CollisionShape2d

![1777211967955](image/README/1777211967955.png)

### 屏幕通知VisibleOnScreenNotifier

![1777212017782](image/README/1777212017782.png)

### 敌人脚本

```plaintext
extends RigidBody2D

func _ready():
	var mob_types = Array($AnimatedSprite2D.sprite_frames.get_animation_names())
	$AnimatedSprite2D.animation = mob_types.pick_random()
	$AnimatedSprite2D.play()


func _on_VisibilityNotifier2D_screen_exited():
	queue_free()
```

## 3.HUD记分板场景CanvasLayer

https://docs.godotengine.org/zh-cn/4.x/classes/class_canvaslayer.html#class-canvaslayer

![1777212102746](image/README/1777212102746.png)

### 得分标签ScoreLable

![1777212165030](image/README/1777212165030.png)

![1777212213434](image/README/1777212213434.png)

![1777212243983](image/README/1777212243983.png)

![1777212262349](image/README/1777212262349.png)

### 信息提示标签MessageLabel

![1777212301632](image/README/1777212301632.png)

![1777212331900](image/README/1777212331900.png)![1777212345597](image/README/1777212345597.png)

### 开始按钮StartButton

![1777212381111](image/README/1777212381111.png)

绑快捷键

![1777212421147](image/README/1777212421147.png)

![1777212444741](image/README/1777212444741.png)

![1777212521634](image/README/1777212521634.png)

### 信息记时器MessageTimer

![1777212473041](image/README/1777212473041.png)

![1777212486606](image/README/1777212486606.png)

### 记分板脚本

```plaintext
extends CanvasLayer

signal start_game

func show_message(text):
	$MessageLabel.text = text
	$MessageLabel.show()
	$MessageTimer.start()


func show_game_over():
	show_message("Game Over")
	await $MessageTimer.timeout
	$MessageLabel.text = "Dodge the\nCreeps"
	$MessageLabel.show()
	await get_tree().create_timer(1).timeout
	$StartButton.show()


func update_score(score):
	$ScoreLabel.text = str(score)


func _on_StartButton_pressed():
	$StartButton.hide()
	start_game.emit()


func _on_MessageTimer_timeout():
	$MessageLabel.hide()

```

## 4.Main场景Node

https://docs.godotengine.org/zh-cn/4.x/classes/class_node.html#class-node

![1777212593830](image/README/1777212593830.png)



### 导入敌人场景

![1777212648017](image/README/1777212648017.png)

### 背景ColorRect


![1777212674819](image/README/1777212674819.png)

颜色：385f61

![1777212716726](image/README/1777212716726.png)

### 导入玩家

![1777212775750](image/README/1777212775750.png)

### 敌人记时器MobTimer

![1777212815814](image/README/1777212815814.png)

![1777212829845](image/README/1777212829845.png)

### 得分记时器ScoreTimer

![1777212854976](image/README/1777212854976.png)

### 开始记时器StartTimer

![1777212871101](image/README/1777212871101.png)

![1777212882958](image/README/1777212882958.png)

### 开始位置StartPosition

![1777212905219](image/README/1777212905219.png)


### 敌人路线MobPath

![1777212946122](image/README/1777212946122.png)


#### 敌人路径MobSpawnLocation

![1777212976000](image/README/1777212976000.png)

### 导入HUD

![1777212990959](image/README/1777212990959.png)

### 背景音乐

![1777213029960](image/README/1777213029960.png)

![1777213014247](image/README/1777213014247.png)

### 死亡音乐

![1777213056812](image/README/1777213056812.png)

### 脚本

```plaintext
extends Node

@export var mob_scene: PackedScene
var score


func game_over():
	$ScoreTimer.stop()
	$MobTimer.stop()
	$HUD.show_game_over()
	$Music.stop()
	$DeathSound.play()


func new_game():
	get_tree().call_group(&"mobs", &"queue_free")
	score = 0
	$Player.start($StartPosition.position)
	$StartTimer.start()
	$HUD.update_score(score)
	$HUD.show_message("Get Ready")
	$Music.play()


func _on_MobTimer_timeout():
	# Create a new instance of the Mob scene.
	var mob = mob_scene.instantiate()

	# Choose a random location on Path2D.
	var mob_spawn_location = get_node(^"MobPath/MobSpawnLocation")
	mob_spawn_location.progress_ratio = randf()

	# Set the mob's position to a random location.
	mob.position = mob_spawn_location.position

	# Set the mob's direction perpendicular to the path direction.
	var direction = mob_spawn_location.rotation + PI / 2

	# Add some randomness to the direction.
	direction += randf_range(-PI / 4, PI / 4)
	mob.rotation = direction

	# Choose the velocity for the mob.
	var velocity = Vector2(randf_range(150.0, 250.0), 0.0)
	mob.linear_velocity = velocity.rotated(direction)

	# Spawn the mob by adding it to the Main scene.
	add_child(mob)


func _on_ScoreTimer_timeout():
	score += 1
	$HUD.update_score(score)


func _on_StartTimer_timeout():
	$MobTimer.start()
	$ScoreTimer.start()

```

## 导出

![1777213121640](image/README/1777213121640.png)

![1777213099288](image/README/1777213099288.png)

## Git 忽略规则

- `.godot/` — 本地引擎缓存，跨环境不一致
- `*.import` — 导入元数据，含本地路径引用
- `build/` — 构建输出
