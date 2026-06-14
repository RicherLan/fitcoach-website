# MIGO FIT Official Website

> ⚠️ **新接手的 AI 请先读 [`doc/AI-PROMPT.md`](./doc/AI-PROMPT.md)**（协作铁律：改完即 commit + push、品牌 VI 跨四仓一致、法律/备案高危操作必先问等），再回头读本文了解项目本身。

MIGO FIT 官方网站源码（纯静态 HTML/CSS），**部署在腾讯云 CVM**（和 [`FitCoachServer`](../FitCoachServer) 同一台机器），未来绑定域名 **migofitai.com**。

- **运营主体**：北京跃动无限科技有限公司
- **产品**：MIGO FIT — AI 健身好朋友
- **当前公网入口**：http://1.14.174.249/
- **未来官方域名**：https://migofitai.com（备案完成后启用）
- **API 域名**：api.migofitai.com（生产环境后端入口，由 FitCoachServer 提供）
- **联系邮箱**：1348270542@qq.com

## 目录结构

```
fitcoach-website/
├── index.html              首页（产品介绍 + 功能特性 + 关于我们）
├── privacy.html            隐私政策（覆盖摄像头/账号/支付/第三方 SDK）
├── terms.html              用户服务协议（含会员/退款/免责）
├── contact.html            联系我们（用户支持/商务/媒体/隐私）
├── legal/                  App WebView 专用法律文档 H5 页面（嵌入到 RN 客户端打开）
│   ├── privacy-policy.html
│   └── user-agreement.html
├── assets/
│   ├── style.css           全站样式（顶部 :root 块是单一颜色 / 字号来源）
│   ├── logo.svg            主 Logo（圆角矩形 + 字母 M，可作 App Icon）
│   ├── logo-wordmark.svg   完整水平 Logo（Logo + "MIGO FIT" 文字）
│   └── favicon.svg         浏览器标签页图标
├── BRAND.md                品牌 VI 规范（色彩 / Logo / 字体 / 文案 — 跨四仓唯一来源）
├── doc/
│   └── AI-PROMPT.md        AI 协作契约（铁律 / 工作流 / 禁止行为 / 跨仓协同）
└── README.md
```

---

## 部署架构

```
本地 (开发者)           github (代码托管)              腾讯云 CVM 1.14.174.249
─────                  ─────────────────              ──────────────────────────
git push     ──────▶  RicherLan/fitcoach-website ──▶ /data/fitcoach/website
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

- **代码托管**：github.com/RicherLan/fitcoach-website（只做版本管理，**不参与发布**）
- **运行机器**：和 FitCoachServer 共用同一台腾讯云 CVM
- **运行容器**：和 server 共用 `fitcoach-nginx-prod` 容器，通过 docker volume 只读挂载 `/data/fitcoach/website`
- **发布脚本**：[`FitCoachServer/shell/deploy-website.sh`](../FitCoachServer/shell/deploy-website.sh)（脚本在 server 仓，不在本仓）

---

## 发布流程

### 日常更新（最常用）

```bash
# 1. 本地改完，commit + push
git add .
git commit -m "feat(xxx): 中文描述"
git push origin main

# 2. 登服务器，跑发布脚本（git pull + nginx -s reload，零停机）
ssh root@1.14.174.249
cd /opt/fitcoach/FitCoachServer
bash shell/deploy-website.sh
```

### 看部署状态 / 比对线上 commit

```bash
# 在服务器上
cd /opt/fitcoach/FitCoachServer
bash shell/deploy-website.sh status
# 会输出当前线上目录、最新 commit hash / message、nginx 容器是否在跑、本地 curl 验证结果
```

### 首次部署（一次性）

```bash
# 服务器上确认 FitCoachServer 已部署并跑起 nginx 容器
cd /opt/fitcoach/FitCoachServer
bash shell/deploy.sh        # 先把 server + nginx + mysql 起来

# 再把 website 克隆下来并 reload
bash shell/deploy-website.sh init
```

### 回滚

```bash
# 本地：revert 出错的 commit
git revert <bad_hash>
git push origin main

# 服务器：拉新代码 + reload
cd /opt/fitcoach/FitCoachServer
bash shell/deploy-website.sh
```

---

## 后续维护

- **改内容**：直接编辑对应 html，commit + push + 服务器跑 `bash shell/deploy-website.sh` 后约 5 秒生效
- **加页面**：在根目录新增 html 文件，记得在导航栏（每个文件的 `nav-links` 部分）和 footer 加入口
- **改样式**：编辑 [`assets/style.css`](./assets/style.css)，**所有颜色 / 字号通过顶部 `:root` 块集中管理**，不要硬编码散落

---

## 微信审核 / App 上架审核常见检查点

本站已经覆盖以下微信开放平台 / Apple App Store / Google Play 通用审核要求：

- ✅ 产品名称、产品介绍、功能描述（[index.html](index.html)）
- ✅ 隐私政策（[privacy.html](privacy.html)，含设备权限调用清单、第三方 SDK 清单、用户权利、未成年人保护）
- ✅ 用户服务协议（[terms.html](terms.html)，含会员/订阅/退款/免责）
- ✅ App WebView 专用法律文档 H5（[legal/privacy-policy.html](legal/privacy-policy.html) / [legal/user-agreement.html](legal/user-agreement.html)）
- ✅ 产品名称 + 联系邮箱（所有页面 footer + [contact.html](contact.html)）
- ⚠️ ICP 备案号 + 公安备案号（已购腾讯云服务器，备案进行中，详见下节）

---

## 备案号下发后操作清单

ICP / 公安备案审批通过后，需要：

### 1. 替换本仓 4 个页面 footer 的备案占位

每个 footer 都已加 HTML 注释指明替换方式：

1. [`index.html`](./index.html) —— `footer-bottom` 块
2. [`privacy.html`](./privacy.html) —— `footer-bottom` 块
3. [`terms.html`](./terms.html) —— `footer-bottom` 块
4. [`contact.html`](./contact.html) —— `footer-bottom` 块

替换示例：

- 把 `<span class="icp-placeholder">京 ICP 备 XXXXXXXX 号（备案中）</span>`
  换成 `<a href="https://beian.miit.gov.cn" target="_blank" rel="noopener">京ICP备2026XXXXXX号</a>`
- 把 `<span class="icp-placeholder">京公网安备 XXXXXXXXXXXX 号（备案中）</span>`
  换成 `<a href="https://beian.mps.gov.cn/#/query/webSearch?code=11XXXXXXXX" target="_blank" rel="noopener">京公网安备 11XXXXXXXX 号</a>`

### 2. 同步 RN 客户端备案号配置（单一来源）

配套的 RN 客户端备案号配置在 [`../FitCoachRN/src/common/config/icpConfig.ts`](../FitCoachRN/src/common/config/icpConfig.ts) 单一来源，备案通过后改一处即可全局生效。

### 3. 绑定 migofitai.com 域名

- DNS：把 `migofitai.com` 和 `www.migofitai.com` 的 A 记录指向腾讯云 CVM `1.14.174.249`
- nginx：在 [`../FitCoachServer/nginx/`](../FitCoachServer/nginx) 加 `server_name migofitai.com www.migofitai.com;`
- HTTPS：参考 [`../FitCoachServer/doc/DEPLOY.md`](../FitCoachServer/doc/DEPLOY.md) § 5 申请 / 装证书
- 重启 nginx：`docker compose -f shell/docker-compose.prod.yml exec nginx nginx -s reload`

---

## License

© 2025-2026 北京跃动无限科技有限公司 版权所有。
