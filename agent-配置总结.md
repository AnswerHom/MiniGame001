# OpenClaw Agent 配置总结

## 当前配置

### Agent 1 (main)
- **Agent ID**: main
- **Agent 目录**: `/root/.openclaw/agents/main`
- **Workspace**: `/root/.openclaw/workspace`
- **飞书应用**: cli_a9282e3648381bcd
- **允许用户**: ou_bd188acc58f00b0b9d0677ad37aa0c85
- **状态**: ✅ 活跃
- **Bot OpenID**: ou_3660181f8c33d95772fd696a73d8be22

### Agent 2 (assistant)
- **Agent ID**: assistant
- **Agent 目录**: `/root/.openclaw/agents/assistant`
- **Workspace**: `/root/.openclaw/workspace-assistant`
- **飞书应用**: cli_a929b17a71781bc0
- **允许用户**: ou_bd188acc58f00b0b9d0677ad37aa0c85
- **状态**: ✅ 活跃
- **Bot OpenID**: ou_f228de575a8b61018f29f6f814b125de

## 配置文件位置

- **主配置**: `/root/.openclaw/openclaw.json`
- **Agent 1 会话**: `/root/.openclaw/agents/main/sessions/sessions.json`
- **Agent 2 会话**: `/root/.openclaw/agents/assistant/sessions/` (需要创建)

## 工作原理

### 消息路由
1. 用户发送消息时，系统根据 `allowFrom` 配置决定使用哪个 agent
2. 每个用户只绑定到一个 agent（避免冲突）
3. Agent 之间完全独立，共享不同的 workspace 和配置

### 配置示例
```json
{
  "channels": {
    "feishu": {
      "accounts": {
        "agent1": {
          "name": "Agent1",
          "appId": "cli_a9282e3648381bcd",
          "enabled": true,
          "allowFrom": ["ou_bd188acc58f00b0b9d0677ad37aa0c85"]
        },
        "agent2": {
          "name": "Agent2",
          "appId": "cli_a929b17a71781bc0",
          "enabled": true,
          "allowFrom": ["ou_bd188acc58f00b0b9d0677ad37aa0c85"]
        }
      }
    }
  }
}
```

## 使用方法

### 通过 Agent 1 回复
- 用户: ou_bd188acc58f00b0b9d0677ad37aa0c85
- Agent: agent1 (main)
- Workspace: /root/.openclaw/workspace

### 通过 Agent 2 回复
- 用户: ou_bd188acc58f00b0b9d0677ad37aa0c85
- Agent: agent2 (assistant)
- Workspace: /root/.openclaw/workspace-assistant

## 状态检查

### 服务状态
```bash
systemctl --user status openclaw-gateway.service
```

### 日志查看
```bash
journalctl --user -u openclaw-gateway.service -f
```

### Agent 会话检查
```bash
# Agent 1
cat /root/.openclaw/agents/main/sessions/sessions.json

# Agent 2
cat /root/.openclaw/agents/assistant/sessions/sessions.json
```

## 创建时间
- 2026年3月2日

## 最后更新
- 2026年3月2日 13:44 - 两个 agent 都已配置并正常运行
