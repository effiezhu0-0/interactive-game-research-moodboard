# Xiaohongshu Search Protocol

Use this protocol whenever the skill needs to search inside Xiaohongshu.

## Why Search Can Fail

Xiaohongshu is a dynamic single-page app. The search field may be rendered after hydration, wrapped in custom components, covered by login/modals, or exposed differently to DOM and vision tools. A visible search box does not always mean a normal `input` is immediately focusable.

## Interaction Rules

- Keep low-level retries internal. Do not tell the user about every failed click, selector, or coordinate attempt.
- Before clicking search, confirm the page is loaded enough to show the header/search area.
- If login, verification, cookie, or modal UI blocks the page, stop and ask the user to resolve it.
- After input, verify success by checking whether the query text appears in the search box, the URL/state changes, or search results visibly update.
- If all automated attempts fail, ask the user to click the search box manually once, then continue typing and collecting evidence.

## Post Detail Capture Protocol

1. Open the selected post detail and wait until both the left media column and right detail/comment column are visible.
2. Identify the visible bounds of the post detail overlay/card. Capture that region only; exclude the global navigation and unrelated feed.
3. Save an overview containing the complete visible media frame plus creator, title/body, publish metadata, metrics, comment count, and first comments.
4. If the post is a carousel, traverse every relevant image and save each image/page before comment scrolling.
5. Scroll the right comment pane, not the whole webpage. Save sequential screenshots with 15-25% vertical overlap so reviewers can verify continuity.
6. Continue until representative high-engagement comments and all comments used in analysis are captured. Capture the end marker when reachable; if pagination, collapsing, or loading prevents completion, label the evidence `评论未完全加载` and state the visible stopping point.
7. Review every saved image at normal size. Reject and recapture images where the post or comments are unreadable, cropped, hidden by overlays, or reduced to a narrow strip.

Do not use `fullPage: true` as the default for post details. It is acceptable for search-result evidence, but post details require overlay clipping and sequential comment-pane captures.

## Preferred Search Sequence

1. Open `https://www.xiaohongshu.com/`.
2. Wait for visible page content, not just the document title.
3. Dismiss only obvious non-auth blocking overlays if they have visible close buttons. Do not bypass login or verification.
4. Try semantic locators first:
   - search box role
   - placeholder containing `搜索`
   - visible input near the page header
   - contenteditable search area
5. If semantic locators fail, use DOM inspection to find visible text/input nodes in the header area.
6. If DOM targeting fails but the search box is visibly on screen, use a vision/coordinate click at the center of the visible search field.
7. After focus, clear existing text, type the keyword, and press Enter.
8. Wait for result content to update.
9. Capture the search results screenshot and record the keyword.

## Fallback Policy

Use at most three automated focus attempts:

- Attempt 1: semantic locator
- Attempt 2: DOM/header locator
- Attempt 3: visual coordinate click

If none works, stop and say:

`我看到小红书搜索框，但自动聚焦失败。请你在浏览器里点一下搜索框，点好后告诉我，我会继续输入关键词并采集结果。`

Do not switch to generic web search.
