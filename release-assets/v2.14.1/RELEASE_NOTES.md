# Sub2API CodexLink v2.14.1

## 修复

- 修复官方账号切换到 Sub2API 后，部分任务只出现在 `Recents`、项目文件夹显示 `No chats` 的问题。
- 不再把全部任务强制写入 `projectless-thread-ids`。
- 保留已有 `thread-project-assignments`，并依据任务 `cwd` 与本地项目 `rootPaths` 补建缺失归属。
- 同步重建 `sidebar-project-thread-orders` 和 `thread-workspace-root-hints`。
- 兼容普通 Windows 路径、`\\?\` 长路径前缀、斜杠差异和大小写差异。
- 归档任务不会重新加入活动项目或 `Recents`。

## 验证

- 新增“任务在 Recents、项目下 No chats”的回归测试。
- 验证项目归属、项目任务顺序、workspace root hint 和 projectless 清理结果。
- 保留 v2.13.5 账号切换/回滚及 v2.14.0 删除/恢复测试。
