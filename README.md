# 猿媒BOT Agent Skills

给支持 AgentSkills 的客户端使用：

- 龙虾 OpenClaw
- 爱马仕 Hermes
- WorkBuddy

## 目录

- `skills/yuanmei-mcp/SKILL.md`：教 Agent 使用猿媒BOT MCP 工具
- `workbuddy/mcp.json`：WorkBuddy 现成 MCP 配置
- `hermes/entry.json`：Hermes MCP Catalog 提交元数据

## 先配置 MCP

Skill 不包含 MCP 服务器配置。先在客户端配置：

```text
URL: https://chatbot.apetd.com/mcp
Header: Authorization: Bearer <YUANMEI_MCP_TOKEN>
```

令牌在猿媒BOT「个人中心 → API 接入 → MCP 接入」签发。

## 文档

https://github.com/CN-Jayden/yuanmei-bot-docs

## 安全

- 不要把令牌写进仓库或群聊
- 发送类工具调用前确认目标群和内容
- Skill 是第三方代码，启用前请阅读 `SKILL.md`
