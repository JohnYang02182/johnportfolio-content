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

### 概要

最初は、portfolio article をすべて Google Sheets で管理していた。

この方法は、データ量が少なく、内容が単純な段階では便利だった。しかし、portfolio の内容が増え、多言語対応のメンテナンスも必要になると、Google Sheets での管理はすぐに直感的ではなくなった。

以前の `projectDetail` のコンテンツ管理フローは以下の通りだった。

```text
Google Sheets に内容を追加する
=> プロジェクト側で Google Sheets API を呼び出し、多言語の `.json` ファイルを取得する
=> 新しい view page を追加し、style を調整して内容を表示する
```

::: div {.content-wrapper}

### 問題点

1. 内容を追加するたびに新しい view page を追加する必要があり、style の調整も必要だった。
2. Google Sheets は記事編集ツールとして適しておらず、Markdown の Preview もできなかった。
3. 内容の調整プロセスが複雑だった。多言語を維持するために、記事を複数の `KeyName` に分割して管理する必要があった。

### 要件

* CMS 上で作品集の記事本文を追加・編集できること。
* CMS 上で `projectList` と `projectDetail` の内容を編集・追加・削除できること。
* CMS にバージョン履歴があること。
* コンテンツ形式では Article と Metadata を分離すること。

### 解決方法

#### Cloudflare-based content flow へ変更

* Cloudflare Pages Functions で `/api/projects` を提供する。
* API 側で project list を整理する。
* フロントエンドは整理済みの JSON だけを扱う。
* detail page は slug に応じて対応する記事を読み込む。
* metadata は記事の一部として扱う。たとえば `title`、`period`、`tags`、`bannerImg` などを以下のように定義する。

```yaml
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

#### フロントエンド開発

* CMS fetch API handler を追加する。
* Pagination Components を追加する。
* Route が static project と CMS project を管理できる View を追加する。

### 成果

* metadata と content を同じ場所で管理できるため、データを保守しやすくなった。
* データは GitHub の content repo に保存されるため、すべての変更履歴を追跡できる。
* 将来的に Cloudflare KV / R2 / D1 と連携できる。
