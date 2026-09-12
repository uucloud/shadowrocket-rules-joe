# 个人配置合并上游记录

合并日期：2026-09-12。来源：仓库内 `shadowrocket-rules.conf`，文件更新时间为 2026-07-31 20:53:55。

## 本轮补充

| 内容 | 个人版处理 |
| --- | --- |
| Typeless | 独立分组，默认新加坡；域名从 AI 服务改归此组 |
| 韩国节点 | 增加地区组和各服务的可选出口；使用个人版的国家代码边界、繁简体及订阅信息过滤 |
| 美国节点 | 测速间隔从 600 秒改为 3600 秒；补充排除「海外用户专用」及繁体写法 |
| 小宇宙 | `xiaoyuzhoufm.com`、`xyzcdn.net` 直连 |
| 多邻国 | `duolingo.com` 直连；`duolingo.cn` 已由现有国内规则覆盖 |
| 其他直连 | 合并 `rmbgame.net`，放在通用规则集前 |
| 工作协作 | `chime.aws`、`resilio.com`、`matters.town` 使用 PROXY |
| LinkedIn | `linkedin.com`、`licdn.com` 使用原有 Social Website 分组，默认美国 |
| Activision | `activision.com` 使用游戏平台；其他上游游戏平台域名已由现有集合覆盖 |

## 已合并或已覆盖

- AI 专用域名、Notion、开发工具、游戏下载分流已在上一轮整理。OpenAI 使用单一远程集合，Claude 等补充域名去除了父域已覆盖的重复子域。
- Netflix、Disney+、HBO 已合为海外流媒体，保持个人版默认新加坡。
- 国内 `.cn` 直连、`paypal.cn` 例外、`always-real-ip` 的逗号修复已存在。
- Twitter/X 相关域名由 Twitter 集合覆盖；不再次添加同策略的显式规则。
- 上游 26 条规则集引用中，豆瓣、小红书由 China 覆盖；其余集合已在个人版引用。个人版保留 OpenAI、Sony、SteamCN、Steam、Game、Global，合计 30 条。
- `yystv.cn` 已由 `.cn` 规则直连。

覆盖比较使用本次审查下载的外部规则集内容；上游集合以后可能改变，不能视为永久包含关系。

## 保留的个人版差异

- Google、Microsoft 的通用服务不整体迁入 AI 分组；不添加 `.ai` 全域 AI 规则。
- `byteoversea.com` 保留已有 TikTok 分流，不将共享域名整体改为直连。
- 不导入整个 `akamaihd.net` 的直连，仅保留具体游戏下载 CDN 域名。
- 不导入上游广告聚合端点 `mediation.unity3d.com` 的强制直连；维持原来的默认分流。
- `alioss.yystv.cn = server:114.114.114.114` 是上游针对特定 DNS/CDN 故障的临时修复，本次未复现该故障，不覆盖个人版 DNS。
- Slack 保留 AgentNEO 专用分组，不导入宽泛的 `DOMAIN-KEYWORD,slack`。
- 保留各现有服务默认出口；仅 Typeless 按新增独立组改为新加坡。Facebook 不与其他社交服务强制合并。
- 不恢复 USER-AGENT 分流、URL 重写、MITM 或上游更新地址。个人版仍从本仓库 Raw 地址更新。
- `FINAL,PROXY` 保持在 `[Rule]` 的最后。
