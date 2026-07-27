# Sub2API CodexLink v2.13.5

## 修复

- 修复 v2.13.4 在 rollout 首行带 UTF-8 BOM 时仍提示“不是有效的 session_meta”的问题。
- 原始字节改写与对话扫描现在统一处理 UTF-8 BOM、零宽前缀和非标准 Windows 路径转义。
- 同步 provider 后会输出无 BOM 的标准 JSON，同时保持路径及其他会话字段值不变。

## 安全

- 仅允许移除首行开头的已知 Unicode 前缀，并修复 JSON 字符串中的非法反斜杠转义。
- 规范化后仍必须完整解析为 `session_meta`；空文件、截断 JSON、缺少 `payload` 的文件继续触发事务回滚。

## 验证

- 新增“UTF-8 BOM + 非法路径转义”组合回归测试。
- 保留官方/Sub2API 往返同步、字段值保持、真实损坏失败关闭和完整回滚测试。

