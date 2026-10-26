---
name: yuanmei-mcp
description: 使用猿媒BOT MCP 读取企业微信群消息、搜索记录，并把回复或通知发回群。
metadata: {"openclaw":{"category":"communication","homepage":"https://github.com/CN-Jayden/yuanmei-bot-docs"},"hermes":{"category":"communication"}}
---

# 猿媒BOT MCP

当用户要求查看企业微信群、读取消息、搜索聊天记录，或向企微群发送消息时，使用已配置的 `yuanmei` MCP 工具。

## 前置条件

- 已配置 MCP 服务器 `yuanmei`
- 地址：`https://chatbot.apetd.com/mcp`
- 请求头：`Authorization: Bearer <YUANMEI_MCP_TOKEN>`
- 令牌在猿媒BOT「个人中心 → API 接入 → MCP 接入」签发

如果没有看到 `mcp__yuanmei__*` 工具，先让用户检查 MCP 配置和令牌；不要假装能调用。

## 工具

| 工具 | 用途 |
| --- | --- |
| mcp__yuanmei__whoami | 验证令牌，获取工作空间和机器人 |
| mcp__yuanmei__list_robots | 列出机器人 |
| mcp__yuanmei__list_conversations | 列出群聊和联系人 |
| mcp__yuanmei__read_messages | 读取消息，支持 after 增量 |
| mcp__yuanmei__search_messages | 搜索消息 |
| mcp__yuanmei__send_text | 发送文本 |
| mcp__yuanmei__send_image | 发送图片 URL |
| mcp__yuanmei__send_link | 发送链接卡片 |
| mcp__yuanmei__schedule_message | 定时发送 |

## 使用规则

1. 第一次接入先调用 `whoami`。
2. 不知道群 ID 时，先调用 `list_conversations`。
3. 读取消息优先用 `read_messages`，不要全量拉取。
4. 定时轮询使用 `after` 和 `next_after`。
5. 发送前向用户确认群、内容和时间。
6. 发送类工具风险为 medium；不要未经确认向客户群群发。
7. 令牌、群 ID、消息内容都属于敏感数据，不要输出完整令牌。
8. 测试空间只允许操作测试群；不要尝试其他群。

## 示例

用户：看看测试群最近消息

1. 调 `list_conversations` 找测试群
2. 调 `read_messages`，`conversation_id` 用返回的群 ID
3. 摘要给用户，不暴露无关数据

用户：在测试群发一条通知

1. 确认群 ID 和内容
2. 调 `send_text`
3. 返回 `messageId` 和 `pending`，说明已入队，不代表已送达
