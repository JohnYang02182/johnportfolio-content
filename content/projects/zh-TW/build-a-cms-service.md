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

現在的 projectDetail 內容管理是
[:.text-primary]
在 Google Sheets 新增內容 ⇒ 在專案呼叫透過 Google Sheets API 取得多語系的 .json 檔案 ⇒ 新增一個 view page 用 ${[key.name](http://key.name)} 的方式將內容顯示。

::: div {.content-wrapper}

### 痛點:

1. 每新增一次內容就會需要新增 view page，style 也需要調整。
2. Google Sheets 不適合用來當作新增文章的編輯器。
3. 調整內容過程複雜
:::

# 需求

### Functional Requirements

- 在 CMS 必須能夠新增/編輯作品集內文內容。
- 在 CMS 必須能夠編輯/新增/刪除 projectList 與 projectDetial 的內容。
- CMS 必須有版本紀錄

### Nonfunctional Requirements

- 必須提供自動化 CICD ，部屬失敗率不能超過 90%
- 必須能夠檢視平台的 Log
- 必須切分 Preview 環境與 Product 環境
- 內容格式必須是 Markdown 格式，結構含有 Metadata、Content

#### API Format

```plain
/// 每個 Project Header 的資訊
export const profolioDetail = [{
  params: '1',
  period: '202008~202101',
  bannerImg: '',
  contentImg: '',
  article: [
    {'title': 'ProjectDetail.Title','content': 'ProjectDetail.content'},
    {'title': 'ProjectDetail.Title','content': 'ProjectDetail.content'},
    {'title': 'ProjectDetail.Title','content': 'ProjectDetail.content'},
  ],
  character: 'UI/UX designer',
  tags: ['Skill.WebDesign','Skill.RWD','Skill.HTML5','Skill.SCSS','Skill.jQuery','Skill.JavaScript'],
  isSideProject: false
}]
```

```markdown
/// 前端 Project List 的格式
export interface CardInfoDetail {
  name: string
  bannerImg: string
  title: string
  link?: string
  team: string
  period: string
  character: string
  tags: string[]
  sideProject: boolean
}
export const designCardInfo: CardInfoDetail[] = [
  {
    name: 'ECWebsite',
    bannerImg: 'pic_vue.png',
    title: 'HomeProfolio.ShinchiECLayout',
    link: '',
    team: 'Team.ShinchiDevelope',
    character: 'Character.FEDeveloper',
    period: '2022',
    tags: ['Skill.UIAndUX', 'Skill.TypeScript', 'Skill.JavaScript', 'Skill.Vue3', 'Skill.Vite', 'Skill.UNOCSS'],
    sideProject: false
  }
]
```

# 限制

- 開發者(我)並非後端開發人員，太過複雜、規模龐大、需要深度後端知識的工具或開發工程無法執行。
- 需要在 3 天內完成。
- 積極考慮的使用現成已有的服務，但不考慮付費。

# 流程

- [x] 選定使用服務或是開發手段
    - [x] 暫時選用 Decap CMS，未來將 CMS 轉移至 Directus(Docker)
- [ ] 選定開發步驟
    - [x] 新開 repo “portfolio-content”
    - [x] 設定 ~~Decap CMS~~ Sveltia CMS
    - [x] 在 GitHub 建立 OAuth App
    - [x] 設定 Netlify 存取權限
- [ ] 執行
- [ ] Unit Test 與 E2E Test
- [ ] Release
