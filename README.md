# Sensei by Hookami — MCP Server

**Live YouTube trend intelligence, inside ChatGPT, Claude, and any MCP client.**

Sensei is Hookami's creative-strategy layer for video creators. This MCP server connects it to the AI assistant you already use — so instead of guessing what to film, your assistant can check what is *actually* rising on YouTube right now, how fast a topic is moving, which videos are overperforming, and whether you're early or late.

```
https://mcp.hookami.com/mcp
```

Remote MCP server · Streamable HTTP · OAuth sign-in · read-only

**Website:** [hookami.ai](https://hookami.ai) · **Setup page:** [hookami.ai/anywhere](https://hookami.ai/anywhere) · **Create a free account:** [hookami.ai/signup](https://hookami.ai/signup)

---

## What you can ask

- *"What's trending on YouTube right now?"*
- *"Is it too late to make videos about AI agents?"*
- *"Find outlier videos about home espresso — what makes them work?"*
- *"What's rising in gaming this week, and what should I film next?"*
- *"Give me the full picture on 'dopamine detox' — momentum, examples, angles."*

Sensei answers from Hookami's live signal — a curated pool of trend-setting creators tracked in near-real-time — and always says so plainly when a signal is early or thin. No invented metrics.

## Connect

### ChatGPT — Developer mode

1. You need a ChatGPT account and an active Hookami account ([hookami.ai](https://hookami.ai)). If Developer mode is unavailable, ask your workspace admin to enable it.
2. Open ChatGPT **Settings → Security and login** and turn on **Developer mode**.
3. Open **Settings → Plugins → Browse plugins** and press the **+** button.
4. Complete **New Plugin**:
   - **Icon:** upload [`hookami-chatgpt-plugin.png`](./hookami-chatgpt-plugin.png) from this repo.
   - **Name:** `Hookami`
   - **Description:** `Live YouTube trend intelligence and creator strategy from Sensei by Hookami.`
   - **Connection:** `Server URL`
   - **Server URL:** `https://mcp.hookami.com/mcp`
   - **Authentication:** `OAuth` — do not change Advanced OAuth settings.
5. Accept the custom MCP warning and press **Create**.
6. Sign in to Hookami and press **Allow**.
7. Start a new chat and type `@Hookami`, or select **Hookami** from the `+` menu.
8. Ask normally, for example: *What's trending in gaming right now?*

> **Use Hookami in a chat.** Start a new chat and type `@Hookami`, then select Hookami from the
> list. You can also press `+` and choose Hookami — look under **More** if it is not immediately
> visible. Once Hookami appears beside your prompt, ask normally. ChatGPT may choose installed
> plugins automatically when relevant, but `@Hookami` makes sure this request uses Hookami.

### Claude (claude.ai & Desktop)

1. You'll need a Hookami account. Custom connectors work on every Claude plan — Claude's free plan allows one custom connector.
2. Open **Customize → Connectors**, press **+**, and choose **Add custom connector**.
3. Name it (say, **Hookami**) and paste `https://mcp.hookami.com/mcp` as the URL.
4. Leave **Advanced settings** (OAuth Client ID / Secret) untouched — they're optional.
5. **Add** → a Hookami window opens → sign in → **Allow**.
6. In a new chat, switch the connector on in the tools menu. It follows you to claude.ai, Desktop, and mobile.

### Claude Code (terminal)

Claude Code connects with a personal developer token instead of the sign-in flow. Create one in **[Settings → Integrations](https://hookami.ai/settings/integrations)** (it is shown once — treat it like a password, and never commit it anywhere), then:

```bash
claude mcp add --transport http hookami https://mcp.hookami.com/mcp \
  --header "Authorization: Bearer hk_mcp_YOUR_TOKEN"
```

Verify with `claude mcp list`. Revoke the token anytime from the same Settings page — access is cut instantly.

## Tools

| Tool | What it does |
|---|---|
| **Radar — always open** | |
| `search_trending_keywords` | What's trending right now — global or by category, with velocity signals |
| `get_keyword_stats` | How popular a keyword/topic is in Hookami's tracked pool |
| `current_sources` | Fresh press & sources on a topic — did it launch, who won, is it confirmed |
| **Deep research** | |
| `get_trend_intelligence` | The full picture on one topic: momentum, drivers, examples, angles |
| `search_videos` | Real performing videos on a topic, with performance signals |
| `get_related_keywords` | The keyword neighborhood around a topic |
| `get_keyword_timing` | Lifecycle timing — are you early, riding the wave, or late |
| **Context & guidance** | |
| `get_sensei_guidance` | Sensei's operating guide — how your assistant should use the data |
| `get_hookami_product_context` | What Hookami's products do |
| `get_youtube_algorithm_context` | How the YouTube algorithm actually works |
| `get_elevenlabs_v3_context` | Prompt & audio-tag guidance for ElevenLabs v3 voiceovers |

## Access & plans

Any **active Hookami account** can connect — [create one free](https://hookami.ai).

| | Free | Paid plans |
|---|---|---|
| Radar (trending, keyword stats, fresh news) | ✅ Always open | ✅ Always open |
| Deep research on a specific topic | **3 Deep Dives per 30-day window** + 1 limited preview | ✅ Unlimited |
| Context & guidance tools | ✅ | ✅ |

A *Deep Dive* opens one topic in full — video examples, trend intelligence, related keywords, timing — and follow-ups on that same topic stay free for the whole window. The window starts with your first Deep Dive; your live counters are always visible in [Settings → Integrations](https://hookami.ai/settings/integrations).

## Data & trust

- **Read-only.** The connector can research; it cannot modify your Hookami account or content.
- **Honest signal.** Hookami tracks a curated pool of trend-setting creators — not all of YouTube — and Sensei says so when data is early or thin.
- **Your conversation stays with your AI provider.** Hookami receives only the tool requests made on your behalf and returns results. See the [Privacy Policy](https://hookami.ai/privacy) and [Terms](https://hookami.ai/terms).

## Troubleshooting

- **"This account can't connect"** — make sure your Hookami account is active (log in at [hookami.ai](https://hookami.ai)). Free connections may occasionally be paused for maintenance; paid plans always connect.
- **Stopped answering** — check [Settings → Integrations](https://hookami.ai/settings/integrations) for your connection status and Deep Dive counters. If it persists: recreate the ChatGPT developer-mode plugin, or remove and re-add the Claude connector.
- **Lost a developer token** — revoke it in Settings → Integrations and create a new one. Tokens are shown only once.

---

**Sensei by Hookami** · [hookami.ai](https://hookami.ai) · © SEIA PRODUCTION S.R.L.
*We don't copy trends. We read them — so you decide what's worth filming.*
