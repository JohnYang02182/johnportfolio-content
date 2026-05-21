---
name: Build a CMS service
bannerImg: /uploads/CMS_banner.png
title: ポートフォリオのCMSを作ろう
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

## 説明

現在の projectDetail のコンテンツ管理は、

Google Sheets にコンテンツを追加 ⇒ プロジェクト側で Google Sheets API を呼び出して多言語対応の .json ファイルを取得 ⇒ 新しい view page を追加し、`${key.name}` の形式でコンテンツを表示する、という流れになっています。

#### 課題:

- コンテンツを追加するたびに、新しい view page を追加する必要があり、style も調整する必要があります。
- Google Sheets は記事を追加するためのエディターとしては適していません。

# Functional Requirements

- CMS で .md 形式を使用して、ポートフォリオ本文のコンテンツを追加／編集できること。
- CMS で日本語、英語、繁体字中国語の3言語のポートフォリオコンテンツを保存できること。
- RESTful API を使用してデータをフロントエンドへ送信すること。
- CMS で projectList と projectDetial の内容を編集／追加できること。

#### API Format

```plain
/// 各 Project Header の情報
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
/// フロントエンドの Project List の形式
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

# 制約

- 開発者（私）はバックエンド開発者ではないため、複雑すぎるもの、大規模なもの、または深いバックエンド知識を必要とするツールや開発作業は実行できません。
- 3日以内に完了する必要があります。
- 既存サービスの利用を積極的に検討しますが、有料サービスは対象外とします。

# フロー

- [x] 使用するサービスまたは開発手段を選定する
    - [x] 一時的に Decap CMS を採用し、将来的には CMS を Directus（Docker）へ移行する
- [ ] 開発手順を選定する
    - [x] 新しい repo “portfolio-content” を作成する
    - [ ] Decap CMS Sveltia CMS を設定する
    - [ ] GitHub で OAuth App を作成する
`GitHub → Settings → Developer settings → OAuth Apps → New OAuth App` へ移動する欄位填入Application namejohnresume2023Homepage URL`https://あなたのサイトURL`Authorization callback URL`https://あなたのサイトURL/admin`**Client ID** と **Client Secret** を取得する
- [ ] 実装
- [ ] Unit Test と E2E Test
- [ ] Release
