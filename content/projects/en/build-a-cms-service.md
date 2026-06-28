---
name: Build a CMS service
bannerImg: /uploads/CMS_banner.png
title: 架設 Portfolio CMS
link: ''
team: Me
period: '202605'
character: Front-end Engineer
tags:
  - Git
  - Vue3
  - TypeScript
  - Markdown
sideProject: true
---

### Description

At the beginning, portfolio articles were managed entirely through Google Sheets.

This approach was convenient when the amount of data was small and the content was simple. However, as the portfolio content increased and multilingual maintenance became necessary, Google Sheets quickly became unintuitive.

The previous `projectDetail` content management flow was:

```plain
Add content in Google Sheets
=> Fetch multilingual `.json` files through the Google Sheets API in the project
=> Add a new view page and adjust the styles to display the content
```
::: div {.content-wrapper}

### Problems

1. Every time new content was added, a new view page also had to be created, and the styles had to be adjusted.
2. Google Sheets is not suitable as an article editor and cannot preview Markdown.
3. The content editing process was complicated. To maintain multilingual content, articles had to be split into multiple `KeyName` entries.

### Requirements

- The CMS must allow adding and editing portfolio article content.
- The CMS must allow editing, adding, and deleting `projectList` and `projectDetail` content.
- The CMS must provide version history.
- The content format must separate Article and Metadata.

### Solution

#### Switch to a Cloudflare-based content flow

- Use Cloudflare Pages Functions to provide `/api/projects`.
- Let the API organize the project list.
- The frontend only consumes clean JSON.
- The detail page reads the corresponding article based on the slug.
- Metadata becomes part of the article, such as `title`, `period`, `tags`, and `bannerImg`, as shown below:

```plain
---
name: build-a-cms-service
title: Build a CMS Service
bannerImg: /uploads/banner.png
period: 2026
character: Frontend Developer
tags:
  - Vue
  - Cloudflare
  - CMS
sideProject: true
---

```

#### Frontend Development

- Add a CMS fetch API handler.
- Add Pagination Components.
- Add a View that lets the Route manage both static projects and CMS projects.

### Results

- Metadata and content are stored together, making the data easier to maintain.
- Data is stored in GitHub, and the content repo can track every modification.
- Cloudflare KV / R2 / D1 can be integrated in the future.
