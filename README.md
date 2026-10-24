# Clash AI Rules

Clash 分流规则集合，覆盖主流 AI 服务与 AI 编程工具，帮助你精准代理 AI 相关流量。

## 支持的服务

| 规则文件 | 服务 | 规则数 | 说明 |
|---|---|---|---|
| `Anthropic.yaml` | Claude / Anthropic | 21 | Claude AI 核心域名、CDN、Auth0 认证、Sentry 监控等 |
| `AppleIntelligence.yaml` | Apple Intelligence | 2 | Apple Private Relay 中继服务 |
| `AugmentCode.yaml` | AugmentCode | 1 | AugmentCode AI 编程助手 |
| `Cursor.yaml` | Cursor | 5 | Cursor AI 编辑器、CDN、API 及 WorkOS 认证 |
| `Gemini.yaml` | Google Gemini | 15 | Gemini / Bard / DeepMind / AI Studio / Colab |
| `Meta.yaml` | Meta AI | ~392 | Meta 全家族（Facebook / Instagram / WhatsApp / Messenger / Oculus 等） |
| `OpenAI.yaml` | OpenAI / ChatGPT | 47 | ChatGPT、Sora、Codex 及相关 CDN / 实时通信 / 客户端进程 / 自有 IP 段 |
| `Trae.yaml` | Trae AI（字节跳动） | 11 | Trae AI 编辑器及后端基础设施 |
| `Windsurf.yaml` | Windsurf / Codeium | 2 | Windsurf AI 编辑器 |
| `xAI.yaml` | xAI / Grok / X | 32 | Grok AI 与 X (Twitter) 平台全量域名及 IP |

## 使用方式

在 Clash 配置文件中添加你需要的规则集。以下示例选择了 Cursor、Anthropic 和 Gemini：

```yaml
rule-providers:
  cursor:
    type: http
    path: ./Cursor.yaml
    url: "https://raw.githubusercontent.com/jinxinkai/clash-ai-rules/refs/heads/master/Cursor.yaml"
    interval: 86400
    proxy: Proxies
    behavior: classical
    format: yaml
    size-limit: 0
  anthropic:
    type: http
    path: ./Anthropic.yaml
    url: "https://raw.githubusercontent.com/jinxinkai/clash-ai-rules/refs/heads/master/Anthropic.yaml"
    interval: 86400
    proxy: Proxies
    behavior: classical
    format: yaml
    size-limit: 0
  gemini:
    type: http
    path: ./Gemini.yaml
    url: "https://raw.githubusercontent.com/jinxinkai/clash-ai-rules/refs/heads/master/Gemini.yaml"
    interval: 86400
    proxy: Proxies
    behavior: classical
    format: yaml
    size-limit: 0

rules:
  - RULE-SET,cursor,US
  - RULE-SET,anthropic,US
  - RULE-SET,gemini,US
```

### URL 格式

所有规则文件的远程地址格式统一为：

```
https://raw.githubusercontent.com/jinxinkai/clash-ai-rules/refs/heads/master/{文件名}.yaml
```

将 `{文件名}` 替换为上表中对应的文件名即可。

## 注意事项

- `interval: 86400` 表示每 24 小时自动更新一次规则
- 请将示例中的 `US` 替换为你实际使用的代理策略组名称
- 请将示例中的 `Proxies` 替换为你实际使用的代理策略组名称
- 规则定期更新，建议保持自动更新以获取最新域名覆盖

## 致谢

- [@SkywalkerJi/Clash-Rules](https://github.com/SkywalkerJi/Clash-Rules/tree/master)
- [ip.net.coffee](https://ip.net.coffee/claude/site.html)
## License

MIT