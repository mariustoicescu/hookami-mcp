# Sensei by Hookami — MCP Server

**Live YouTube trend intelligence, inside ChatGPT, Claude, and any MCP client.**

Hookami is an AI workspace for YouTube creators that brings together current trend research, personalized creator intelligence, scripts, thumbnails, and pre-publish video analysis. Sensei connects that research to creative decisions. This MCP server connects it to the AI assistant you already use — so instead of guessing what to film, your assistant can check what is *actually* rising on YouTube right now, how fast a topic is moving, which videos are overperforming, and whether you're early or late.

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

The assistant can consult Hookami's current trend research, video examples and recent sources. Check the source dates and supporting videos when choosing your angle. The research is tied to Hookami's tracked creator activity.

## A practical YouTube research workflow

After connecting, send these prompts in order in one chat. Replace the category and audience with your own. These are prompts to run, not a saved benchmark: the results depend on the topic, available data and your plan.

### 1. Find a topic

> Use Hookami to find five trending topics in Tech & Gadgets. Show the current Hookami ranking and explain the signals returned. I make English-language videos for beginners.

**Tool:** `search_trending_keywords`. **Result:** a ranked shortlist from Hookami's tracked creator pool, with available trend signals. Choose a specific topic from the answer.

### 2. Check its timing and video evidence

> For [chosen topic], use Hookami to check the trend lifecycle and find five long-form video examples, ordered by outlier performance. Include titles, channels, views, published dates, performance and YouTube links where available. Explain what the returned evidence supports.

**Tools:** `get_keyword_timing` and `search_videos`. **Result:** a timing assessment and a checkable shortlist. The video tool supports format selection and outlier ordering of retrieved matches. That order is not a ranking of every video on YouTube. Keep unavailable metrics and unknown timing stages explicit.

For a news-driven topic, ask: *Use Hookami to check the latest coverage of [chosen topic]. Show the source links and publication dates.* `current_sources` supplies recent coverage; the assistant interprets it.

### 3. Build an original brief

> Use the Hookami evidence above to propose three original angles for my audience. Separate observed facts from your ideas, cite the supporting videos, and flag missing information. Develop the strongest angle into a brief: audience promise, hook, three beats and a thumbnail concept.

**Result:** the host assistant creates a text brief from the retrieved evidence. It is the assistant's creative proposal, not another measured signal. Open the Hookami tool activity to inspect the actual research results.

Copy the topic, brief and reference-video links into the relevant [Hookami workspace](https://hookami.ai/how-it-works). The connector does not automatically save the chat or create a workspace project. On Free, researching a new topic may use a Deep Dive; follow-ups on an already opened topic share that topic's access window.

See the [visual workflow and copyable prompts](https://hookami.ai/anywhere#youtube-research-workflow).

## The Hookami workspace

Research in this connector can support the next step in [Hookami](https://hookami.ai/how-it-works):

- [Creator Lens](https://hookami.ai/features/creator-lens): channel, video and niche research, Channel DNA, related opportunities and personal context for Sensei.
- [Blueprint](https://hookami.ai/features/blueprint) and [Forge](https://hookami.ai/features/forge): study a video's creative structure and build an original script.
- [Frame Studio](https://hookami.ai/features/frame-studio): generate images from prompts and references, analyze a frame or compare two or three options.
- [Pre-Publish](https://hookami.ai/features/pre-publish): review an actual video and compare its edited versions.

These are web-app capabilities. The MCP connector retrieves research and product information; it does not generate images or run every Hookami workspace. The ElevenLabs tool provides voiceover guidance, not audio generation.

## Connect

Setup checked against official host documentation on **October 11, 2026**. Account and workspace permissions can affect the options you see.

### ChatGPT — custom MCP plugin

1. Sign in to ChatGPT and have an active [Hookami account](https://hookami.ai/signup) ready.
2. In [ChatGPT Plugins](https://chatgpt.com/plugins), use **+ → Add custom MCP server**.
3. Name it `Hookami`. Suggested description: `Live YouTube trend intelligence and creator strategy from Sensei by Hookami.`
4. Choose **Server URL**, enter `https://mcp.hookami.com/mcp` and use **OAuth** authentication.
5. Review the custom MCP warning, then choose **Create as a plugin**. Sign in to Hookami and authorize access when prompted.
6. Install the resulting plugin. Start a new chat, type `@` and select Hookami. Send the first research prompt above.

If the form asks for an icon, use [`hookami-chatgpt-plugin.png`](./hookami-chatgpt-plugin.png). If the custom-server option is unavailable, check your host account or workspace permissions. [OpenAI's official connection guide](https://developers.openai.com/plugins/deploy/connect-chatgpt) documents the current flow.

Check the response's tool activity to confirm that Hookami supplied the research. Selecting a plugin makes it available to the assistant; a generic answer without a Hookami tool result is not evidence of a lookup.

### Claude (claude.ai & Desktop)

1. You'll need a Hookami account. Custom connectors work on every Claude plan — Claude's free plan allows one custom connector.
2. Open **Customize → Connectors**, press **+**, and choose **Add custom connector**.
3. Name it **Hookami**, paste `https://mcp.hookami.com/mcp` and continue through the detected authentication settings.
4. Choose to sign in, finish adding the connector and authorize your Hookami account when prompted. This flow does not require a developer token or pasting your Hookami password into Claude.
5. In a new chat, open **+ → Connectors**, enable Hookami and send the first research prompt above. Web-configured connectors can also be used on Desktop and mobile.

For Team or Enterprise, your organization owner must add the connector first. See [Claude's official custom-connector guide](https://support.claude.com/en/articles/11175166-get-started-with-custom-connectors-using-remote-mcp).

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
- **Public research, not private channel analytics.** The connector does not connect to your private YouTube Studio analytics or retrieve private CTR and retention reports.
- **Your conversation stays with your AI provider.** Hookami receives only the tool requests made on your behalf and returns results. See the [Privacy Policy](https://hookami.ai/privacy) and [Terms](https://hookami.ai/terms).

## Troubleshooting

- **"This account can't connect"** — make sure your Hookami account is active (log in at [hookami.ai](https://hookami.ai)), check the connection status in Integrations, and verify that your AI host permits custom connectors.
- **Stopped answering** — check [Settings → Integrations](https://hookami.ai/settings/integrations) for your connection status and Deep Dive counters. Confirm that Hookami is enabled in the current chat. If the tool list is stale, refresh the ChatGPT plugin connection; if authorization has expired, reconnect your Hookami account.
- **Lost a developer token** — revoke it in Settings → Integrations and create a new one. Tokens are shown only once.

---

**Sensei by Hookami** · [hookami.ai](https://hookami.ai) · © SEIA PRODUCTION S.R.L.
*We don't copy trends. We read them — so you decide what's worth filming.*
