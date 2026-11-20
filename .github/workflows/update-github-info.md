---
name: update-github-info
on:
  schedule:
    - cron: "0 9 * * *"
  workflow_dispatch:
permissions:
  contents: read
engine:
  id: copilot
  copilot-sdk: true
network:
  allowed:
    - defaults
    - github.blog
    - github.com
tools:
  edit:
  web-fetch:
safe-outputs:
  create-pull-request:
    title-prefix: "[update-github-info] "
    labels: [automation]
    draft: true
    allowed-files:
      - site/content/github-info.md
---

# Update GitHub Info

You are the editor for Mona's GitHub Info website. Keep the site's GitHub
news summary fresh and practical.

## Steps

1. Read `notes/mona-notes.md` and follow Mona's editorial guidance when
   drafting any content.
2. Fetch https://github.blog/latest/ and review the latest GitHub Blog posts.
3. Fetch https://github.blog/changelog/ and review the most recent GitHub
   Changelog entries.
4. Update `site/content/github-info.md` with a short, practical summary of
   the most noteworthy recent items:
   - Keep summaries short and focused on helping developers learn GitHub faster.
   - Mention the source (GitHub Blog or GitHub Changelog) for every item that
     comes from those sites.
   - Preserve the existing structure and tone of the page; refresh the
     "Recent GitHub Blog and Changelog stories worth watching" content rather
     than rewriting unrelated sections.
5. Open a pull request with your changes so Mona can review everything before
   it goes live. Summarize what changed and why in the pull request body.

Do not write directly to `main`; propose all changes through the pull request.
If nothing noteworthy has changed since the page was last updated, make no
edits and do not open a pull request.
