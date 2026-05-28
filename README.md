# MIGO FIT Official Website

MIGO FIT 官方网站，部署在 GitHub Pages，绑定自定义域名 **migofitai.com**。

- **公司主体**：北京跃动无限科技有限公司
- **产品**：MIGO FIT — AI 健身好朋友
- **官方网站**：https://migofitai.com
- **API 域名**：api.migofitai.com（生产环境后端入口）
- **联系邮箱**：1348270542@qq.com

## 目录结构

```
fitcoach-website/
├── index.html              首页（产品介绍 + 功能特性 + 关于我们）
├── privacy.html            隐私政策（覆盖摄像头/账号/支付/第三方 SDK）
├── terms.html              用户服务协议（含会员/退款/免责）
├── contact.html            联系我们（用户支持/商务/媒体/隐私）
├── CNAME                   GitHub Pages 自定义域名绑定（migofitai.com）
├── assets/
│   ├── style.css           全站样式
│   ├── logo.svg            主 Logo（圆角矩形 + 字母 M，可作 App Icon）
│   ├── logo-wordmark.svg   完整水平 Logo（Logo + "MIGO FIT" 文字）
│   └── favicon.svg         浏览器标签页图标
├── BRAND.md                品牌 VI 规范（色彩 / Logo / 字体 / 文案）
└── README.md
```

## 部署到 GitHub Pages（一次性，约 3 分钟）

### 步骤 1：在 GitHub 创建仓库

打开 https://github.com/new ，填写：

- **Repository name**：`fitcoach-website`
- **Visibility**：**Public**（GitHub Pages 免费版只支持 public 仓库）
- 其他保持默认，点 **Create repository**

### 步骤 2：把本地代码推上去

在本目录执行：

```bash
cd /Users/richerlan/code/lanprojects/fitcoach-website
git init
git add .
git commit -m "init: MIGO FIT 官网首发 v1"
git branch -M main
git remote add origin git@github.com:RicherLan/fitcoach-website.git
git push -u origin main
```

> 如果你用 HTTPS 推送，把 remote 改成：
> `git remote add origin https://github.com/RicherLan/fitcoach-website.git`

### 步骤 3：开启 GitHub Pages

1. 打开 https://github.com/RicherLan/fitcoach-website/settings/pages
2. **Source** 选择：`Deploy from a branch`
3. **Branch** 选择：`main` + `/ (root)`
4. 点 **Save**
5. 等待 1-3 分钟，页面上方会出现绿色提示：
   > Your site is live at `https://richerlan.github.io/fitcoach-website/`

### 步骤 4：绑定自定义域名 migofitai.com

仓库已包含 `CNAME` 文件（内容为 `migofitai.com`），GitHub Pages 会自动识别。
你只需要在 **DNS 服务商**（推荐用 Cloudflare 或 DNSPod）做一条解析：

| 主机记录 | 记录类型 | 值                          |
|---------|---------|-----------------------------|
| `@`     | A       | 185.199.108.153             |
| `@`     | A       | 185.199.109.153             |
| `@`     | A       | 185.199.110.153             |
| `@`     | A       | 185.199.111.153             |
| `www`   | CNAME   | richerlan.github.io         |

> GitHub Pages 官方 A 记录见：https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site

DNS 生效后（一般 5-30 分钟），打开 https://migofitai.com 即可访问。
然后到 GitHub Pages 设置页勾选 **Enforce HTTPS**（等证书自动签发完成）。

## 后续维护

- **改内容**：直接编辑对应 html，`git commit` + `git push` 后约 1 分钟自动重新发布
- **加页面**：在根目录新增 html 文件，记得在导航栏（每个文件的 `nav-links` 部分）和 footer 加入口
- **改样式**：编辑 `assets/style.css`，使用 CSS 变量集中调色（顶部 `:root` 块）

## 迁移到腾讯云（可选 / 备案后启用）

如果未来想把网站搬到腾讯云 CVM：

```bash
# 把整个目录上传到服务器 /var/www/migofitai/
rsync -avz --exclude='.git' ./ root@<服务器IP>:/var/www/migofitai/
# Nginx 配置：
# server { listen 443 ssl; server_name migofitai.com; root /var/www/migofitai; index index.html; }
```

GitHub Pages 与自建 Nginx 不能同时绑定同一域名，迁移时切换 DNS A 记录指向服务器即可。

## 微信审核常见检查点

本站已经覆盖以下微信开放平台 / Apple App Store / Google Play 通用审核要求：

- ✅ 产品名称、产品介绍、功能描述（[index.html](index.html)）
- ✅ 隐私政策（[privacy.html](privacy.html)，含设备权限调用清单、第三方 SDK 清单、用户权利、未成年人保护）
- ✅ 用户服务协议（[terms.html](terms.html)，含会员/订阅/退款/免责）
- ✅ 公司全称 + 联系邮箱（所有页面 footer + [contact.html](contact.html)）
- ⚠️ ICP 备案号（已购腾讯云服务器，备案通过后把 footer `.icp-placeholder` 占位换成真实备案号）

## License

© 2025 北京跃动无限科技有限公司 版权所有。
