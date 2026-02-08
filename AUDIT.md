# 审计与留存策略

## 执行周期
- 安全审计：每月
- 深度诊断（doctor）：每季度

## 记录内容（脱敏）
- 执行时间、执行人
- 主要发现与风险等级
- 已采取动作与回滚方案

## 模板
日期：
执行人：
命令：
摘要：
风险：
处置：
验证结果：

## 最近执行记录（脱敏）
日期：2026-02-08
执行人：管理员
命令：
- openclaw-cn doctor --non-interactive
- openclaw-cn security audit --deep
摘要：
- doctor 正常完成，无 channel security 警告
- audit summary: 0 critical / 2 warn / 1 info
风险：
- gateway.trusted_proxies_missing
- models.weak_tier
处置：
- 保持 Control UI 仅本机访问，暂不配置 trustedProxies
- 暂留现有模型，后续根据可用性升级
验证结果：
- 日志与摘要已记录
