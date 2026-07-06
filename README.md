# 微信视频号 MCP | WeChat Channels MCP

This public repository provides public connection docs and MCP metadata for a hosted 微信视频号 MCP / WeChat Channels MCP service by SocialDataX.

If you are looking for a WeChat Channels MCP or 微信视频号 MCP for social media research workflows, this repository includes:

- public MCP metadata and client configuration examples
- the hosted `streamable-http` endpoint for clients that support remote MCP
- an `mcp-remote` fallback example for command/stdio-only MCP clients

The business implementation is privately hosted. This repository exposes only the public connection surface for social media content intelligence workflows.

## Search Aliases

Common search phrases for this MCP service:

- `微信视频号 MCP`
- `视频号 MCP`
- `视频号 数据 MCP`
- `视频号 热榜 MCP`
- `视频号 评论 MCP`
- `视频号 用户 MCP`
- `WeChat Channels MCP`
- `WeChat Channels data MCP`
- `WeChat Channels video research MCP`
- `WeChat Channels comments MCP`
- `Wechat MCP`
- `微信 MCP`

## Service

- Hosted MCP endpoint: `https://mcp.socialdatax.com/wechat/mcp`
- Hosted transport: `streamable-http`
- Authentication: `Authorization: Bearer <SOCIALDATAX_API_KEY>`
- Product: `SocialDataX` / `社媒数据助手`
- Website: <https://socialdatax.com>
- Registry name: `com.52choujiang/wechat-channels-insights`
- Future registry name: `com.socialdatax/wechat-channels-insights`
- Current public capability version: `0.1.1`

## Platform MCP

Use the hosted `streamable-http` endpoint directly from clients that support authenticated remote MCP. For clients that only support command/stdio MCP servers, use `mcp-remote` as a local compatibility proxy.

## Workflow Scope

This MCP service is designed for social media content intelligence workflows. It does not provide account login, posting, editing, liking, commenting, forwarding, or other account actions.

Supported workflows include:

- Read the WeChat Channels / 微信视频号 hot search list.
- Search WeChat Channels videos by keyword with optional `page_token` continuation and filters; do not pass `page`.
- Resolve a WeChat Channels video link or share text into structured video details.
- Read video details when the caller already has an `encrypted_object_id`.
- Fetch paginated first-level comments for comment analysis.
- Fetch paginated replies under a first-level comment.
- Read user profile data when the caller already has a `user_id`.
- Fetch user posted video lists from a profile/video link or `user_id`.
- Submit a video speech-to-text transcript task; submit tools 提交完成后最多短等 15 秒, and unfinished jobs can be polled by `job_id`.

## Tools

| Tool | Public purpose |
| --- | --- |
| `wechat_get_hot_search_list` | Get the current WeChat Channels / 微信视频号 hot search list. |
| `wechat_search_videos` | Search WeChat Channels videos by keyword with optional `page_token` continuation and filters; do not pass `page`. |
| `wechat_get_video_detail_by_encrypted_object_id` | Fetch structured video details when the caller already has an `encrypted_object_id`. |
| `wechat_get_video_detail_by_url` | Resolve a WeChat Channels video link or share text into structured video details. |
| `wechat_get_video_comments_by_object_id` | Fetch paginated first-level comments when the caller already has the video object identifiers. |
| `wechat_get_video_comments_by_url` | Fetch paginated first-level comments directly from a WeChat Channels video link or share text. |
| `wechat_get_video_comment_replies_by_comment_id` | Fetch paginated replies under a first-level comment by video object identifiers and `comment_id`. |
| `wechat_get_user_info_by_user_id` | Fetch user profile data when the caller already has a `user_id`. |
| `wechat_get_user_posted_videos_by_user_id` | Fetch a paginated list of videos published by a user when the caller already has a `user_id`. |
| `wechat_get_user_posted_videos_by_url` | Fetch a paginated list of videos published by a user from a profile or video link. |
| `wechat_submit_video_speech_text_by_video_url` | Submit a video speech-to-text transcript task from a video link or share text. 提交完成后最多短等 15 秒. |
| `wechat_submit_video_speech_text_by_encrypted_object_id` | Submit a video speech-to-text transcript task from an `encrypted_object_id`. 提交完成后最多短等 15 秒. |
| `wechat_get_video_speech_text_job` | Check a video speech-to-text transcript job by `job_id` without creating a new task. This v1 surface returns transcript only, not summary. |

## Quick Start

For clients that support authenticated `streamable-http`, use the hosted endpoint directly:

```json
{
  "mcpServers": {
    "socialdatax-wechat": {
      "type": "streamable_http",
      "url": "https://mcp.socialdatax.com/wechat/mcp",
      "headers": {
        "Authorization": "Bearer <SOCIALDATAX_API_KEY>"
      }
    }
  }
}
```

A ready-to-copy example is available in [`examples/streamable_http_config.json`](examples/streamable_http_config.json).

For command/stdio-only MCP clients, use `mcp-remote`:

```json
{
  "mcpServers": {
    "socialdatax-wechat": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote",
        "https://mcp.socialdatax.com/wechat/mcp",
        "--header",
        "Authorization: Bearer <SOCIALDATAX_API_KEY>"
      ]
    }
  }
}
```

Claude Code can use remote HTTP directly:

```bash
claude mcp add --transport http socialdatax-wechat https://mcp.socialdatax.com/wechat/mcp --header 'Authorization: Bearer ${SOCIALDATAX_API_KEY}'
```

Persist `SOCIALDATAX_API_KEY` in the runtime environment or client Secret before restarting Claude Code.

Claude Desktop should use its remote MCP / Connectors UI when available. If a local configuration file in your version only supports command/stdio servers, use the `mcp-remote` fallback.

## Client Examples

Configuration examples are available in [examples](examples/):

- [Command/stdio fallback config](mcp.json)
- [Claude Desktop fallback config](examples/claude_desktop_config.json)
- [Cursor remote HTTP config](examples/cursor_mcp.json)
- [Codex remote HTTP config](examples/codex_config.toml)
- [Direct streamable HTTP config](examples/streamable_http_config.json)

## API Key

Request or manage API access from the product website:

<https://socialdatax.com>

Use the key as a Bearer token in the `Authorization` request header. Do not commit real API keys to code, docs, issues, or screenshots.

## Directory Metadata

Public metadata files in this repository:

- [server-card.json](server-card.json): directory-oriented metadata for the hosted service. Official MCP Registry publishing uses the private source repo's `registry/wechat/server.json` for the current `com.52choujiang/wechat-channels-insights` entry.
- [mcp.json](mcp.json): generic command/stdio fallback config using `mcp-remote`.
- [glama.json](glama.json): Glama repository ownership metadata.
- [SUBMISSION_CHECKLIST.md](SUBMISSION_CHECKLIST.md): checklist for MCP directory submissions.

## License

The files in this public repository are released under the MIT License. The license covers the public documentation and configuration examples in this repository only. It does not cover the managed service implementation, hosted infrastructure, or any private backend code outside this repository.
