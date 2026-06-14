# 📌 AI 接手须知（fitcoach-website / MIGO FIT 官网）

> **本文是「协作契约」**：任何新接手 / 断线重连 / 切换 AI 工具的助手，**动手前必须先从头到尾读完**。
> 项目"是什么"请看 [`../README.md`](../README.md) 和 [`../BRAND.md`](../BRAND.md)；本文只讲"和我协作的规矩"。

---

## 0. 四仓全景（务必先认清楚）

本工程不是孤岛，是 **4 个仓库协同开发**，本机路径都在 `~/code/lanprojects/`：

| 仓 | 路径 | 角色 |
|---|---|---|
| **fitcoach-website**（本仓） | `~/code/lanprojects/fitcoach-website` | **官网静态站**（纯 HTML/CSS，部署在腾讯云 CVM nginx 容器，未来绑域名 `migofitai.com`） |
| FitCoachRN | `~/code/lanprojects/FitCoachRN` | RN 客户端（Android 已实装） |
| FitCoachServer | `~/code/lanprojects/FitCoachServer` | Spring Boot 后端 |
| FitCoachAdminManager | `~/code/lanprojects/FitCoachAdminManager` | 管理后台 |

> 本仓与其余三仓**没有代码依赖**，但**品牌 VI（颜色 / Logo / Slogan / 公司信息 / 备案号）必须保持四端一致**。

---

## 1. ⚠️ 铁律：改完即 commit + push（最重要！）

> **这一条违反一次都不行**。我（用户）以前的 AI 协作流程是「每完成一个主题就立刻 commit + push」。
>
> **官网部署流程**：本地 `git push origin main`（github 仓库做代码托管）→ 到生产服务器 `bash shell/deploy-website.sh`（详见 [`FitCoachServer/shell/deploy-website.sh`](../../FitCoachServer/shell/deploy-website.sh)）→ 服务器 `git pull` 到 `/data/fitcoach/website` → docker nginx 容器只读挂载 + reload。**push 完不会自动上线**，需要去服务器跑一次部署脚本（或我手动跑）。

### 强制流程

1. **完成一个独立主题就立刻提交**（"独立主题"= 一处文案 / 一个页面 / 一张图）。**不要积压**。
2. 提交前**自检 3 条**：
   - 双语 / 错别字 / 公司名 / 邮箱 / 域名 拼写过一遍
   - 法律相关页面（`privacy.html` / `terms.html` / `legal/*`）改完**双开本地浏览器看下渲染**
   - 链接（特别是跨页 `nav-links`、`footer` 和外部备案链接）有没有断
3. 提交后**必须** `git push origin main`，不要只 commit 不 push。
4. 提交完用一句话告诉我：**「已 commit + push，hash: abc1234，请在服务器执行 `cd /opt/fitcoach/FitCoachServer && bash shell/deploy-website.sh` 发布」**。

### Commit message 规范（参考本仓真实历史）

格式：`<type>(<scope>): <中文描述>`

- `type`：`feat` / `fix` / `refactor` / `chore` / `docs` / `style`
- `scope`：`brand` / `privacy` / `terms` / `contact` / `index` / `legal` / `beian`（备案）/ `domain` / `assets`
- 描述：**中文**，一句话讲清楚做了什么

参考样例（取自本仓最近真实历史）：

```
feat: 新增 App WebView 专用法律文档 H5 页面
fix(beian): 备案区域 粤→京 + 恢复北京跃动无限科技有限公司
feat(beian): footer 加 ICP / 公安备案占位 + 明确备案中状态
feat(domain): 绑定自定义域名 migofitai.com
feat: 品牌全面重塑 FitCoach → MIGO FIT
```

### 不要做的事

- ❌ 不要 `git commit -am` 一把梭把不相关的改动揉一起
- ❌ 不要写"WIP / temp / test"（线上站点不允许有半成品）
- ❌ 不要忘 `git push`
- ❌ 不要静默修改 `CNAME`（会直接改变域名绑定，必须提前问我）

---

## 2. ⚠️ 铁律：动手前先读 doc

### 按场景必读清单

| 你要做的事 | 必读 |
|---|---|
| 看项目全貌（目录 / 部署 / DNS / 备案流程） | [`../README.md`](../README.md) |
| 改文案 / 颜色 / Logo / Slogan / 应用商店关键词 | [`../BRAND.md`](../BRAND.md) **— 必读，VI 规范是强制约束** |
| 改隐私 / 协议 / 法律 H5 | [`../privacy.html`](../privacy.html) / [`../terms.html`](../terms.html) / [`../legal/`](../legal) |
| 改导航 / 首屏 / 功能介绍 | [`../index.html`](../index.html) |
| 改样式（颜色 / 排版 / 间距） | [`../assets/style.css`](../assets/style.css)（**顶部 `:root` 块是单一来源**，不要硬编码色值散落各处）|
| 改备案号 / 备案文案 | [`../README.md`](../README.md) § 备案号下发后操作清单 |

---

## 3. ⚠️ 铁律：品牌 VI 跨四仓一致

**官网是品牌门面，必须严格执行 [`BRAND.md`](../BRAND.md)。** 不要凭"我觉得这个颜色好看"就改：

- 颜色：主色 `#FF4D4F` / 辅色 `#FFA940` / 渐变 `#FF4D4F → #FFA940`，全站走 CSS 变量（`assets/style.css` 顶部 `:root`），改一处就好
- Slogan 中文：「你的 AI 健身好朋友」固定不变
- Slogan 英文：「Your AI Workout MIGO」固定不变
- 应用名：**MIGO FIT**（全大写，两词中间 1 空格），中文「米高」
- 公司名：**北京跃动无限科技有限公司**（不要乱改成「跃动无限」「北京跃动」简写）
- 联系邮箱：`1348270542@qq.com`（未来切换到企业邮箱前不要擅自改）
- 公司信息源单一：[`BRAND.md`](../BRAND.md) § 7

**改其中任何一项 = 必须四仓同步**（详见 § 7）。

---

## 4. ⚠️ 铁律：法律文档 / 备案信息改动是高危操作

涉及 `privacy.html` / `terms.html` / `legal/*` / 任何带 `京 ICP 备` / `京公网安备` 字样的文案：

1. **必须先告诉我你要改什么**，不要直接动手
2. 改完**必须**自己 grep 一遍四个 footer 文件确认改全了（README § 备案号下发后操作清单 已列出 4 处）：
   - [`index.html`](../index.html)
   - [`privacy.html`](../privacy.html)
   - [`terms.html`](../terms.html)
   - [`contact.html`](../contact.html)
3. **备案号下发后**，RN 客户端 [`FitCoachRN/src/common/config/icpConfig.ts`](../../FitCoachRN/src/common/config/icpConfig.ts) 也要同步改（**跨仓**，单一来源在 RN 那边）
4. 法律页面的变更涉及合规，**改完跟我同步，不要直接 push 上线**

---

## 5. 标准工作流

```
1. 读用户需求 → 拆 todo
2. 读 BRAND.md 和 README.md 对应章节
3. 涉及多页面同步 → 列清单确认改全
4. 改代码（apply_diff 优先）
5. CSS 改动 → 走 :root 变量，不要散落硬编码
6. 改完自检：本地浏览器开 file:// 看渲染，特别是导航 / footer
7. git add → commit（中文 message） → push
8. 告诉用户「已 commit + push, hash: xxxxxxx，1 分钟后 migofitai.com 生效」
9. 进入下一个 todo
```

---

## 6. 禁止行为清单

| ❌ 不要 | ✅ 应该 |
|---|---|
| 引入 npm / 构建工具（Vite / Webpack / 任何 bundler） | 保持**纯静态 HTML**，浏览器直开即可 |
| 引入 JS 框架（React / Vue） | 一律原生 HTML + CSS，必要时少量原生 JS |
| 引入外部 CDN（除已有的 Google Fonts / 字体类）| 资源全本仓自托管，规避网络风险 |
| 加追踪脚本 / GA / 百度统计 | 涉及隐私协议变更，**先问我** |
| 自作主张改 `CNAME` 文件 | 域名绑定属高危，**先问我** |
| 直接修改 `legal/privacy-policy.html` / `legal/user-agreement.html` 的法律条款 | 法律措辞**先问我**，错一字都可能违规 |
| 加 cookie / localStorage / 任何持久化 | 静态站不需要，**先问我** |
| 把颜色硬编码到 inline style 或散落到各文件 | 一律走 `assets/style.css` 顶部 `:root` 变量 |
| 主动创建总结 md（`SUMMARY.md` / `CHANGES.md` 等）| 进度直接对话讲，需要文档时**问我** |
| 改完不本地预览就 commit | 至少 `open index.html` 看一眼再提交 |

---

## 7. 跨仓协同约定（品牌 VI 一致性）

| 改动场景 | 同步动作 |
|---|---|
| 改品牌色（主色 / 辅色 / 渐变） | website `assets/style.css` + RN `src/common/theme/colors.ts` + admin `src/theme` + BRAND.md → **四仓 commit + push** |
| 改 Slogan / 应用名 / 中英文文案 | website 所有 html + RN 启动页/关于页 + admin 登录页/About + BRAND.md → **四仓 commit + push** |
| 改 Logo | website `assets/logo*.svg` + RN `android/.../res/mipmap-*` + admin `public/logo.svg` → **四仓 commit + push** |
| 改公司信息（名称 / 邮箱 / 域名） | website 所有 footer + RN `Settings`/`About` + admin `About`/`Login` + BRAND.md → **四仓 commit + push** |
| 备案号下发 | RN `icpConfig.ts`（**单一来源**）+ website 4 处 footer + admin（如有） → **多仓 commit + push** |
| 域名变更（极少发生） | RN `httpClient baseUrl` + admin `vite.config.ts` proxy + server `application-prod.yml` + server nginx `server_name` + website 所有外链文案 → **四仓 commit + push** |

---

## 8. 部署特性（必须懂）

> 官网部署在**腾讯云 CVM**（和 FitCoachServer 同一台机器），**不是 GitHub Pages**。本仓 README 早期写过 GitHub Pages 方案，**已废弃**，请以下面为准。

### 部署架构

```
本地 (你)               github (代码托管)              腾讯云 CVM 1.14.174.249
─────                  ─────────────────              ──────────────────────────
git push   ────────▶  RicherLan/fitcoach-website ──▶ /data/fitcoach/website
                                                              │
                                                              │ docker volume 只读挂载
                                                              ▼
                                                     fitcoach-nginx-prod 容器
                                                     /usr/share/nginx/website
                                                              │
                                                              ▼
                                                     http://1.14.174.249/
                                                     (未来 → migofitai.com)
```

### 发布动作（每次都要做，**push 不会自动上线**）

```bash
# 在服务器上执行（不是本地！）
cd /opt/fitcoach/FitCoachServer
bash shell/deploy-website.sh         # 日常更新（git pull + nginx -s reload，零停机）
bash shell/deploy-website.sh status  # 看部署状态 + 当前线上 commit hash
bash shell/deploy-website.sh init    # 首次部署专用（git clone）
```

脚本源码 + 详细注释：[`FitCoachServer/shell/deploy-website.sh`](../../FitCoachServer/shell/deploy-website.sh)

### 几件必须知道的事

- **push 不等于上线**：必须去服务器跑 `bash shell/deploy-website.sh` 才生效（脚本里是 `git pull + nginx -s reload`）
- **github 仅作代码托管**：私有 / public 都行，不参与"发布"
- **回滚方式**：`git revert <bad_hash> && git push` → 在服务器再跑一次 `bash shell/deploy-website.sh`
- **nginx 容器共用**：和 FitCoachServer 共用同一个 `fitcoach-nginx-prod` 容器；改 nginx 配置请去 `FitCoachServer/nginx/`
- **没有 CNAME 文件**：早期 GitHub Pages 方案曾留过 `CNAME` 文件，**已删除**。当前 CVM nginx 方案下，域名绑定通过 nginx `server_name` + DNS A 记录实现，本仓不需要任何与域名相关的元文件
- **域名当前状态**：尚未绑定 `migofitai.com`，公网通过 `http://1.14.174.249/` 访问；备案完成后通过改 nginx `server_name` + DNS A 记录指向 CVM 来绑定
- **HTTPS**：通过 nginx 容器内的证书配置（详见 [`FitCoachServer/doc/DEPLOY.md`](../../FitCoachServer/doc/DEPLOY.md) § 5 HTTPS 证书配置）

---

## 9. 用户偏好（蓝伟华 / 林逸）

- 中文回复，简体中文，**不要用 emoji 表情**
- 直接出方案，不要反复确认"你确定吗"
- 出错了**承认错误**，不要狡辩 / 找借口
- 给命令优先给「我能直接复制粘贴跑」的完整命令
- 涉及线上文案 / 法律 / 备案 → **改前先告诉我，得到允许再动手**
- 改完跟我同步：commit hash + 提醒去服务器跑 `bash shell/deploy-website.sh`

---

## 10. 紧急情况

如果你（AI）发现：
- 本地有未提交的改动 → **立刻 commit + push**（官网积压改动 = 线上和本地不一致 = 后续协作必踩坑）
- 已 push 但发现错字 / bug / 法律措辞错误 → **立刻 `git revert <hash> && git push`** 撤回；如果已经在服务器跑过 `deploy-website.sh`，提醒我再跑一次部署脚本同步线上
- 隐私政策 / 用户协议被改动 → **立刻告诉我**，不论改动多小
- 不知道某段代码 / 文案是不是线上跑着的 → 在服务器跑 `bash shell/deploy-website.sh status` 看当前线上 commit hash 比对

---

**Last updated**: 2026-06 by 蓝伟华 — 这份文档是血泪教训，不允许打折执行。
