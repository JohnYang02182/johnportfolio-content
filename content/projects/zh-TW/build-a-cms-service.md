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

# 描述

一開始 portfolio article 統一透過 Google Sheets 管理。
這個方式在資料量少、內容單純時很方便，但當 portfolio 內容開始變多且要顧及多語系的維護時，Google Sheets 很快就變得很不直覺。

過去的 projectDetail 內容管理是
```
在 Google Sheets 新增內容 
⇒ 在專案呼叫透過 Google Sheets API 取得多語系的 .json 檔案 
⇒ 新增一個 view page 調整 Style 將內容顯示。
```

::: div {.content-wrapper}

### 問題:

1. 每新增一次內容就會需要新增 view page，style 也需要調整。
2. Google Sheets 不適合用來當作文章編輯器，也無法 Preview Markdown。
3. 調整內容過程複雜，為了維護多語系，要將文章拆成好幾個 KeyName 維護。

### 需求

- 在 CMS 必須能夠新增/編輯作品集內文內容。
- 在 CMS 必須能夠編輯/新增/刪除 projectList 與 projectDetial 的內容。
- CMS 必須有版本紀錄
- 內容格式必須將 Article 與 Metadata 分離

### 解決方法

#### 改成 Cloudflare-based content flow

- 用 Cloudflare Pages Functions 提供 /api/projects
- 由 API 負責整理 project list
- 前端只吃乾淨的 JSON
- detail page 依 slug 讀取對應文章
- metadata 變成文章的一部分，例如 title、period、tags、bannerImg，像是以下：

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

#### 前端開發

- 新增 CMS fetch API handler
- 新增 Pagination Components
- 新增 View 讓 Route 管理 static project 與 CMS project

### 成果

- metadata 和 content 放在一起，使資料更容易維護
- 資料存放在 GitHub - content repo 可以追蹤每一次修改
- 未來可接 Cloudflare KV / R2 / D1
