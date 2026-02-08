# 现状盘点快照（脱敏）

更新时间：2026-02-08

## 运行状态
- 网关服务：LaunchAgent（loaded）
- 绑定地址：`127.0.0.1`
- 端口：`18789`
- Dashboard：`http://127.0.0.1:18789/`
- RPC 探测：正常

## 健康检查摘要
- Telegram：ok（bot 名称已验证）
- Feishu：未配置
- Agent：main（默认）
- 会话存储：本地 JSON

## 发现的问题（M1）
- CLI 运行时缺少 `OPENCLAW_TELEGRAM_BOT_TOKEN`，导致配置校验失败
  - 说明：服务环境变量可能已设置，但当前终端未注入该变量
  - 影响：`openclaw-cn gateway status` 与 `openclaw-cn health` 报告 config invalid

## 结论
本机网关处于可运行状态，Control UI 可访问。需要补齐 CLI 运行环境的 Telegram Token 变量，以避免 CLI 校验失败。
