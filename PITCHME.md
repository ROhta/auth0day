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

- 契約による法的拘束力は恐ろしい |
- 契約書を結ぶには、多大な労力によるチェックが必要 |

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

## 知識・スキルの<br/>属人化・専門化

+++

法律は全ての人に等しく適用される
<br/>
@fa[arrows-alt-v]
<br/>
法務の情報は非対称化する

---

![gvatechHP](assets/gvatechHP.png)
<br/>
弊社HPより

+++

スタートアップ・フリーランスを中心に
<br/>
サービス展開してきた

+++

| AI-CON                                                                    | AI-CON登記                                                            |
| ------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| ![ai-con](https://raw.github.com/ROhta/auth0day/master/assets/ai-con.png) | ![登記](https://raw.github.com/ROhta/auth0day/master/assets/toki.png) |

---

大企業の法務も課題を抱えている！

+++
@transition[zoom]

# [AI-CON Pro](https://ai-con-pro.com/)

---

 # 目次

- マイクロサービス化の流れ |
- Auth0の使いどころ |

---

# マイクロサービス化の流れ

---

### 契約書レビュー（ざっくり）

```
1. これから結ぶ契約書のドラフトを受け取る
2. 雛形契約書（自社にとっての理想形）と照らし合わせる
3. ドラフト修正
4. 修正版を契約書の締結相手に送る
5. 1~4を繰り返す
```
@[2](wordで行うことが殆ど)
@[3](条文単位で行う、ドラフトと雛形の条文順は異なるので照らし合わせが大変)

---

#### サービス概要

- 大企業法務向け |
- word add in |
- セキュリティ最重視 |

+++?color=linear-gradient(100deg, white 50%, #567AD2 50%)

@snap[west text-right]
最初期
@snapend
@snap[east]
![初期構成](https://raw.github.com/ROhta/auth0day/master/assets/diagram/first.svg?sanitize=true)
@snapend

---

#### 仕様変更

+++

| スタートアップ<br/>フリーランス | 大企業                              |
| ------------------------------- | ----------------------------------- |
| 契約書の雛形を<br/>持っていない | 雛形を持っていたり<br/>いなかったり |

+++?color=linear-gradient(100deg, white 40%, #567AD2 60%)

@snap[west span-40 text-left]
どちらの雛形でも
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

#### 精度を上げたい

+++?color=linear-gradient(100deg, white 40%, #3f9ac4 60%)

@snap[west span-40]
elasticserachを使おう
@snapend
@snap[east span-60]
![ES使用](https://raw.github.com/ROhta/auth0day/master/assets/diagram/third.svg?sanitize=true)
@snapend

---

#### EC2が増えすぎている

+++?color=linear-gradient(100deg, white 40%, #3f9ac4 60%)

@snap[west span-40]
コンテナ管理しよう
@snapend
@snap[east span-60]
![コンテナ化](https://raw.github.com/ROhta/auth0day/master/assets/diagram/fourth.svg?sanitize=true)
@snapend

---

#### もっと精度を上げたい

+++?color=linear-gradient(100deg, white 40%, #23566e 60%)

@snap[west span-40]
AIを使おう
@snapend
@snap[east span-60]
![AI使用](https://raw.github.com/ROhta/auth0day/master/assets/diagram/fifth.svg?sanitize=true)
@snapend

---

#### やりきった!!

+++

#### やりきった...?

+++

#### サービス概要

- 大企業法務向け
- word add in
- セキュリティ最重視 |

+++

#### **さあ認証だ**

+++?color=linear-gradient(100deg, white 40%, #23566e 60%)

@snap[west span-40]
Auth0と
<br/>
連携させなければ
@snapend
@snap[east span-60]
![Auth0](https://raw.github.com/ROhta/auth0day/master/assets/diagram/sixth.svg?sanitize=true)
@snapend

+++

@fa[dizzy]どうすればいいの@fa[dizzy]

---


# Auth0の<br/>使いどころ

+++?color=linear-gradient(100deg, white 40%, #0b1a21 60%)

@snap[west span-40]
こうなった
@snapend
@snap[west span-60]
![β版](https://raw.github.com/ROhta/auth0day/master/assets/diagram/seventh.svg?sanitize=true)
@snapend

---

### Auth0構成

---

#### 今後の展望

- 各テナント間でCI/CDを回す
- ActionScriptのTypeScript化
