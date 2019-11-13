## Auth0 in Microservices

#### ～リーガルテックの事績～

@snap[south]
GVA TECH 太田
@snapend

---

@snap[north]
本スライドは
<br/>
こちらから閲覧できます
@snapend
@snap[middle]
![QRコード](assets/qrcode.png)
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

![gvatechHP](assets/gvatechHP.png)
弊社HPより

+++

スタートアップ・フリーランスを中心に
<br/>
サービス展開してきた

+++

@snap[north-west]
ai-con
@snapend
@snap[north-east]
![ai-con](assets/ai-con.png)
@snapend

@snap[south-west]
ai-con登記
@snapend
@snap[south-east]
![登記](assets/toki.png)
@snapend

---

大企業の法務も課題を抱えている！

+++
@transition[zoom]

# [AI-CON Pro](https://ai-con-pro.com/)

---

 ### 目次

- マイクロサービス化の流れ |
- Auth0の使いどころ |

---

### マイクロサービス化の流れ

---

#### サービス構成

@snap[north]
最初期
@snapend
@snap[midpoint]
![初期構成](https://raw.github.com/ROhta/auth0day/master/assets/diagram/first.svg?sanitize=true)
@snapend

---

仕様変更

---

@snap[north]
次のどちらでも契約書レビューを行いたい

- GVA TECH作成の雛形契約書
- 顧客作成の雛形契約書
@snapend
@snap[midpoint]
![gvaと自社](https://raw.github.com/ROhta/auth0day/master/assets/diagram/second.svg?sanitize=true)
@snapend

---

精度を上げたい

---
@snap[north]
精度を上げるために

elasticserachを使おう
@snapend
@snap[midpoint]
![ES使用](https://raw.github.com/ROhta/auth0day/master/assets/diagram/third.svg?sanitize=true)
@snapend

---

EC2が増えすぎている

---

@snap[north]
コンテナ管理しよう
@snapend
@snap[midpoint]
![コンテナ化](https://raw.github.com/ROhta/auth0day/master/assets/diagram/fourth.svg?sanitize=true)
@snapend

---

もっと精度を上げたい

---

@snap[north]
精度を上げるために

AIを使おう
@snapend
@snap[midpoint]
![AI使用](https://raw.github.com/ROhta/auth0day/master/assets/diagram/fifth.svg?sanitize=true)
@snapend

---

さあ認証だ

---
@snap[north]
Auth0と連携させなければ
@snapend
@snap[midpoint]
![Auth0](https://raw.github.com/ROhta/auth0day/master/assets/diagram/sixth.svg?sanitize=true)
@snapend
---

どうしたらいい？？？？？

---


### Auth0の使いどころ

---

@snap[north]
こうなった
@snapend
@snap[midpoint]
![β版](https://raw.github.com/ROhta/auth0day/master/assets/diagram/seventh.svg?sanitize=true)
@snapend

---

 #### 今後の展望

- 各テナント間でCI/CDを回す
- ActionScriptのTypeScript化
