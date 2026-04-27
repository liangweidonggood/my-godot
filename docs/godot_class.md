# 场景

Godot 游戏就是由场景构成的树状结构，而每一个场景又是一个由节点构成的树状结构

本质上，Godot 编辑器就是一个 **场景编辑器** 。它有很多用于编辑 2D 和 3D 场景以及用户界面的工具。Godot 项目中可以包含任意数量的场景。引擎只要求将其中之一设为程序的 **主场景** 。这是你或者玩家运行游戏时，Godot 最初加载的场景。

## 节点node

**节点是你的游戏的基本构件** 。它们就像食谱里的食材。节点是 Godot 的基本单元。它们可以成为另一个节点的子节点，从而形成树状排列。

### 2d-1-dodge_the_creeps用到的节点

| 分类   | 根节点      | 二级节点                | 三级节点     | 说明                           |
| ------ | ----------- | ----------------------- | ------------ | ------------------------------ |
| 玩家   | Area2D      |                         |              | 命名：Player                   |
|        |             | AnimatedSprite2D        |              |                                |
|        |             | CollisionShape2D        |              |                                |
|        |             | GPUParticles2D          |              | 命名：Trail 角色移动的规迹特效 |
| 敌人   | RigidBody2D |                         |              | 命名：Mob                      |
|        |             | AnimatedSprite2D        |              |                                |
|        |             | CollisionShape2d        |              |                                |
|        |             | VisibleOnScreenNotifier |              |                                |
| 记分板 | CanvasLayer |                         |              | 命名：HUD                      |
|        |             | Label                   |              |                                |
|        |             | Button                  |              |                                |
|        |             | Timer                   |              |                                |
| 主场景 | Node        |                         |              | 命名：Main                     |
|        |             | ColorRect               |              |                                |
|        |             | Timer                   |              |                                |
|        |             | Marker2D                |              |                                |
|        |             | Path2D                  |              |                                |
|        |             |                         | PathFollow2D |                                |
|        |             | AudioStreamPlayer       |              |                                |

### 3d-1-squash-the-creeps用到的节点

| 分类     | 根节点          | 二级节点           | 三级节点         | 说明                   |
| -------- | --------------- | ------------------ | ---------------- | ---------------------- |
| 主场景   | Node            |                    |                  | Main                   |
|          |                 | StaticBody3D       |                  | Ground                 |
|          |                 |                    | CollisionShape3D |                        |
|          |                 |                    | MeshInstance3D   |                        |
|          |                 | DirectionalLight3D |                  | 平行光                 |
| 玩家场景 | CharacterBody3D |                    |                  | Player                 |
|          |                 | Node3D             |                  | Pivot                  |
|          |                 |                    | Node3d           | player.glb, Character |
|          |                 | CollisionShape3D   |                  |                        |
|          |                 |                    |                  |                        |

.
