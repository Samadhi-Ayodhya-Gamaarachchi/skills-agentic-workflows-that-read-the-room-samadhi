---
name: update-github-info
description: Draft concise GitHub Info updates for Mona from official GitHub sources.
on:
  workflow_dispatch:
  schedule:
    - cron: '17 9 * * *'
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
tools:
  edit:
  web-fetch:
network:
  allowed:
    - defaults
    - github.com
    - github.blog
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before making any changes.

Use these sources:
- `notes/mona-notes.md`
- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/

Update `site/content/github-info.md` with concise, practical updates for readers.
When content comes from the GitHub Blog or GitHub Changelog, mention the source
clearly in the update.

Open a pull request for Mona to review using `safe-outputs` with
`create-pull-request`. Do not write directly to `main`.

If the sources do not justify a website update, call `noop` with a short reason
instead of making a change.

## Safe Outputs

- Use `create-pull-request` for all visible write actions.
- Keep the pull request focused on the site content update.