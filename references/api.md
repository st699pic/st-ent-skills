# 699pic OpenAPI MCP

本 Skill 对接本机的 `st-mcp` MCP server，服务目录：

- `/Users/huihui/.openclaw/mcp/st-mcp`

服务通过 `mcporter` 注册名：

- `st-mcp`

可用 tools：

- `search_photos`
- `search_videos`
- `download_asset`
- `get_download_records`
- `check_downloaded`

## 建议用法

- 先搜索，再给出候选结果
- 搜索结果默认输出为 Markdown 图片文档，不要只给裸链接
- 如果 `preview_url` / `thumbnail_url` 以 `//` 开头，补成 `https://` 后再用于 Markdown 图片
- 下载前确认 `asset_type` 与 `id`
- 若要判断企业是否已下载，先调用 `check_downloaded`
- 若用户要查历史下载记录，调用 `get_download_records`

## 常用 mcporter 示例

```bash
mcporter list st-mcp --schema
mcporter call st-mcp.search_photos keywords=春节 limit=10 --output json
mcporter call st-mcp.search_videos keywords=城市航拍 limit=10 --output json
mcporter call st-mcp.check_downloaded content_id=123456 type=1 --output json
```
