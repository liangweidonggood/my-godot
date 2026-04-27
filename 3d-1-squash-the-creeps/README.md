# Squash the Creeps

## Main主场景Node

我们先添加一个地板，以防止角色掉落。要创建地板、墙壁或天花板等静态碰撞器，可以使用 [StaticBody3D](https://docs.godotengine.org/zh-cn/4.x/classes/class_staticbody3d.html#class-staticbody3d) 节点。它们需要 [CollisionShape3D](https://docs.godotengine.org/zh-cn/4.x/classes/class_collisionshape3d.html#class-collisionshape3d) 子节点来定义碰撞区域。

![1777276019810](image/README/1777276019810.png)

![1777276048377](image/README/1777276048377.png)

![1777276298976](image/README/1777276298976.png)

创建形状

盒子形状非常适合平坦的地面和墙壁。它的厚度使它能够可靠地阻挡甚至快速移动的物体。

![1777276342961](image/README/1777276342961.png)

_Size_ 设置

![1777276435266](image/README/1777276435266.png)

碰撞形状是不可见的。我们需要添加一个与之配套的视觉层。选择 `Ground`节点并添加一个 [MeshInstance3D](https://docs.godotengine.org/zh-cn/4.x/classes/class_meshinstance3d.html#class-meshinstance3d) 作为其子节点。

![1777276493512](image/README/1777276493512.png)

在*检查器*中，点击 _Mesh_ 旁边的字段，创建一个 [BoxMesh](https://docs.godotengine.org/zh-cn/4.x/classes/class_boxmesh.html#class-boxmesh) 资源，创建一个可见的立方体。

![1777276594585](image/README/1777276594585.png)

再次设置大小

![1777276731139](image/README/1777276731139.png)

Ground

![1777277033469](image/README/1777277033469.png)

现在来添加一个平行光，让我们的整个场景不全都是灰色的。选择 `Main`节点，然后添加一个子节点 [DirectionalLight3D](https://docs.godotengine.org/zh-cn/4.x/classes/class_directionallight3d.html#class-directionallight3d)。

![1777277144048](image/README/1777277144048.png)

我们需要移动并旋转 [DirectionalLight3D](https://docs.godotengine.org/zh-cn/4.x/classes/class_directionallight3d.html#class-directionallight3d) 节点。通过单击并拖动操作器的绿色箭头将该节点往上移动，然后单击并拖动红色弧线以围绕 X 轴旋转它，直到地面被照亮。

在*检查器*中，点击复选框以启用*阴影*功能。

![1777277400066](image/README/1777277400066.png)

## 玩家场景

点击**其他节点**按钮，选择 `CharacterBody3D`节点类型，创建一个 [CharacterBody3D](https://docs.godotengine.org/zh-cn/4.x/classes/class_characterbody3d.html#class-characterbody3d) 作为根节点。

![1777277533025](image/README/1777277533025.png)

为 `Player`节点添加一个 [Node3D](https://docs.godotengine.org/zh-cn/4.x/classes/class_node3d.html#class-node3d) 子节点。

![1777277639689](image/README/1777277639689.png)

然后在文件系统面板中 `player.glb`拖放到 `Pivot` 节点上。改名为Character

![1777277750124](image/README/1777277750124.png)

与所有物理节点一样，我们需要为角色添加一个碰撞形状，让其能与环境发生碰撞。再次选中 `Player` 节点，为其添加一个子节点 [CollisionShape3D](https://docs.godotengine.org/zh-cn/4.x/classes/class_collisionshape3d.html#class-collisionshape3d)。在**检查器**中，点击 **形状（Shape）** 属性，新建一个 [SphereShape3D](https://docs.godotengine.org/zh-cn/4.x/classes/class_sphereshape3d.html#class-sphereshape3d)。

![1777277944430](image/README/1777277944430.png)

![1777278077917](image/README/1777278077917.png)

按键映射

![1777278155081](image/README/1777278155081.png)

![1777278170456](image/README/1777278170456.png)
