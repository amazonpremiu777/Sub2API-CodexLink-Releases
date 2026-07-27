# Sub2API CodexLink v2.13.4

## 修复

- 修复部分电脑从官方账号模式切换到 Sub2API 时提示“Rollout 首行不是有效的 session_meta”并回滚的问题。
- 兼容 Codex 在 Windows 路径元数据中生成的非标准 JSON 反斜杠转义，例如路径段 `\0-work`。
- 同步 provider 时会把这类首行规范化为有效 JSON，同时保持原路径和其他会话元数据不变。
- 对话扫描与 provider 改写共用同一套兼容解析逻辑，避免写入前后判断不一致。

## 安全

- 兼容处理仅修复 JSON 字符串中无效的反斜杠转义，完整首行仍必须能够解析为 `session_meta`。
- 空文件、截断 JSON、缺少 `payload` 或缺少 `session_meta` 的 rollout 仍会终止切换并自动回滚。
- 模式切换前的数据库、索引、全局状态和改写过的 rollout 仍保留事务快照。

## 验证

- 新增非法 Windows 路径转义的扫描、官方/Sub2API 往返同步和规范化回归测试。
- 新增真实截断 rollout 必须失败并回滚的测试。

