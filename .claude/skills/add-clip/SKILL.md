---
name: add-clip
description: Add one of Ellie's published stories to the Clips section of index.html from a link, then push. Use when Ellie runs /add-clip <url> or asks to add a story or clip to her site.
argument-hint: <story URL>
---

# Add a clip

Ellie gives a link to one of her published stories. Add it to the Clips section of `index.html`, push, and report back.

## 1. Get the story details from the link

Open the URL that came with the command (`$ARGUMENTS`). Use WebFetch if you have it, or the `web-fetch` agent otherwise. Ask it for these exact values and tell it not to paraphrase them:

- **Headline**: the article's headline exactly as published, taken from the page's main `<h1>` headline. If you can't find an `<h1>`, use `og:title` or the JSON-LD `headline`. Don't use the `<title>` tag when another source exists, because it often has "| Outlet Name" tacked on.
- **Outlet**: the publication's name, taken from `og:site_name`, the JSON-LD `publisher.name` or the masthead, for example "The Washington Sun".
- **Date**: the original publication date, taken from `article:published_time`, the JSON-LD `datePublished` or the dateline. Never use the "updated" date.

Rules:
- **Never rewrite, shorten, retitle, re-case or "fix" the headline.** Keep its exact words, capitalization, punctuation and curly quotes. The only allowed change is HTML-escaping (`&` → `&amp;`, `<` → `&lt;`) so the page stays valid.
- **If you can't open the link** (paywall, error, blocked, login page), or you can't find one of the three values with confidence, **stop and ask Ellie** for the headline, outlet and date. Don't guess, and don't fill in anything from the URL slug or from memory.
- If two sources on the page give different headlines (for example the `<h1>` and `og:title`), use the `<h1>`. Mention the other version when you report back.
- If the URL is already in the Clips list, don't add it again. Tell Ellie it's already there.

## 2. Add it to `index.html`

Clips live in `<ul class="clip-list">` inside `<section id="clips">`. Each clip is a list item in this exact format, indented to match the file:

```html
        <li>
          <span class="outlet">OUTLET</span>
          <a href="URL">HEADLINE</a>
          <time datetime="YYYY-MM-DD">DISPLAY DATE</time>
        </li>
```

- Write `DISPLAY DATE` in AP style, abbreviating the month where AP does: Jan., Feb., Aug., Sept., Oct., Nov. and Dec. March, April, May, June and July are spelled out. Examples: "Nov. 20, 2026" and "March 3, 2026".
- Keep the list **newest first**. A new story normally goes at the top. If it's older than clips already in the list, put it where its date belongs.
- If `<ul class="clip-list"></ul>` is still empty, open it onto separate lines and **delete** the line `<p class="placeholder">Stories will be added here soon.</p>`.
- Don't change anything else on the page. Follow the style guide in `CLAUDE.md`.

Check the result by loading the page in Playwright (Chromium is pre-installed) and confirming the clip shows up first and the page has no horizontal scroll at 390px wide. Save any screenshots to the scratchpad, never into the repository.

## 3. Push

Commit only `index.html`, with a message like `Add clip: <first few words of headline>`, and push to the current branch with `git push`. Retry network failures up to 4 times with backoff. Follow the repository's git rules from the session: don't push to other branches and don't open a pull request unless Ellie asks.

## 4. Report back

Tell Ellie in a short message:
- The headline exactly as added, the outlet and the display date.
- Where it landed in the list ("at the top", or its position if older).
- That the change is pushed, and to which branch. If the site's hosting serves a different branch, say the change isn't live until it's merged there.
- Any discrepancy you noticed, such as a different `og:title` or no visible publish date.
