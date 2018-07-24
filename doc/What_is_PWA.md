<!-- $theme:gaia -->
<!-- page_number: true -->
<!-- prerender: true -->

# PWAとは何か?

---


## What Is PWA ?

* PWA
= Progresive Web App 
= 前進したWebアプリケーション

##### なるほどわからん　＼(^o^)／
→別方面から考えてみる。

---

<!-- *template: gaia -->
## PWAの分類

---

## PWAの分類
- (Progressive)Web App なのだから、Webアプリケーションの系列のはず。
- そもそもアプリケーションってどんな物があったっけ？
	- Webアプリ
	- ハイブリッドアプリ
	- ネイティブアプリ

---
## Webアプリ
==<オフラインでの動作>==
- 動かない

==<UIの動作>==
- ブラウザのできることに制限される。
 (=スマホのスワイプなどの動作は苦手)
 
==<開発しやすさ>==
- 少ない言語で開発できる。
→開発者が多く、開発しやすい

---
## ハイブリッドアプリ
==<オフラインでの動作>==
- (ほぼ)動かない
(コンテンツはWebViewなどを利用するため)

==<UIの動作>==
- ブラウザ+スマホの動作
 
==<開発しやすさ>==
- Web系言語 + 一部ネイティブアプリの言語が必要
→どちらかしか出来ない開発者が多い。中途半端。。。

---
## ネイティブアプリ
==<オフラインでの動作>==
- 動く

==<UIの動作>==
- スマホに最適化された動きでサクサク動く。
 
==<開発しやすさ>==
- デバイスによって言語を変える必要がある
→開発者が少なく、開発しにくい

---
## アプリの分類
|アプリ|オフライン|UI|開発しやすさ|
|:-|:-|:-|:-|
|Web|動かない|ブラウザ次第|開発しやすい|
|ハイブリッド|(ほぼ)動かない|ブラウザ+ネイティブ|開発しにくい|
|ネイティブ|動く|ネイティブ次第|開発しにくい|

---
##### ここまでを踏まえて、PWAを考えてみると？

---
## PWA
==<オフラインでの動作>==
- (擬似的に)動く。
→オンライン時に取得したコンテンツをブラウザキャッシュに保存し、オフライン時にはそれを利用することで、擬似的に動かす事ができる。
= ==**Service Worker**== を利用する。
==(*Progressive*と言われる所以)==

---
## PWA
==<UIの動作>==
- ブラウザを利用するので、ブラウザの動きに制限される。
→とはいえ、JavascriptやCSSの様々なプラグインが発展していくことによって、ネイティブのような動作に近づいていくと予想される。**CSSフレームワークを積極的に利用することでスマホ向けのUIは提供可能。**

<small>CSSフレームワーク…[BootStrap](https://getbootstrap.com/),[Onsen UI](https://ja.onsen.io/),[Material-UI](https://material-ui.com/),etc...</small>

---
## PWA
==<開発しやすさ>==
- ==「HTML + Javascript」== を利用
=Webアプリと同じスキルセットで開発可能。

→**つまり、Webアプリと同様、開発しやすい！**

---
## アプリの分類
|アプリ|オフライン|UI|開発しやすさ|
|:-|:-|:-|:-|
|Web|動かない|ブラウザ次第|開発しやすい|
|==PWA==|==(ほぼ)動く==|==ブラウザ次第==|==開発しやすい==|
|ハイブリッド|(ほぼ)動かない|ブラウザ+ネイティブ|開発しにくい|
|ネイティブ|動く|ネイティブ次第|開発しにくい|

---
<!-- *template: gaia -->
## PWAの定義

---
## What Is PWA ?

* PWA
= Progresive Web App 
= 前進したWebアプリケーション
= Webアプリとハイブリッドアプリの中間

##### 少しわかったけど、厳密な定義は？　(´・ω・｀)
→ ==**厳密な定義は現在存在していない**==

---
## PWAの定義
厳密な定義は存在していないが、Googleでは以下の2段階のチェックリストが存在している。
- [Baseline PWA Checklist](https://developers.google.com/web/progressive-web-apps/checklist#baseline)
→PWAとして、最低限クリアすべき項目

- [Exemplary PWA CheckList](https://developers.google.com/web/progressive-web-apps/checklist#exemplary)
→より良いPWAとするために、クリアすべき項目
(今回は言及しません。)

---
### Baseline PWA Checklist
- HTTPSを使っている
- タブレットやモバイルでレスポンシブである
- オフラインでもロードできること
- ホーム画面に追加するためのメタデータが提供されていること
- 3G 回線でも高速に読み込めること
- クロスブラウザで動くこと
- ページ遷移がネットワークによってブロックされているように見えないこと
- それぞれのページが URL を持つこと

---
### Baseline PWA Checklist
- HTTPSを使っている
→ServiceWorkerを利用することが必須条件であるため、**「ServiceWorkerを利用するための条件=HTTPSを使っていること」** となっている。
→ ==**ServiceWorkerが必須**==

---
### Baseline PWA Checklist
- タブレットやモバイルでレスポンシブである
→ ==モバイルファーストの考え方で開発する必要がある。==

---
### Baseline PWA Checklist
- オフラインでもロードできること
→ ==PWA最大の特徴==。
ServiceWorkerのキャッシュ機能を利用し、実現する。
→ ==**ServiceWorkerが必須**==

---
### Baseline PWA Checklist
- ホーム画面に追加するためのメタデータが提供されていること
→[ブラウザ拡張機能](https://developer.mozilla.org/ja/Add-ons/WebExtensions)を利用して、スマホのホーム画面に当該画面を開くための専用アイコンを追加する設定のこと。
==**「manifest.json」**== というファイルを用意する。
<small>※現状、iOSは未対応。</small>

---
### Baseline PWA Checklist
- 3G 回線でも高速に読み込めること
→ServiceWorkerとIndexDB、localstorageを利用し、初回ロードの待ち時間を減少させる仕組みを持っていること。
→ ==**ServiceWorkerが必須**==

---
### Baseline PWA Checklist
- クロスブラウザで動くこと
(言わずもがな)

---
### Baseline PWA Checklist
- ページ遷移がネットワークによってブロックされているように見えないこと
→画面遷移の際に画面がロードされるのではなく、次画面を構成するために必要な情報をAPIで取得し、その結果でHTMLを書き換える方法を取る必要がある。
→要するに ==**SPA(Single Page Application)**==

---
### Baseline PWA Checklist
- それぞれのページが URL を持つこと
→画面をJavascriptで書き換えるだけではなく、URLもきちんと書き換える必要がある。
→要するに ==**SPA(Single Page Application)**==

---
### Baseline PWA Checklist
- HTTPSを使っている
- タブレットやモバイルでレスポンシブである
- オフラインでもロードできること
- ホーム画面に追加するためのメタデータが提供されていること
- 3G 回線でも高速に読み込めること
- クロスブラウザで動くこと
- ページ遷移がネットワークによってブロックされているように見えないこと
- それぞれのページが URL を持つこと

---
### Baseline PWA Checklist
- ==**ServiceWorker**==
- モバイルファースト
- ==**ServiceWorker**==
- ==**manifest.json**==
- ==**ServiceWorker**==
- (言わずもがな)
- ==**SPA**==
- ==**SPA**==

---
### Baseline PWA Checklist
要するに
- ==**ServiceWorker**==
- ==**manifest.json**==
- ==**SPA**==

が構成要素であり、これらを利用したWebアプリがPWAとみなされる！
<small>
※[Lighthouse - Chrome ウェブストア](https://chrome.google.com/webstore/detail/lighthouse/blipmdconlkpinefehnmjammfjpmpbjk)を利用して確認可能。
※Chrome拡張機能の「Audits」タブでも確認可能。
</small>

---
<!-- *template: gaia -->
## What Is PWA ?

---
## What Is PWA ?

- PWA
= Progresive Web App 
= 前進したWebアプリケーション
= Webアプリとハイブリッドアプリの中間
---
## What Is PWA ?
|アプリ|オフライン|UI|開発しやすさ|
|:-|:-|:-|:-|
|Web|動かない|ブラウザ次第|開発しやすい|
|==PWA==|==(ほぼ)動く==|==ブラウザ次第==|==開発しやすい==|
|ハイブリッド|(ほぼ)動かない|ブラウザ+ネイティブ|開発しにくい|
|ネイティブ|動く|ネイティブ次第|開発しにくい|


---
## What Is PWA ?

- PWAの構成要素
	- ==**ServiceWorker**==
	- ==**manifest.json**==
	- ==**SPA**==


==**PWA = (これらで構成される)オフライン環境でも(擬似的に)動作するWebアプリケーション**==