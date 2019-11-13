## Auth0 in Microservices

#### ～リーガルテックの事績～

@snap[south]
GVA TECH 太田
@snapend

---

@snap[north]
本スライドは以下のQRコードから閲覧可能です。
@snapend
![QRコード](assets/qrcode.png)
---

### リーガルテック？

---

法律関連のレガシー・労働集約型の領域を

テクノロジーで代替していく

---

特に法務部業務はレガシー

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
![初期構成](https://raw.github.com/ROhta/auth0day/master/assets/svg/first.svg?sanitize=true)
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
![gvaと自社](https://raw.github.com/ROhta/auth0day/master/assets/svg/second.svg?sanitize=true)
@snapend

---

精度を上げたい

---
@snap[north]
精度を上げるために

elasticserachを使おう
@snapend
@snap[midpoint]
![ES使用](https://raw.github.com/ROhta/auth0day/master/assets/svg/third.svg?sanitize=true)
@snapend

---

EC2が増えすぎている

---

@snap[north]
コンテナ管理しよう
@snapend
@snap[midpoint]
![コンテナ化](https://raw.github.com/ROhta/auth0day/master/assets/svg/fourth.svg?sanitize=true)
@snapend

---

もっと精度を上げたい

---

@snap[north]
精度を上げるために

AIを使おう
@snapend
@snap[midpoint]
![AI使用](https://raw.github.com/ROhta/auth0day/master/assets/svg/fifth.svg?sanitize=true)
@snapend

---

さあ認証だ

---
@snap[north]
Auth0と連携させなければ
@snapend
@snap[midpoint]
![Auth0](https://raw.github.com/ROhta/auth0day/master/assets/svg/sixth.svg?sanitize=true)
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
![β版](https://raw.github.com/ROhta/auth0day/master/assets/svg/seventh.svg?sanitize=true)
@snapend

---

 #### 今後の展望

- 各テナント間でCI/CDを回す
- ActionScriptのTypeScript化
