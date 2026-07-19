# 自定义文件后台

该后台不使用 Decap 或 GitHub OAuth。访问 `/admin/` 后输入 Cloudflare Worker 中的 `ADMIN_PASSWORD` 即可编辑网站内容。

后台把内容保存到 GitHub 仓库的 `data/content.json`，Cloudflare Pages 会自动重新发布网站。

Worker 需要三个配置：

- Secret `ADMIN_PASSWORD`：后台登录密码。
- Secret `GITHUB_TOKEN`：GitHub Fine-grained token，只授予 `mishideoo/guangxing` 的 Contents Read and write 权限。
- Variable `GITHUB_REPO`：`mishideoo/guangxing`。

可选 Variable `ALLOWED_ORIGIN`：`https://guangxing.pages.dev`。
