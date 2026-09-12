# shadowrocket-rules-joe

Shadowrocket 使用方法可以查看： https://houjoe.me/posts/shadowrocket-guide/

这个仓库放置我的 Shadowrocket 规则，方便在 GitHub 里管理和更新

## uucloud 个人配置

本仓库的个人配置为 [`uucloud-shadowrocket-rules.conf`](./uucloud-shadowrocket-rules.conf)。固定更新地址：

```text
https://raw.githubusercontent.com/uucloud/shadowrocket-rules-joe/main/uucloud-shadowrocket-rules.conf
```

- AI 服务统一分组，默认美国节点；普通 Google 服务保留独立分组。
- Netflix、Disney+、HBO 合并为「海外流媒体」，默认新加坡节点。
- Slack 保留「AgentNEO 节点组」；首页的节点订阅需命名为 `AGENTNEO`，且节点名称含 `x1.0`。未使用此订阅时，在 Slack 分组手动选择其他策略。
- 游戏下载的具体域名优先走直连，其他游戏流量保持原来的游戏平台策略。
- 外部规则集从 37 条引用精简为 30 条；删除重复规则和旧 YouTube 域名黑名单，清理支付、评论等业务域名的旧拦截项。
- 移除 URL 重写及 MITM；保留的域名广告拦截优先于服务分流。
- 保留国内直连和最后的 `FINAL,PROXY`。

修改此文件并推送到本仓库的 `main` 后，手机才能下载到新版本。配置自动更新只下载同名文件，不会自动合并上游 `shadowrocket-rules.conf` 的变更。以下 Pages 地址属于上游配置；个人版使用上面的 GitHub Raw 地址，不依赖 Pages 部署。

## 📦 配置版本选择

除个人配置外，仓库还保留以下两个上游版本供参考；其策略说明见下文：

### 🔥 **完整版（推荐新手）**
- **链接**：`https://shadowrocket-rules-joe.pages.dev/shadowrocket-rules.conf`
- **特点**：包含 26 个外部规则集，覆盖面广，开箱即用
- **适合**：不想折腾，希望有完整分流体验的用户
- **优势**：规则覆盖全面，各种 App 都有专门优化

### ⚡ **极简版（推荐进阶用户）**
- **链接**：`https://raw.githubusercontent.com/houjoe0829/shadowrocket-rules-joe/refs/heads/main/shadowrocket-rules-simplified.conf`
- **特点**：只保留 3 个核心规则集，主要依靠自定义规则
- **适合**：追求简洁高效，不需要过多外部依赖的用户
- **优势**：
  - 🚀 加载速度更快（减少 88% 的外部规则集）
  - 🔧 更稳定（减少外部依赖）
  - 📝 易于维护和自定义
  - 💡 保留所有核心分流功能

## 使用方法

1.  **获取配置链接**

    *   **完整版**：`https://shadowrocket-rules-joe.pages.dev/shadowrocket-rules.conf`
    *   **极简版**：`https://raw.githubusercontent.com/houjoe0829/shadowrocket-rules-joe/refs/heads/main/shadowrocket-rules-simplified.conf`
    *   **uucloud 个人版**：`https://raw.githubusercontent.com/uucloud/shadowrocket-rules-joe/main/uucloud-shadowrocket-rules.conf`
    *   选择其中一个版本复制原始文件链接，不要使用 GitHub 的 `blob` 页面链接。

2.  **在 Shadowrocket 中添加配置**

    *   打开 Shadowrocket 应用。
    *   在配置界面，点击右上角的 " **+** "  加号按钮。
    *   在弹出的窗口中，粘贴你刚刚复制的配置链接。
    *   下载后点击该配置，选择「使用配置」，确认已勾选。
    *   首页的全局路由选择「配置」。

3.  **开启自动更新 (可选)**

    *   Shadowrocket → 设置 → 更新区域的「配置」→ 开启「自动后台更新」，间隔可设为每天。
    *   iOS 设置 → 通用 → 后台 App 刷新，允许 Shadowrocket；实际执行时间受 iOS 后台调度影响。
    *   急需更新时，点击配置文件 →「更新配置」。首页机场节点的「订阅更新」是另一项功能。
    *   远程更新会覆盖手机上的配置修改，请把个人修改维护在本仓库的个人配置中。
    *   功能说明参考 [Shadowrocket 使用手册：自动更新](https://github.com/LOWERTOP/Shadowrocket/wiki#自动更新)。

## 📊 版本对比

| 特性 | 完整版 | 极简版 |
|------|--------|--------|
| 外部规则集数量 | 26 个 | 3 个 |
| 配置文件大小 | 较大 | 较小 |
| 加载速度 | 普通 | 更快 |
| 稳定性 | 依赖外部规则集 | 更稳定 |
| 维护难度 | 简单（自动更新） | 简单（自定义规则） |
| 覆盖范围 | 全面 | 核心功能完整 |
| 适用人群 | 新手用户 | 进阶用户 |
| 推荐场景 | 开箱即用 | 追求性能 |

## 🔄 版本切换

如果您想从一个版本切换到另一个版本：

1. 添加新版本的配置链接
2. 下载并选择「使用配置」
3. 确认连接正常后，再按需删除旧配置

## 🗂️ 上游完整版策略组说明

| 策略组 | 默认节点 | 说明 |
|--------|----------|------|
| AI 服务 | 美国节点 | OpenAI、Claude、Gemini 等 AI 工具 |
| Typeless | 新加坡节点 | Typeless 写作工具，独立分组 |
| 海外流媒体 | 自选 | Netflix、Disney+、HBO 等 |
| YouTube | 香港节点 | YouTube 及视频 CDN |
| TikTok | 自选 | TikTok 海外版 |
| Spotify | 直连 | Spotify 音乐 |
| Telegram | 自选 | Telegram 即时通讯 |
| 海外社交媒体 | 美国节点 | Twitter/X、Reddit、Facebook、Instagram 等 |
| 游戏平台 | 香港节点 | Steam、Epic、PlayStation、Xbox 等商店 |
| 游戏下载 | 直连 | 游戏内容下载走直连，速度更快 |

## 🛡️ 节点过滤

地区分组（香港 / 台湾 / 日本 / 新加坡 / 韩国 / 美国）均已配置以下过滤规则：

- **自动排除假节点**：过滤机场塞在订阅里的信息条目。排除词采用词根形式（套餐、流量、订阅、网址、到期、过期、重置、expire、官网、官方），可覆盖「套餐到期日期」「订阅获取时间」「当前网址」「剩余流量」等各种写法。注意该过滤只作用于地区分组，这些条目在服务器总列表中仍会显示
- **繁简体双覆盖**：支持繁体与简体节点名称（如臺灣 / 台湾、東京 / 东京、獅城 / 狮城等），避免漏匹配
- **地区互斥**：每个地区分组都排除其他地区的名称与代码，避免中转节点被误选。例如名为「美国 03 | 新加坡中转」的节点不会被算作美国节点
- **不使用裸小写代码**：英文关键词统一用 `(?i)` 做大小写不敏感匹配，不再直接匹配 `us`、`jp`、`kr`、`sg` 等小写子串，避免 `Australia`、`Russia` 等节点名被误判

## ⚠️ 使用注意

### Claude Code 等终端工具无法走代理？

如果发现 Claude Code 授权时提示「不在支持的区域」，或者终端里的命令行工具没有走代理，原因是 Shadowrocket 默认只是一个 HTTP 代理，只有主动配置了代理地址的应用（如浏览器）才会走它。

**解决方法：开启隧道的「强制路由」**

在 Shadowrocket → 隧道 页面，开启：

- ✅ **强制路由**：让终端等 CLI 工具的流量也进入隧道，由规则决定走代理还是直连

注意：无需开启「包括所有网络」，国内网站仍会按规则走直连，不影响国内访问速度。

---

**简单来说，只需要复制链接，粘贴到 Shadowrocket 里面就可以使用了！记得开启自动更新，省心又方便！**
