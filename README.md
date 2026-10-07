# xiaohongshu-articles

## 统一发布与内容索引

总入口：https://zcxxcz.github.io/ 。本项目通过公开 `catalog.json` 接入全文搜索。`publish.json` 显式列出公开内容，不包含账号数据。

Windows/macOS 均安装 Node.js 24、Git 与 GitHub CLI，先 `gh auth login`。使用独立任务分支，提交本任务文件后运行 `npm run publish`：创建 PR → 等待 Publish Pages 检查 → 自动合并 → GitHub Actions 构建发布 → 自动刷新总索引。工作区必须干净；main 更新时先合并最新 main 并解决冲突。不需要本地运行 gh-pages。

Pages Source 使用 GitHub Actions，正式产物只由云端构建。直接推送 main 后，总索引由每日补漏任务更新；需要立即更新则运行 `node scripts/publish.mjs --refresh-only`。不自动执行数据库迁移。新增或修改公开内容时同步 publish.json 的元信息和 textPaths；不得将私人文件加入索引。
