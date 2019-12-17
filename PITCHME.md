## Auth0 in Microservices

### ～リーガルテックの事績～

@snap[south]
GVA TECH 太田
@snapend

---

### リーガルテック？

---

法律関連のレガシー・労働集約型の領域を
<br/>
テクノロジーで代替していく

---

#### 特に法務はレガシー

+++

- 契約による法的拘束力は恐ろしい
- 契約書は十分なチェックが必要 |
- 多大な労力と時間がかかる |

+++

- 権利義務関係の明確化
- リスクコントロール |
    - 競業禁止規定 |
    - 任意解除規定 |
    - 賠償額と条件 |
    - etc |

+++

## これら全てを<br/>**目視チェック**

+++

## 知識・スキルの属人化

+++

法律は全ての人に等しく適用される
<br/>
@fa[arrows-alt-v]
<br/>
経験を積んだ人以外には法務業務が難しくなっている

---

## [GVA TECH](https://gvatech.co.jp/)

+++

![gvatechHP](assets/gvatechHP.png)

+++

スタートアップ・フリーランスを中心に
<br/>
サービス展開してきた

+++

| [AI-CON](https://ai-con.lawyer/)                                          | [AI-CON登記](https://corporate.ai-con.lawyer/)                        |
| ------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| 契約書チェックを<br/>AIで行う                                             | 法人の登記書類の作成を<br/>オンラインで行う                           |
| ![ai-con](https://raw.github.com/ROhta/auth0day/master/assets/ai-con.png) | ![登記](https://raw.github.com/ROhta/auth0day/master/assets/toki.png) |

---

大企業の法務も同じ課題を抱えている

+++
@transition[zoom]

# [AI-CON Pro](https://ai-con-pro.com/)

---

 ## 目次

- マイクロサービス化の流れ |
- Auth0の使いどころ |

---

# マイクロサービス化の流れ

---

### 契約書レビュー（ざっくり）

```
1. これから結ぶ契約書の草案を受け取る
2. ひな型契約書（自社にとっての理想形）と照らし合わせる
3. 草案修正
4. 修正版を契約書の締結相手に送る
5. 1~4を繰り返す
```
@[2](Wordで行うことが殆ど)
@[3](条文単位で行う、草案とひな型の条文順は異なるので照らし合わせが大変)

---

### サービス概要

- 大企業法務向け |
- Word add in |
- セキュリティ最重視 |

+++

#### 使用技術

- client
  - 言語: TypeScript
  - FW: vue.js
- API
  - 言語: Go
  - FW: Buffalo
- DB
  - Aurora MySQL

+++?color=linear-gradient(100deg, white 50%, #567AD2 50%)

@snap[west text-right]
最初期
@snapend
@snap[east]
![初期構成](https://raw.github.com/ROhta/auth0day/master/assets/diagram/first.svg?sanitize=true)
@snapend

---

### 仕様変更

+++

| 大企業                                | スタートアップ<br/>フリーランス   |
| ------------------------------------- | --------------------------------- |
| ひな型を持っていたり<br/>いなかったり | 契約書のひな型を<br/>持っていない |

+++

| 大企業                                                | スタートアップ<br/>フリーランス     |
| ----------------------------------------------------- | ----------------------------------- |
| ひな型を持っていたり<br/>いなかったり                 | 契約書のひな型を<br/>持っていない   |
| 顧客企業作成・GVA TECH作成<br/>両方のひな型でレビュー | GVA TECH作成の<br/>ひな型でレビュー |

+++

システム上の問題点

- ひな型契約書のセキュリティレベルが異なる |
  - GVA TECH作成と顧客企業作成で<br/>ひな型DBは分けるべき |
- セキュリティレベルが異なる<br/>=認証のスコープが異なる |
  - OAuthのフローに従うと、<br/>リソースサーバはAPIとDBの1対1対応が理想 |
  - DBを分けたらリソースAPIも分ける |

+++?color=linear-gradient(100deg, white 50%, #567AD2 50%)

@snap[west text-right]
最初期
@snapend
@snap[east]
![初期構成](https://raw.github.com/ROhta/auth0day/master/assets/diagram/first.svg?sanitize=true)
@snapend

+++

仕様増えた。。。

+++

ここが潮目では。

+++

#### マイクロサービス化を徹底するぞ

+++

柔軟＆堅牢な開発のため、徹底しよう

- スキーマ駆動開発 |
- テスト駆動開発 |
- アジャイル開発 |

+++?color=linear-gradient(100deg, white 40%, #567AD2 60%)

@snap[west span-40 text-left]
どちらのひな型でも
<br/>
契約書レビュー
<br/>
<br/>
・GVA TECH作成
<br/>
・顧客作成
@snapend
@snap[east span-60]
![gvaと自社](https://raw.github.com/ROhta/auth0day/master/assets/diagram/second.svg?sanitize=true)
@snapend

---

### 草案条文とひな型条文の<br/>マッチ精度を上げたい

+++

#### 使用技術

- client
  - 言語: TypeScript
  - FW: vue.js
- API
  - 言語: Go
  - FW: Buffalo
- DB
  - Aurora MySQL
  - elasticsearch |

+++?color=linear-gradient(100deg, white 40%, #3f9ac4 60%)

@snap[west span-40]
elasticsearchを使う
@snapend
@snap[east span-60 text-right]
![ES使用](https://raw.github.com/ROhta/auth0day/master/assets/diagram/third.svg?sanitize=true)
@snapend

---

### EC2が増えすぎている

+++

コンテナ管理をしよう

+++

@snap[north]
使用技術
@snapend
@snap[west]
・client
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・言語: TypeScript
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・FW: vue.js
<br/>
・API
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・言語: Go
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・FW: Buffalo
<br/>
・DB
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・Aurora MySQL
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・elasticsearch
@snapend
@snap[east text-left]
・IaC
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・terraform
<br/>
・CI/CD
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・Fargate
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・ECS
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・github
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・CircleCI
@snapend

+++?color=linear-gradient(100deg, white 40%, #3f9ac4 60%)

@snap[west span-40]
コンテナ管理する
@snapend
@snap[east span-60]
![コンテナ化](https://raw.github.com/ROhta/auth0day/master/assets/diagram/fourth.svg?sanitize=true)
@snapend

---

### もっと精度を上げたい

+++

@snap[north]
使用技術
@snapend
@snap[west]
・client
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・言語: TypeScript
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・FW: vue.js
<br/>
・API
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・言語: Go
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・FW: Buffalo
<br/>
・DB
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・Aurora MySQL
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・elasticsearch
@snapend
@snap[east text-left]
・IaC
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・terraform
<br/>
・CI/CD
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・Fargate
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・ECS
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・GitHub
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・CircleCI
<br/>
@snapend

+++

@snap[north]
使用技術
@snapend
@snap[west]
・client
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・言語: TypeScript
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・FW: vue.js
<br/>
・API
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・言語: Go
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・FW: Buffalo
<br/>
・DB
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・Aurora MySQL
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・elasticsearch
@snapend
@snap[east text-left]
・IaC
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・terraform
<br/>
・CI/CD
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・Fargate
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・ECS
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・GitHub
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・CircleCI
<br/>
・ML
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・SageMaker
@snapend

+++?color=linear-gradient(100deg, white 40%, #23566e 60%)

@snap[west span-40]
機械学習する
@snapend
@snap[east span-60]
![ML使用](https://raw.github.com/ROhta/auth0day/master/assets/diagram/fifth.svg?sanitize=true)
@snapend
