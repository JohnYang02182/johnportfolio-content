---
name: Build a CMS service
bannerImg: /uploads/CMS_banner.png
title: Build a CMS service
link: ''
team: Me
period: '202605'
character: Front-end Engineer
tags:
  - ''
  - ''
  - ''
  - ''
sideProject: true
---

# Description

The current projectDetail content management flow is:

Add content in Google Sheets ⇒ The project calls the Google Sheets API to retrieve multilingual .json files ⇒ Add a new view page and display the content using `${key.name}`.

#### Pain Points:

- A new view page needs to be added every time new content is added, and the style also needs to be adjusted.
- Google Sheets is not suitable as an editor for adding articles.

# Functional Requirements

- The CMS shall allow portfolio body content to be added and edited in .md format.
- The CMS shall be able to store portfolio content in three languages: Japanese, English, and Traditional Chinese.
- Data shall be sent to the front end through a RESTful API.
- The CMS shall allow editing and adding content for projectList and projectDetial.

#### API Format

```plain
/// Information for each Project Header
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

```plain
/// Format of the front-end Project List
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
    // params: 'https://www.behance.net/gallery/125095859/_',
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

# Constraints

- The developer, myself, is not a back-end developer, so tools or development tasks that are too complex, large-scale, or require deep back-end knowledge cannot be implemented.
- The task must be completed within 3 days.
- Existing services will be actively considered, but paid services will not be considered.

# Flow

- [x] Select the service or development approach to use
    - [x] Temporarily use Decap CMS, and migrate the CMS to Directus (Docker) in the future
- [ ] Select the development steps
    - [x] Create a new repo named “portfolio-content”
    - [ ] Configure Decap CMS Sveltia CMS
    - [ ] Create an OAuth App on GitHub
Go to `GitHub → Settings → Developer settings → OAuth Apps → New OAuth App`FieldValueApplication namejohnresume2023Homepage URL`https://your-website-url`Authorization callback URL`https://your-website-url/admin`Obtain the **Client ID** and **Client Secret**
- [ ] Implementation
- [ ] Unit Test and E2E Test
- [ ] Release
