# MCP Directory Submission Checklist

Use this checklist before syncing this listing to the public WeChat Channels MCP repository, submitting it to MCP directories, or updating a directory entry.

## Public Repository

- Primary repository name: `wechat-channels-mcp`
- Fallback repository name if unavailable: `wechat-channels-socialdatax-mcp`
- Repository URL after creation: `https://github.com/DevinChen2014/wechat-channels-mcp`
- Repository description: `微信视频号 MCP / WeChat Channels MCP by SocialDataX for hot search, video search, video and image-post details, comments, comment replies, user profiles, creator videos and image posts, and transcript, plus WeChat Official Account article details and engagement statistics.`
- Suggested repository topics: `mcp`, `mcp-server`, `wechat`, `wechat-channels`, `wechat-channels-mcp`, `wechat-official-account`, `socialdatax`, `social-insights`, `marketing-research`, `comment-analysis`, `creator-analytics`
- Root README title: `微信视频号与公众号 MCP | WeChat Channels and Official Account MCP`
- Product: `SocialDataX` / `社媒数据助手`
- Website: `https://socialdatax.com`
- Registry name: `com.52choujiang/wechat-channels-insights`
- Future registry name: `com.socialdatax/wechat-channels-insights`
- Hosted MCP endpoint: `https://mcp.socialdatax.com/wechat/mcp`
- Hosted auth: `Authorization: Bearer <SOCIALDATAX_API_KEY>`
- Default client transport: hosted `streamable-http`
- Command/stdio fallback: `npx -y mcp-remote https://mcp.socialdatax.com/wechat/mcp --header "Authorization: Bearer <SOCIALDATAX_API_KEY>"`
- License: MIT for the public documentation and examples only

## Safety Checks

- No real API Key values are present.
- No private backend implementation is included.
- No production configuration is included.
- No internal samples are included.
- No account data or credentials are included.
- No generated build output is included.
- Public text uses neutral product wording.
- Public docs do not expose internal business code.

## Required Files

- `README.md`
- `LICENSE`
- `server-card.json`
- `mcp.json`
- `glama.json`
- `examples/streamable_http_config.json`
- `examples/claude_desktop_config.json`
- `examples/cursor_mcp.json`
- `examples/codex_config.toml`
- `assets/logo.png`

## Directory Checks

- Hosted streamable HTTP clients can connect directly to `https://mcp.socialdatax.com/wechat/mcp` with `Authorization: Bearer <SOCIALDATAX_API_KEY>`.
- Current public capability version: `0.1.4`
- Hosted production and official MCP Registry both verified at `0.1.4`, with 24 tools, on `2026-10-09`.
- With a valid key, hosted MCP `initialize` succeeds.
- Hosted MCP `tools/list` and the local server card both contain 24 tools, including `wechat_search_finder_user`; verified on `2026-10-09`.
- `socialdatax_get_points_balance` is present in `tools/list`.
- `wechat_get_hot_search_list` is present in `tools/list`; if it is missing, deploy the latest service before publishing.
- `wechat_get_user_info_by_url` is present in `tools/list`; if it is missing, deploy the latest service before publishing.
- `wechat_search_mp_articles` is present in `tools/list`; if it is missing, deploy the latest service before publishing.
- `wechat_get_mp_article_detail_by_url` is present in `tools/list`; if it is missing, deploy the latest service before publishing.
- `wechat_get_mp_account_info_by_account_id` is present in `tools/list`; if it is missing, deploy the latest service before publishing.
- `wechat_get_mp_account_articles_by_account_id` is present in `tools/list`; if it is missing, deploy the latest service before publishing.
- `wechat_get_mp_article_stats_by_url` is present in `tools/list`; if it is missing, deploy the latest service before publishing.
- `wechat_get_mp_article_comments_by_url` and `wechat_get_mp_article_comment_replies_by_url` are present in `tools/list`; if either is missing, deploy the latest service before publishing.
- `wechat_get_video_share_url_by_object_id` is present in `tools/list`; if it is missing, deploy the latest service before publishing.
- `wechat_submit_video_speech_text_by_video_url`, `wechat_submit_video_speech_text_by_encrypted_object_id`, and `wechat_get_video_speech_text_job` are present in `tools/list`; if any are missing, deploy the latest service before publishing.
- `examples/codex_config.toml` uses remote HTTP URL and `bearer_token_env_var`, not `mcp-remote`.
- `examples/cursor_mcp.json` uses remote HTTP URL and `headers` with `${env:SOCIALDATAX_API_KEY}`, not `mcp-remote`.
- `mcp.json` is explicitly command/stdio fallback and uses `mcp-remote`.
- Before submitting to directories, verify `https://mcp.socialdatax.com/wechat/.well-known/mcp/server-card.json` returns the WeChat Channels server card, not the root XHS server card.

## Directory Submission Order

1. Official MCP Registry
2. GitHub public repository
3. Glama
4. ModelScope MCP 广场
5. MCP.Directory
6. MCP.so
7. mcpservers.org
8. MCP Market
9. Cline MCP Marketplace
10. awesome-mcp-servers / awesome-remote-mcp-servers

## Search Keywords To Verify After Approval

- `WeChat Channels`
- `WeChat Channels MCP`
- `WeChat Channels data MCP`
- `WeChat Channels video research MCP`
- `WeChat Channels comments MCP`
- `WeChat Official Account MCP`
- `WeChat Official Account article MCP`
- `微信视频号`
- `微信视频号 MCP`
- `视频号`
- `视频号 MCP`
- `视频号 数据 MCP`
- `视频号 热榜 MCP`
- `视频号 评论 MCP`
- `视频号 用户 MCP`
- `微信公众号文章 MCP`
- `公众号文章详情 MCP`
- `SocialDataX`
- `社媒数据助手`
