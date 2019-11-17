## Auth0 in Microservices

### ～リーガルテックの事績～

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

- 契約による法的拘束力は恐ろしい
- 契約書を結ぶには多大な労力によるチェックが必要 |

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

## [gva tech](https://gvatech.co.jp/)

+++

![gvatechHP](assets/gvatechHP.png)

+++

スタートアップ・フリーランスを中心に
<br/>
サービス展開してきた

+++

| [AI-CON](https://ai-con.lawyer/)                                          | [AI-CON登記](https://corporate.ai-con.lawyer/)                        |
| ------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| ![ai-con](https://raw.github.com/ROhta/auth0day/master/assets/ai-con.png) | ![登記](https://raw.github.com/ROhta/auth0day/master/assets/toki.png) |

---

大企業の法務も課題を抱えている！

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
1. これから結ぶ契約書のドラフトを受け取る
2. 雛形契約書（自社にとっての理想形）と照らし合わせる
3. ドラフト修正
4. 修正版を契約書の締結相手に送る
5. 1~4を繰り返す
```
@[2](wordで行うことが殆ど)
@[3](条文単位で行う、ドラフトと雛形の条文順は異なるので照らし合わせが大変)

---

### サービス概要

- 大企業法務向け |
- word add in |
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

| スタートアップ<br/>フリーランス | 大企業                              |
| ------------------------------- | ----------------------------------- |
| 契約書の雛形を<br/>持っていない | 雛形を持っていたり<br/>いなかったり |

+++

| スタートアップ<br/>フリーランス   | 大企業                                              |
| --------------------------------- | --------------------------------------------------- |
| 契約書の雛形を<br/>持っていない   | 雛形を持っていたり<br/>いなかったり                 |
| GVA TECH作成の<br/>雛形でレビュー | GVA TECH作成・顧客企業作成<br/>両方の雛形でレビュー |

+++

システム上の問題点

- 雛型契約書のセキュリティレベルが異なる |
  - GVA TECH作成と顧客企業作成で<br/>雛形DBは分けるべき |
- セキュリティレベルが異なる<br/>=認証のスコープが異なる |
  - リソースサーバはAPIとDBの1対1対応が理想 |
  - DBを分けたらリソースAPIも分ける |

+++

仕様増えた。。。

+++

ここが潮目では。

+++

#### マイクロサービスを徹底するぞ！

+++

柔軟＆堅牢な開発のため、徹底しよう

- スキーマ駆動開発 |
- テスト駆動開発 |
- アジャイル開発 |

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

### 精度を上げたい

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
・Iac
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・terraform
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
・Iac
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・terraform
・CI/CD
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・Fargate
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・ECS
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・github
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
・Iac
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・terraform
・CI/CD
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・Fargate
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・ECS
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;・github
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

---

### やりきった!!

+++

### やりきった...?

+++

### サービス概要

- 大企業法務向け
- word add in
- セキュリティ最重視 |

+++

### **さあ認証だ**

+++?color=linear-gradient(100deg, white 40%, #23566e 60%)

@snap[west span-40]
Auth0と
<br/>
連携させなければ
@snapend
@snap[east span-60]
![withAuth0](https://raw.github.com/ROhta/auth0day/master/assets/diagram/sixth.svg?sanitize=true)
@snapend

+++

@fa[dizzy]どうすればいいの@fa[dizzy]

---

# Auth0の<br/>使いどころ

+++

- customDB
- トークン検証API

---

## customDB

+++

ユーザデータの格納場所

- user_metadata or app_metadata |
  - [profileの項目以外のデータを格納する場所](https://auth0.com/docs/users/references/user-profile-structure#user-profile-attributes) |
  - [userに操作させたい情報はuser_metadataを使用](https://community.auth0.com/t/differences-between-client-metadata-and-app-metadata/21388/2) |
- 顧客データがuser_metadataに収まらないかも |
  - [userあたり16MBまで](https://auth0.com/docs/users/concepts/overview-user-metadata#metadata-best-practices) |
  - [userあたり10項目まで](https://auth0.com/docs/users/references/metadata-field-name-rules#metadata-size-limits) |
  - [custom DBを構築するのがよい](https://community.auth0.com/t/metadata-size-limits/6662) |

+++

customDB データ連携

- customDBをpublicに晒さないため、APIを挟む |
- Database Connectionsを設定し、<br/>ActionScriptsによりAPIへCRUDリクエスト |

+++?color=linear-gradient(100deg, white 40%, #0b1a21 60%)

![Auth0Tenant](https://raw.github.com/ROhta/auth0day/master/assets/diagram/auth0.svg?sanitize=true)

---

## トークン検証API

+++

構築経緯

- マイクロサービス化により、リソースAPIが複数 |
- リソースAPIの個数分のトークン検証処理コード |
  - 処理がばらつく恐れ ⇔ 処理統一の必要 |
  - DRY原則 |
- トークン検証処理をAPI化して、リクエストを送る |

+++

技術選定

- ~~API Gateway + Lambda~~ |
  - AWS SAMの導入 |
  - 多くのAPIからリクエストを受け続けるので、lambdaの恩恵があまり無い |
- Buffallo API |
  - 他のコンテナと同一基盤に載せた方が無難 |

---

### 躓きポイント

+++

#### Auth0 SDKのErrorが<br/>依存module jwt-goのError情報を塗り替える

+++

[auth0/go-jwt-middleware](https://github.com/auth0/go-jwt-middleware)の抜粋
※[dgrijalva/jwt-go](https://github.com/dgrijalva/jwt-go)に依存（package名: jwt）
```go
func (m *JWTMiddleware) CheckJWT(w http.ResponseWriter, r *http.Request) error {
中略

    // Now parse the token
	parsedToken, err := jwt.Parse(token, m.Options.ValidationKeyGetter)

	// Check if there was an error in parsing...
	if err != nil {
		m.logf("Error parsing token: %v", err)
		m.Options.ErrorHandler(w, r, err.Error())
		return fmt.Errorf("Error parsing token: %v", err)
    }

中略

	// Check if the parsed token is valid...
	if !parsedToken.Valid {
		m.logf("Token is invalid")
		m.Options.ErrorHandler(w, r, "The token isn't valid")
		return errors.New("Token is invalid")
	}

中略
}
```
@[5](jwt-goの正常値とエラー値の返却)
@[8](エラーハンドリング)
@[9](err.Error())
@[10](生成されたエラーをフォーマットして返却)
@[18](他の箇所では文字列を渡している)


+++


+++

- goのmoduleの返り値の型がおかしい
  - dgrijalva/jwt-go というmodule
  - Issueにも挙げられている
  - https://github.com/dgrijalva/jwt-go/pull/355

+++



---

### その他やっていること

- Connections |
  - social login |
- Rules |
  - srcIP制限 |
  - MFA |

---

#### 最終的に

+++?color=linear-gradient(100deg, white 40%, #0b1a21 60%)

@snap[west span-40]
こうなった
@snapend
@snap[east span-60]
![β版](https://raw.github.com/ROhta/auth0day/master/assets/diagram/seventh.svg?sanitize=true)
@snapend

---

### 今後やっていくこと

- トークン検証API廃棄
  - 処理のプライベートパッケージ化
- 各テナント間でCI/CDを回す
- ActionScriptのTypeScript化

---

## [AI-CON Pro](https://ai-con-pro.com/)
## [β版リリース](https://prtimes.jp/main/html/rd/p/000000030.000033386.html)
## 問い合わせ受付中

---

@snap[north]
本スライドは
<br/>
こちらから閲覧できます
@snapend
@snap[middle]
![QRコード](assets/qrcode.png)
@snapend
