# OpenClaw Admin 部署基线（本机）

更新时间：2026-02-08

## 基线要求（官方对齐）
- Node 22+
- 网关服务可用（本机）
- Control UI 可访问且启用认证
- 避免公网直接暴露 Control UI

参考：
- https://docs.openclaw.ai/start/getting-started
- https://docs.clawdbot.com/web/dashboard

## 本机部署约束
- 绑定地址：`127.0.0.1`（loopback）
- 端口：`18789`
- 认证方式：token
- 网关生命周期：launchd（LaunchAgent）

## 关键路径
- 配置文件：`~/.openclaw/openclaw.json`
- 日志：`~/.openclaw/logs/gateway.log`（若实际路径变更，以运行日志为准）
- LaunchAgent：`~/Library/LaunchAgents/com.clawdbot.gateway.plist`

## 常用命令（运维）
- 网关状态：`openclaw-cn gateway status`
- 网关重启：`openclaw-cn gateway restart`
- 健康检查：`openclaw-cn health`
- Control UI：`http://127.0.0.1:18789/`

## 安全基线
- token 认证必须启用（不允许 `auth: "none"`）
- 控制台只允许本机访问（loopback）
- 远程访问使用 Tailscale/SSH 隧道
- 密钥不在文档中明文保存

## 验证清单
- Control UI 本地可访问且需要认证
- 网关服务处于运行中
- loopback 绑定确认（`127.0.0.1`）
