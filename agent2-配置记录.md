# OpenClaw Agent2 配置记录

## 配置信息

### 飞书应用配置
- **应用名称**: Agent2
- **AppID**: cli_a929b17a71781bc0
- **APPSecret**: syhb5Mqmgeayfk9Ey2zspeEebsvPJjL7
- **账户ID**: agent2

### 模型配置
- **模型**: zai/glm-4.7-flash (默认配置)

### 配置文件位置
- **文件**: `/root/.openclaw/openclaw.json`
- **配置段**: `channels.feishu.accounts.agent2`

## 配置说明

Agent2 是一个额外的飞书机器人实例，使用独立的飞书应用凭证。它将与主飞书应用（cli_a9282e3648381bcd）同时运行。

### 如何使用 Agent2

Agent2 会自动绑定到所有飞书私信中（基于动态agent配置），并使用与主agent相同的配置（glm-4.7-flash模型）。

### 注意事项

- 两个飞书应用可以同时运行
- 每个飞书用户会收到一个独立的agent实例
- 所有agent共享同一套配置，使用相同的模型
- Agent2 的配置在 openclaw.json 的 accounts 部分管理

## 创建时间
- **日期**: 2026年3月2日
- **状态**: 配置已完成，需要重启OpenClaw使配置生效
