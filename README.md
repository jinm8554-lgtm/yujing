# 余烬纪元

Cocos Creator 3.8.5 导出的手机网页游戏。本仓库已经包含网页发布文件，部署时无需安装 Node.js、运行 npm 或重新构建。

## 宝塔部署

1. 在宝塔终端确认 Git 可用：`git --version`。若尚未安装，请通过服务器对应的包管理器安装 Git。
2. 将仓库克隆到一个尚不存在的目录（如果该路径已有文件，请换一个新目录，不要覆盖原站点）：

   ```bash
   git clone https://github.com/jinm8554-lgtm/yujing.git /www/wwwroot/yujing
   ```

3. 在宝塔「网站」中添加站点，绑定自己的域名，选择「纯静态」，数据库和 FTP 均不创建。网站根目录设置为 `/www/wwwroot/yujing`，运行目录保持根目录，默认文档使用 `index.html`，伪静态留空。
4. 将域名解析到服务器公网 IP，放行云服务器安全组和系统防火墙中的 TCP 80、443 端口。
5. 用 HTTP 打开域名检查游戏，随后在站点的 SSL 设置中部署证书并开启 HTTPS。

文件结构应保持完整：根目录下直接包含 `index.html`、`index.js`、`application.js`、`style.css`，以及 `assets/`、`cocos-js/`、`src/` 三个目录。

如果从 ZIP 部署，请下载仓库 ZIP 后上传解压，并把网站根目录设置到包含 `index.html` 的那一层。

## 更新

在宝塔终端执行：

```bash
cd /www/wwwroot/yujing
git pull --ff-only
```

若服务器上有本地修改导致拉取失败，请先保存并处理修改，不要直接强制覆盖。更新后若仍显示旧版，尝试强制刷新；若启用了 CDN，刷新对应缓存。

## 运行说明

- 游戏资料当前使用浏览器本地存储，不提供云端账号、云存档或跨设备同步。切换域名、协议或端口不会自动迁移原地址的存档。
- 请通过 HTTP/HTTPS 访问，避免双击 HTML 用 `file://` 打开。
- `.wasm` 文件应以 `application/wasm` 类型响应；如果浏览器报 MIME 错误，请检查 Web 服务器的 MIME 配置。
- Git 部署时保留宝塔默认的敏感路径访问限制，确认网站不能通过 HTTP 访问 `/.git/config`（应返回 403 或 404）。
