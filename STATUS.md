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
- CLI 运行时缺少 `OPENCLAW_TELEGRAM_BOT_TOKEN` 与 `OPENCLAW_GATEWAY_TOKEN`
  - 说明：服务环境变量已设置，但当前终端未注入
  - 影响：`openclaw-cn gateway status` 与 `openclaw-cn health` 报告 config invalid

## 审计与诊断结论（已执行）
- doctor：完成（无 channel security 警告）
- security audit --deep：`0 critical / 2 warn / 1 info`
  - warn：`gateway.trusted_proxies_missing`（仅在反向代理访问时需要配置）
  - warn：`models.weak_tier`（主模型低于推荐等级）
  - info：attack surface 摘要（groups open=0 / allowlist=1）

## 模型可用性
- 默认模型已切换为 `openai/gpt-5.2`
- 允许模型列表已包含 `openai/gpt-5.2`
- 其余已配置模型不可用（需要完成对应提供方认证）

## 结论
本机网关处于可运行状态，Control UI 可访问。CLI 运行环境仍需注入 token（或在服务环境执行），以避免校验失败。
