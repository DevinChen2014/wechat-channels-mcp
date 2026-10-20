# 微信视频号与公众号 MCP | WeChat Channels and Official Account MCP

LobeHub 用户请使用 [LobeHub setup / 接入说明](LOBEHUB.md)，包含专属官网入口、认证和来源配置。

This public repository provides public connection docs and MCP metadata for a hosted 微信视频号与公众号 MCP / WeChat Channels and Official Account MCP service by SocialDataX.

If you are looking for a WeChat Channels MCP, 微信视频号 MCP, or 微信公众号文章 MCP for social media research workflows, this repository includes:

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
- `微信公众号文章 MCP`
- `公众号文章详情 MCP`
- `WeChat Channels MCP`
- `WeChat Channels data MCP`
- `WeChat Official Account MCP`
- `WeChat Channels video research MCP`
- `WeChat Channels comments MCP`
- `WeChat MCP`
- `微信 MCP`

## Service

- Hosted MCP endpoint: `https://mcp.socialdatax.com/wechat/mcp`
- Hosted transport: `streamable-http`
- Authentication: `Authorization: Bearer <SOCIALDATAX_API_KEY>`
- Product: `SocialDataX` / `社媒数据助手`
- Website and API Key access: <https://socialdatax.com/ai?from=github>
- Registry name: `com.52choujiang/wechat-channels-insights`
- Future registry name: `com.socialdatax/wechat-channels-insights`
- Current public capability version: `0.1.4`
- Hosted production and official MCP Registry both verified at `0.1.4`, with 24 tools, on `2026-10-09`.

## Platform MCP

Use the hosted `streamable-http` endpoint directly from clients that support authenticated remote MCP. For clients that only support command/stdio MCP servers, use `mcp-remote` as a local compatibility proxy.

## Workflow Scope

This MCP service is designed for social media content intelligence workflows. It does not provide account login, posting, editing, liking, commenting, forwarding, or other account actions.

Supported workflows include:

- Query the current API Key account's SocialDataX points balance / 积分余额、剩余积分或点数.
- Read the WeChat Channels / 微信视频号 hot search list.
- Fetch WeChat Official Account / 微信公众号 article details, body text, account information, and engagement statistics.
- Read WeChat Official Account article reading, likes, shares, collections, comments, and "wow" counts.
- Read paginated WeChat Official Account article comments and replies under a first-level comment.
- Search WeChat Channels videos by keyword with optional paging and filters.
- Resolve a WeChat Channels video or image-post link or share text into structured work details.
- Read video details when the caller already has an `encrypted_object_id`.
- Fetch paginated first-level comments on a WeChat Channels video for comment analysis.
- Fetch paginated replies under a first-level WeChat Channels video comment.
- Read user profile data when the caller already has a `v2_...@finder` user_id.
- Resolve a video or image-post link or share text into its creator profile data.
- Fetch user-posted work lists, including videos and image posts, from a work link/share text or a `v2_...@finder` user_id.
- Submit a video speech-to-text transcript task; the submit call may wait up to 240 seconds, and unfinished jobs should continue polling the same `job_id` until terminal.

## Tools

| Tool | Public purpose |
| --- | --- |
| `socialdatax_get_points_balance` | Query the current API Key account's SocialDataX points balance / 积分余额、剩余积分或点数. |
| `wechat_get_hot_search_list` | Get the current WeChat Channels / 微信视频号 hot search list. |
| `wechat_search_mp_articles` | Search WeChat Official Account / 微信公众号 articles by keyword, with sort_type, publish_time_range, and pagination. |
| `wechat_get_mp_article_detail_by_url` | Fetch WeChat Official Account / 微信公众号 article detail and body text from an article link or share text. |
| `wechat_get_mp_account_info_by_account_id` | Fetch WeChat Official Account / 微信公众号 account information from an account ID returned by article detail. |
| `wechat_get_mp_account_articles_by_account_id` | Fetch paginated WeChat Official Account / 微信公众号 articles from an account ID returned by article detail. |
| `wechat_get_mp_article_stats_by_url` | Fetch WeChat Official Account / 微信公众号 article reading, likes, shares, collections, comments, and "wow" counts from an article link or share text. |
| `wechat_get_mp_article_comments_by_url` | Fetch paginated WeChat Official Account / 微信公众号 article comments from an article link or share text. |
| `wechat_get_mp_article_comment_replies_by_url` | Fetch replies under a selected first-level comment, or let the service select one, from an article link or share text. |
| `wechat_search_finder_user` | Search WeChat Channels users by keyword or Channels ID; use the returned `user_id` to read user profiles and published posts. Supports `page_token` continuation. |
| `wechat_search_videos` | Search WeChat Channels videos by search term. Use this tool when the user needs videos found by a search term; when a video or image-post link is available, use the detail tool; when a video link is available and comments are needed, use the comment tool; when a video link or `encrypted_object_id` is available and a transcript is needed, use the speech-to-text tool. Supports `page_token` continuation. |
| `wechat_get_video_detail_by_encrypted_object_id` | Fetch structured video details when the caller already has an `encrypted_object_id`. |
| `wechat_get_video_share_url_by_object_id` | Generate a WeChat Channels work share URL from a known numeric `object_id`. |
| `wechat_get_video_detail_by_url` | Resolve a WeChat Channels video or image-post link or share text into structured work details. |
| `wechat_get_video_comments_by_object_id` | Fetch paginated first-level comments when the caller already has the same video's `object_id` and `object_nonce_id`. |
| `wechat_get_video_comments_by_url` | Fetch paginated first-level comments directly from a WeChat Channels video link or share text. |
| `wechat_get_video_comment_replies_by_comment_id` | Fetch paginated replies under a first-level comment using the same video's `object_id` and `object_nonce_id` plus the first-level `comment_id`. |
| `wechat_get_user_info_by_user_id` | Fetch user profile data when the caller already has a `v2_...@finder` user_id. |
| `wechat_get_user_info_by_url` | Resolve a WeChat Channels video or image-post link or share text into its creator profile data. |
| `wechat_get_user_posted_videos_by_user_id` | Fetch a paginated list of videos and image posts published by a user when the caller already has a `v2_...@finder` user_id. |
| `wechat_get_user_posted_videos_by_url` | Fetch a paginated list of videos and image posts published by a user from a work link or share text. |
| `wechat_submit_video_speech_text_by_video_url` | Submit a video speech-to-text transcript task from a video link or share text. The submit call may wait up to 240 seconds; if unfinished, continue polling the same `job_id` until terminal. |
| `wechat_submit_video_speech_text_by_encrypted_object_id` | Submit a video speech-to-text transcript task from an `encrypted_object_id`. The submit call may wait up to 240 seconds; if unfinished, continue polling the same `job_id` until terminal. |
| `wechat_get_video_speech_text_job` | Continue checking a video speech-to-text transcript job using a valid `job_id` supplied by the user, or a `job_id` returned by a submit tool, without creating a new task; each call waits up to 240 seconds. If unfinished, continue querying the same `job_id` until terminal. This v1 surface returns transcript plus content context, not summary. |

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

<https://socialdatax.com/ai?from=github>

Use the key as a Bearer token in the `Authorization` request header. Do not commit real API Key values to code, docs, issues, or screenshots.

## Directory Metadata

Public metadata files in this repository:

- [server-card.json](server-card.json): directory-oriented metadata for the hosted service. Official MCP Registry publishing uses the private source repo's `registry/wechat/server.json` for the current `com.52choujiang/wechat-channels-insights` entry.
- [mcp.json](mcp.json): generic command/stdio fallback config using `mcp-remote`.
- [glama.json](glama.json): Glama repository ownership metadata.
- [SUBMISSION_CHECKLIST.md](SUBMISSION_CHECKLIST.md): checklist for MCP directory submissions.

## License

The files in this public repository are released under the MIT License. The license covers the public documentation and configuration examples in this repository only. It does not cover the managed service implementation, hosted infrastructure, or any private backend code outside this repository.

## Gemini CLI extension

Install this service from its public GitHub repository:

```sh
gemini extensions install https://github.com/DevinChen2014/wechat-channels-mcp
```

When prompted, enter your own `SOCIALDATAX_API_KEY`. Get a key from [SocialDataX](https://socialdatax.com/ai?from=github); business tool calls consume SocialDataX credits. The extension connects directly to the existing hosted MCP endpoint and does not include the private service implementation.

Verify the connection with `gemini mcp list`. To change the saved key, run:

```sh
gemini extensions config socialdatax-wechat
```
