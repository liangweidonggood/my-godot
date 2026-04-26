# CLAUDE.md

## 项目结构

- `2d-1/` - 第一个 2D Godot 子项目

## 开发规范

1. 子项目单独开发，统一在主仓库管理
2. 提交前确认 .gitignore 已包含目标忽略项

## Godot 项目规范

- `.godot/` 缓存目录用 `/.godot/` 精确匹配（防止 `*.godot` 误匹配 project.godot）
- `*.import` 文件是本地导入元数据，不需要提交
- `*.uid` 文件（脚本 UID）是 Godot 4.x 追踪机制，必须提交
- `project.godot` 是项目配置文件，必须提交，不能忽略

## Windows Git 操作规范

- 使用 `git -C <绝对路径>` 代替 cd 持久化问题
- GitHub 仓库删除需先 `gh auth refresh -s delete_repo` 授权
- 子目录禁止创建 .gitignore，统一在 root 管理

## 仓库结构

- 多子项目 monorepo 结构，主仓库根目录是唯一入口
- .claude/ 目录存放所有 AI 辅助配置，不可污染根目录
