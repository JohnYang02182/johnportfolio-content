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

#### 痛點:

1. 每新增一次內容就會需要新增 view page，style 也需要調整。
2. Google Sheets 不適合用來當作新增文章的編輯器。
3. 調整內容過程複雜

# Functional Requirements

- 在 CMS 可以使用 .md 格式新增/編輯作品集內文內容。
- 在 CMS 需要能夠儲存有日文、英文、繁體中文3語系的作品集內容。
- 使用 RESTful API 將資料送到前端。
- 在 CMS 能夠編輯/新增 projectList 與 projectDetial 的內容。

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
    name: 'BahaWorld',
    bannerImg: 'braver_banner.png',
    title: 'HomeProfolio.BahaWallTitle',
    link: '',
    team: 'Team.BahamutProduce',
    character: 'Character.UIUXDesigner',
    period: '2019',
    tags: ['Skill.UIAndUX', 'Skill.Sketch', 'Skill.iOS', 'Skill.Andriod', 'Skill.AI', 'Skill.PS'],
    sideProject: false
  },{ 
    name: 'BahaECShop',
    bannerImg: 'shopping_banner.png',
    title: 'HomeProfolio.BShoppingMallTitle',
    link: '',
    team: 'Team.BahamutEC',
    period: '2020',
    character: 'Character.UIUXDesigner',
    tags: ['Skill.WebDesign', 'Skill.RWD', 'Skill.HTML5', 'Skill.SCSS', 'Skill.jQuery'],
    sideProject: false
  },{
    // params: '<https://www.behance.net/gallery/125095859/_>',
    name: 'AnimeDetail',
    bannerImg: 'anime_banner.png',
    title: 'HomeProfolio.AnimePlateFormTitle',
    link: '',
    team: 'Team.BahamutAnime',
    period: '2021',
    character: 'Character.UIUXDesigner',
    tags: ['Skill.WebDesign', 'Skill.RWD', 'Skill.HTML5', 'Skill.SCSS', 'Skill.jQuery', 'Skill.JavaScript'],
    sideProject: false
  }, {
    name: 'ECWebsite',
    bannerImg: 'pic_vue.png',
    title: 'HomeProfolio.ShinchiECLayout',
    link: '',
    team: 'Team.ShinchiDevelope',
    character: 'Character.FEDeveloper',
    period: '2022',
    tags: ['Skill.UIAndUX', 'Skill.TypeScript', 'Skill.JavaScript', 'Skill.Vue3', 'Skill.Vite', 'Skill.UNOCSS'],
    sideProject: false
  }, {
    name: 'FortuneSeeking',
    bannerImg: 'foutune_cardbackground.png',
    title: 'HomeProfolio.FortuneSeeking',
    link: '',
    team: 'Team.Myself',
    character: 'Character.FEDeveloper',
    period: '2023',
    tags: ['Skill.TypeScript', 'Skill.JavaScript', 'Skill.Vue3', 'Skill.Vite', 'Skill.AI', 'Skill.PS'],
    sideProject: true
  }
].reverse()
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
    - [ ] 設定 ~~Decap CMS~~ Sveltia CMS
    - [ ] 在 GitHub 建立 OAuth App
前往 `GitHub → Settings → Developer settings → OAuth Apps → New OAuth App`欄位填入Application namejohnresume2023Homepage URL`https://你的網站網址`Authorization callback URL`https://你的網站網址/admin`取得 **Client ID** 和 **Client Secret**
- [ ] 執行
- [ ] Unit Test 與 E2E Test
- [ ] Release
