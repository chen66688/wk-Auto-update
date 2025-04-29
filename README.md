
# wk-Auto-update

自动同步 BPB-Worker-Panel 项目的最新 worker.js 文件。

## 🚀 快速开始（适合 Fork）
Fork GitHub 仓库
1. 点击右上角 Fork 本仓库到你的 GitHub 账号。
2. 打开你的仓库，进入 Actions 页面，点击 Enable workflows（启用 GitHub Actions）。
3. 无需其他配置，GitHub 默认的 GITHUB_TOKEN 权限即可推送更新。
4. 你可以手动点击 Run workflow，也可以等待每天定时自动检查。
.......... cloud flare部署pages节点 ..........


在 Cloudflare Pages 创建项目
1：登录 Cloudflare 后台 → 左侧点击【Pages】→ 【创建项目】
2：选择 连接到 GitHub：
 选择你的 Fork 仓库
 允许 Cloudflare Pages 读取你的 GitHub 仓库权限
3：项目基本配置：
 项目名字自己取，比如 cf-auto-update
 分支选择 main

配置环境变量（Variables）

在 Pages 项目设置里：

打开 【设置 Settings】→ 【环境变量 Environment Variables】
添加这些变量：

名字	内容
UUID	自己生成一个 UUID，比如去 https://1024tools.com/uuid
TR_PASS	自己设一个密码
FALLBACK	  推荐设置成 example.com
⚡ 注意：

变量名字全大写！
TR_PASS、FALLBACK 都是根据项目需求补充的。

配置 KV 存储绑定

Pages Functions 也可以使用 KV，
需要绑定 KV 存储桶。

步骤：

1：Cloudflare 后台左侧【Workers & KV】→ 【KV 存储】
2：创建一个新的命名空间（比如叫 test）
3：回到 Pages 项目的【Settings → KV Bindings】
4:添加绑定：

Binding Name	kv
Namespace	你刚才创建的 test

✅ Binding Name 必须是 kv 小写，保持和代码对应！

访问面板
部署完成后：

1：访问你的 Pages 地址，比如：
https://your-project-name.pages.dev/panel
2：第一次访问，会让你设置后台管理密码
3：进入后台后，可以自由开关协议（Trojan、VLess 等），生成订阅链接

常见问题和注意事项
如果访问时报错提示【需要 UUID/TR_PASS/KV】，说明变量或者 KV 没有设置正确，请检查
若绑定自己的域名，可以在 Pages → 自定义域名那里添加
Pages 默认会自动根据 GitHub 更新来重新部署，不需要手动部署！
总结
✅ 通过 Cloudflare Pages + GitHub 自动部署，你可以：

免费、快速搭建自己的节点服务
每次 GitHub 仓库有更新，Pages 自动同步，无需人工操作
通过配置 UUID / 密码 / 回退域名，自由控制节点
搭配 GitHub Actions 自动同步源码，真正做到零维护、永久免费、超快节点！
