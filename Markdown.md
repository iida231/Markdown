<!-- TOC -->

- [1. Markdownの書き方について](#1-markdown%E3%81%AE%E6%9B%B8%E3%81%8D%E6%96%B9%E3%81%AB%E3%81%A4%E3%81%84%E3%81%A6)
    - [1.1. Markdownとは](#11-markdown%E3%81%A8%E3%81%AF)
    - [1.2. 目的](#12-%E7%9B%AE%E7%9A%84)
    - [1.3. 事前準備](#13-%E4%BA%8B%E5%89%8D%E6%BA%96%E5%82%99)
    - [1.4. MarkDownの基本的な記述方法](#14-markdown%E3%81%AE%E5%9F%BA%E6%9C%AC%E7%9A%84%E3%81%AA%E8%A8%98%E8%BF%B0%E6%96%B9%E6%B3%95)
    - [1.5. plantUMLについて](#15-plantuml%E3%81%AB%E3%81%A4%E3%81%84%E3%81%A6)
        - [1.5.1. コンポーネント図](#151-%E3%82%B3%E3%83%B3%E3%83%9D%E3%83%BC%E3%83%8D%E3%83%B3%E3%83%88%E5%9B%B3)
        - [1.5.2. アーキテクチャ図](#152-%E3%82%A2%E3%83%BC%E3%82%AD%E3%83%86%E3%82%AF%E3%83%81%E3%83%A3%E5%9B%B3)
        - [1.5.3. ユースケース](#153-%E3%83%A6%E3%83%BC%E3%82%B9%E3%82%B1%E3%83%BC%E3%82%B9)
    - [1.6. シーケンス図](#16-%E3%82%B7%E3%83%BC%E3%82%B1%E3%83%B3%E3%82%B9%E5%9B%B3)

<!-- /TOC -->

# 1. Markdownの書き方について

## 1.1. Markdownとは

簡単に文章作成ができるツールである

## 1.2. 目的

- Markdownの書き方のチートシートを作成し、今後の業務効率を向上させる
- 将来的なブログ作成に向けての原本を作成する

## 1.3. 事前準備

- vscodeをinstall
- TOCを生成する際のバグを回避するために以下の動作を行う
  - 設定を開く
  - Eolを検索しauto→/nと変更する
  ![](images/2021-07-25-11-26-13.png)

- おすすめ拡張機能
  - 入れ方
  以下の部分から検索してインストールする

  ![](images/2021-07-25-11-32-32.png)
  
|アプリ名|機能|
|---|---|
|Auto Markdown TOC|右クリックを押すと章番号や目次を入れることができる|
|Markdown All in one|便利機能盛沢山|
|Markdown Paste|画像を挿入できる|
|Paste Images|画像を挿入できる|
|Markdown PDF|マークダウンをPDFに変更できる|
|Zenkaku|全角のスペースを見やすくする|
|PlantUML|UMLを作成できる|
|Markdownlist|HTMLの記述用語が使える|
|Markdown Preview Enhanced|Markdownの結果が見れる|
|Githistory|gitの更新履歴を確認できる|

補足：Auto Markdown TOC を有効にするには
設定で以下の項目にチェックをつける
![](images/2021-07-25-12-03-22.png)

## 1.4. MarkDownの基本的な記述方法

||記述方法|出力例|
|---|---|---|
|太字|`**a**`|**a**|
|イタリック|`***a***`|***a***|
|見出し|# 見出し||
|リンク1|`[リンク](a.jp)`|[リンク](a.jp)|
|リンク2|`<http://example.com>`|<http://example.com>|
|リンク3|`http://example.com`|http://example.com|
|画像|`![](example.jpeg)`||
|引用|>||
|箇条書き|- example||
|箇条書き（番号付き）|1. ||
|水平線|---||
|code|``|`a`|
|codeブロック|||
|表|||
|チェックボタン|- [ ] example or - [x] example||
|打消し|`~~example~~`|~~example~~|
|絵文字|`:smile: :heart: :+1:`|:smile::heart::+1:|

## 1.5. plantUMLについて

### 1.5.1. コンポーネント図

>'```plantuml
>scale 400 width
>package "adapter" #gainboro{
>    [sample.dll]
>}
>
>package "ライブラリ"{
>  frame "sampleライブラリ"{
>    [sample1.dll]
>  }
>
>  frame "sample2ライブラリ"{
>    [sample2.dll]
>  }
>}
>
>[sample.dll] -down-> [sample1.dll]
>[sample1.dll]-left->[sample2.dll]
>@enduml
>'```

```plantuml
' 上記がないとgithubで表示できない
scale 400 width
' 大きさを規定
package "adapter" #gainsboro{
    [sample.dll]
}

package "ライブラリ"{
  frame "sampleライブラリ"{
    [sample1.dll]
  }

  frame "sample2ライブラリ"{
    [sample2.dll]
  }
}

[sample.dll] -down-> [sample1.dll]
[sample1.dll]-left->[sample2.dll]
@enduml
```

### 1.5.2. アーキテクチャ図

>'```plantuml
>!define samplecircle circle #black
>
>samplecircle start
>
>archimate #Technology "クライアント" as client >`<<technology-device>>`
>
>database "サーバー" as server
>
>client -up-> start
>client -left->server:リクエスト
>client<-right-server:レスポンス
>
>@enduml
>'```

```plantuml
!define samplecircle circle #black

samplecircle start

archimate #Technology "クライアント" as client <<technology-device>>

database "サーバー" as server

client -up-> start
client -left->server:リクエスト
client<-right-server:レスポンス

@enduml
```

### 1.5.3. ユースケース

>``plantuml
>left to right direction
>
>actor "service"  as Adapter  
>rectangle Query{
>  usecase "検索する"  as indexQuery
>} 
>Adapter --> indexQuery
>@enduml
>``

```plantuml
left to right direction 

actor "service"  as Adapter  
rectangle Query{
  usecase "検索する"  as indexQuery
} 
Adapter --> indexQuery
@enduml
```

## 1.6. シーケンス図

>'```plantuml
>actor service
>participant Query
>database data
>
>service -> Query:サンプル
>
>@enduml
>'```

```plantuml
actor service
participant Query
database data

service -> Query:サンプル

@enduml
```
