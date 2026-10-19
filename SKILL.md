---
name: interactive-game-research-moodboard
description: Research interactive marketing games through screenshot-backed Xiaohongshu cases and user feedback, derive three evidence-backed visual directions, and create a separate curated visual-reference board. Use for lottery, quiz, collection, cultivation, task, level, synthesis, branded H5, mini-game campaigns, and gamified growth mechanics. Exclude ordinary brand identity and non-interactive campaign venues.
---

# Interactive Game Research & Moodboard

Research interactive games as a UI/UX design partner. Produce two Chinese visual HTML files: one for `竞品调研/用户反馈`, then one for `视觉参考`. Keep sources auditable and distinguish observation, user evidence, interpretation, and recommendation.

## Reference Reading Order

- At task start, read [references/overview.md](references/overview.md) to confirm scope, terminology, inputs, and deliverables.
- Before accepting or interpreting evidence, read [references/rules.md](references/rules.md), then the existing detailed [evidence rules](references/evidence-rules.md).
- Before moving between research, direction, and reference-collection stages, read [references/workflow.md](references/workflow.md).
- Before searching Xiaohongshu, read [references/xiaohongshu-search-protocol.md](references/xiaohongshu-search-protocol.md).
- [examples/input-01.md](examples/input-01.md) and [examples/output-01.md](examples/output-01.md) are review and regression examples. Do not treat their project facts as live evidence.

## Start-of-Task User Guide

On every explicit invocation of this skill, make the first assistant response a concise Chinese `使用流程` guide **before opening a browser, collecting evidence, or creating files**. This is a user-facing orientation, not an internal plan.

Render the process as **five separate fenced `text` blocks**. In Codex these render as the same card style as the invocation examples; in Claude Code and other agents they remain readable Markdown. Do not use a bullet list as the primary process layout. Present the cards in order from `01｜输入背景` to `05｜参考图交付`, then place the project-input request in plain text immediately after all five cards.

Each card must contain both `我会做什么` and `你需要参与`. The user must be able to tell at a glance which stages need a decision:

1. `01｜输入背景` — clarify the project scope from supplied materials. User participation: provide the requested information after the cards; a partial brief is enough to start.
2. `02｜证据采集` — collect Xiaohongshu competitor and user evidence. User participation: no continuous monitoring is needed while collection runs.
3. `03｜证据确认` — present retained, excluded, and missing evidence. User participation: explicitly reply with what to retain, exclude, or add. Do not generate visual directions before this confirmation unless the user explicitly waives it.
4. `04｜方向确认` — read the three official trend pages, cross-analyze accepted evidence, and present exactly three directions. User participation: explicitly choose, adjust, or reject directions before visual-reference collection begins.
5. `05｜参考图交付` — open original detail pages, curate 10 de-duplicated original assets per approved direction, then create the visual-reference HTML. User participation: review the delivered board and request revisions if needed.

After the fifth card, display the project-input request in plain text exactly as specified in the required template. It asks for the project name, game mechanic, and any available PRD, relevant links, or screenshots. A partial brief is enough to start. Do not show invocation examples or explain skill-call syntax.

If the user already specifies a stage constraint such as “只做证据采集” or “直接进入视觉参考”, repeat that constraint in the relevant card and follow it. After showing the guide, extract inputs and proceed; ask at most one focused question only when an unknown would materially change research.

### Required First-Response Template

Use this structure, adapting the bracketed text to the brief:

````markdown
## 使用流程

```text
01｜输入背景
我会做什么：根据你提供的资料明确项目范围与研究重点。
你需要参与：在全部流程卡片后提供项目资料；资料不全也可开始。
```

```text
02｜证据采集
我会做什么：在小红书采集竞品案例与用户反馈，并保存可追溯证据。
你需要参与：采集中无需持续跟进。
```

```text
03｜证据确认【需要你确认】
我会做什么：整理保留、排除和待补充的证据。
你需要参与：回复保留 / 排除 / 补充哪些案例；确认前不生成视觉方向。
```

```text
04｜方向确认【需要你确认】
我会做什么：读取官方趋势，与已确认案例交叉分析，提出 3 个方向。
你需要参与：选择、调整或否决方向；确认后才采集视觉参考。
```

```text
05｜参考图交付
我会做什么：打开原帖详情页筛选并去重，每个已确认方向保留 10 张参考图，生成视觉参考页。
你需要参与：查看成品并提出需要替换或补充的图片。
```

请先提供项目资料；资料不全也可开始：

项目名称：<如 JOY 游记、东东农场>

玩法：<如答题、抽奖、养成或暂不确定>

如有 PRD、链接或截图，也可一并补充。
````

Do not place this guide in the final research HTML. It is the kickoff message only.

## Required Inputs

Extract from the brief, meeting notes, or PRD:

- Project background and project name
- Priority goal: acquisition, activation, conversion, sharing, retention, membership growth, or brand awareness
- Game mechanic or `暂不确定`
- Target audience
- Current problem for an existing experience
- Research openness: focused, balanced, or exploratory

Infer missing form fields only when the source supports a reasonable inference and label it as inference. Ask at most one focused question when a missing field would materially change the search.

## Browser And Source Rules

- Xiaohongshu is the primary live source for competitor cases and user feedback. Do not silently replace it with general web search or random sites.
- Use the user's logged-in browser session. Never request passwords, cookies, or tokens.
- The first live action is to open `https://www.xiaohongshu.com/` and search with its own UI.
- If login, a challenge, or blocking prevents research, stop and ask the user to complete the visible action or provide Xiaohongshu links/screenshots.
- Read [references/xiaohongshu-search-protocol.md](references/xiaohongshu-search-protocol.md) before Xiaohongshu collection and [references/evidence-rules.md](references/evidence-rules.md) before accepting evidence.
- Record only visible information. Mark unavailable values `未显示`, `不可见`, or `约`.

### Required Official Trend Sources

For every task that enters visual-direction work, directly open and read these three public pages before proposing directions:

1. [Pinterest Predicts](https://business.pinterest.com/pinterest-predicts/)
2. [Canva Design Trends](https://www.canva.com/design-trends/)
3. [Adobe Creative Trends Report](https://business.adobe.com/resources/creative-trends-report.html)

- Do not call platform APIs for trend collection. Read the visible page body from each live page, then cross-analyze its visible trend signals with the accepted Xiaohongshu visual cases.
- Give each page up to 20 seconds to load. If it fails to open in that window, record the failed source and continue using the successfully read sources; do not repeatedly retry it.
- Cite the specific page and visible trend term beside every direction it informs. Do not substitute other design systems, trend reports, or general web sources for these three required sources unless the user explicitly asks.
- Keep official-trend observations distinct from user feedback and competitor evidence.

## Stage 1: Competitor Research And User Feedback

### Query Strategy

Build two or three query families from the brand/project, mechanic, goal, audience, pain point, and phrases found in the project background.

- Focused: keep brand plus exact mechanic or problem.
- Balanced: mix branded and category-level queries.
- Exploratory: search analogous mechanics and business goals beyond the brand.

Use `综合` as the main result pool when popularity sorting harms relevance. Adapt queries using visible platform vocabulary and hashtags. Stop repeating variants that remain irrelevant.

### Inclusion And Exclusion

- Open an original post detail before counting or interpreting it.
- Prefer posts with more than 50 visible likes, comments, or other visible interactions. A lower-signal post may be retained only when it provides unique, directly relevant evidence; label that limitation.
- Exclude generic diaries, unrelated celebrity/game content, polluted keyword matches, and posts that do not concern the target interaction or a transferable analogue.
- Do not use engagement count as the sole indicator of design quality.

### Collection Volume And Competitor Fit

- Collect project-specific user-feedback cases as broadly as the available relevant evidence permits. Do not impose a small default cap such as four cases; deduplicate repeated claims and label lower-signal cases.
- Identify at most four valid competitors. Before collecting competitor evidence, state the transferable core loop and screen candidates against it.
- For each accepted competitor, search Xiaohongshu separately and retain at most five valid visual cases. A visual case must show the product experience or its interaction evidence clearly enough to support comparison.
- For idle cultivation products, accept competitors only when their loop materially includes limited input or layout, offline or autonomous character activity, and a return visit that reveals growth, visitors, collected items, or another accumulated result. Exclude products that only share surface themes, routine task completion, storefront mini-games, or cosmetic collection.

### Screenshot Collection Standard

For every accepted post, capture the live post-detail container rather than a broad full-page feed screenshot.

1. Locate the complete visible post container, preferring `.note-container`; otherwise find the nearest container owning both media and detail/comment columns.
2. Measure its live boundary immediately before each capture. Never reuse fixed crop coordinates, viewport assumptions, zoom, or DPR.
3. Verify the capture includes complete media, creator, title/body, visible date, engagement bar, and visible comments without global navigation or large empty margins.
4. If clipping is mis-scaled, capture the current viewport and crop losslessly using measured CSS-to-image scale ratios.
5. Re-measure after navigation, carousel changes, scrolling, resizing, zoom, or reflow.
6. Visually inspect every saved screenshot at readable size. Reject clipped, tiny, or contextless evidence.

Capture at minimum:

- `post-overview`: full visible post media plus creator, copy, metadata, engagement, and first comments.
- `post-media-01..NN`: every evidence-bearing carousel image or media segment.
- `comments-01..NN`: consecutive comment-pane segments with overlap, covering representative praise, objections, questions, high-engagement comments, and the end marker when reachable.

Use stable names such as `E02_post_<short-title>_overview.png`, `E02_post_<short-title>_media-01.png`, and `E02_comments_<short-title>_01.png`. An item is incomplete if it omits relevant media or cannot attribute comments to the post.

For every accepted competitor, add at least one embedded screenshot preview in the candidate document or report, with the product name as its heading. The preview must be a saved evidence image, not only a text link.

### Source-Link Fallback

- Prefer an original Xiaohongshu post URL when it opens reliably.
- When an original-post URL is blocked or cannot be opened because of platform access controls, replace it with the Xiaohongshu search-result URL that contains the post.
- In the evidence card, preserve the post title, visible account, date, metrics, and screenshot alongside the fallback link so the post remains traceable. Label the URL as `小红书搜索页` or equivalent; do not present it as a direct original-post URL.

### Analysis Dimensions

Use these four dimensions as the primary report structure:

1. `达成的业务目标`: visible acquisition, activation, membership, conversion, sharing, or brand path.
2. `游戏玩法模式`: rule clarity, entry threshold, core loop, repetition, rounds, levels, lottery, quiz, collection, or synthesis.
3. `用户牵引及留存机制`: tasks, progress, check-ins, rankings, teams, collection, reward cadence, and return triggers.
4. `内容叙事与情绪价值`: characters, story, seasonal or brand context, emotional vocabulary, and resonance.

Supporting observations may cover entry hooks, liked experiences, churn causes, incentives, social spread, conversion paths, and opportunities, but they must not replace the four primary dimensions.

### Evidence Cards And Confirmation

Assign stable evidence IDs. Each candidate card records type, screenshots and absolute paths, source link (or search-result fallback), title, visible account/date/metrics, visible text or short quote, covered dimensions, neutral observation, interpretation, and limitation.

Present candidate evidence grouped by the four dimensions and flag coverage gaps. Ask the designer what to retain, exclude, or research further. Do not finalize conclusions before confirmation unless the user explicitly waives review. During evidence collection and candidate review, do not generate visual directions.

### First HTML Output

After confirmation, create `competitor-research-<project-slug>.html`. It contains:

- Project brief and research scope
- Exactly four core conclusion cards in a 2x2 grid, each with one or two supporting screenshots
- Competitor cases and real user feedback as distinct evidence types
- A four-row analysis matrix using the required dimensions
- For every row: title, key points, short visible evidence quotes, design implication, and adjacent evidence screenshots
- Source links, visible dates, limitations, and audit metadata

Do not include visual directions in the first HTML unless the user has explicitly asked to enter visual-direction work after reviewing the evidence. When requested, produce exactly three provisional visual directions tied to evidence, risks, and interaction-carrier implications.

Use responsive visual HTML, not a Markdown report. Images keep their natural ratio with `height:auto`; avoid fixed-height gray letterboxing. Evidence IDs may remain in metadata and filenames, but visible conclusions should be supported by adjacent screenshots and source titles rather than opaque ID shorthand.

Stop after delivering the first HTML and ask the user to approve the evidence conclusions or request further collection. Enter visual-direction work only when the user explicitly requests it.

## Stage 2: Visual Reference Collection

Begin only after the user has explicitly requested and approved direction work. Use Behance, Pinterest, and ZCOOL by default. Enter each platform directly, open original detail pages, and never count a search-result thumbnail as a reviewed sample.

For each of the three approved directions:

1. Generate short visual terms from perception, material, composition, motion, interface, and mechanic implications.
2. Target 40 opened detail pages per platform across the approved directions. Author information is optional; preserve publication date and original link.
3. Score direction relevance, visible visual quality, interaction transfer value, source confidence, and distinctness.
4. Reject images whose visible content cannot support the direction or whose caption would require guessing.
5. Remove duplicates and near-duplicates; keep the stronger and more relevant candidate.
6. Select exactly 10 qualified references when available: 5 `灵感参考` and 5 `执行参考`.

For every approved direction, collect 10 references before delivering the visual-reference board. Reduce the count only after a documented search shows fewer than 10 qualified, non-duplicative cases. Never pad the board with weak matches.

- Deduplicate visually similar results before selection. When two samples have substantially the same composition, subject, visual language, or interaction expression, retain only the one with the stronger directional relevance and clearer source evidence.
- Each reference card displays only the image, source platform or source link, and visible publication date. Do not add title, creator, interpretation, selection reason, or explanatory body text below individual images.
- A reference image must be the original visual asset or a tight crop of the actual visual content. Do not use a browser-window screenshot, page chrome, search-result tile, or other UI surrounding the source image as the reference image.
- Create and maintain one project-level `design.md` before generating any HTML. Every HTML output for that project must use this file as its visual specification. The default specification is concise, white-background, content-first, with no decorative card copy unless the user changes it.
- For visual-reference HTML, use a project-summary card followed by one separate, clearly headed direction card per direction. Each direction card uses a compact 5-column, 2-row image-card grid for its 10 references.

`灵感参考` transfers color, material, composition, form, atmosphere, or motion. `执行参考` shows game UI, campaign flow, rewards, feedback states, progression, or another directly transferable digital execution.

### Second HTML Output

Create `moodboard-<project-slug>.html` containing only the approved three directions and their visual evidence:

- Direction name, rationale, visual principles, and interaction implication
- A stable 5-column by 2-row grid per direction
- Complete uncropped images, source platform, visible date, original link, reference role, and concise selection reason
- A limitations/footer section with platform review counts, failed URLs or access constraints, copyright/reuse notice, and degraded-result notes

Do not repeat the full competitor report in this file.

## Degradation And Quality Gate

- Use bounded navigation and analysis timeouts. On timeout, record the URL and continue; do not repeatedly retry the same page.
- If one visual platform reviews fewer than 40 details, continue with qualified evidence from other platforms and disclose the exact count and reason.
- If a direction has fewer than 10 qualified references, deliver the smaller set rather than padding with irrelevant or duplicate images.
- Fail Stage 2 only when all visual platforms yield zero usable samples. Authentication requirements must be surfaced for user action.
- Verify both HTML files at desktop and mobile widths. No broken images, clipping, overlapping text, unreadable screenshots, or captions that contradict images.
- References are generally copyrighted. Use them for research, study, internal alignment, or local archival unless broader rights are granted.

