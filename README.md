# EPmaketitle package

日本語 LaTeX で卒論・修論等を執筆する際に，表紙を作成するためのパッケージです．タイトル・著者・日付のほかに，所属や指導教員などを表紙に加えることができます．

## 使い方

とりあえず，upLaTeX で動作テスト済みです．また，パッケージ内で textpos パッケージを読み込みます（TeXLive を使っている人なら大丈夫だと思います）．

プリアンブルに \usepackage{epmaketitle} と書けば \maketitle 風に使えるようになります．表紙に記載する情報を定義するコマンドは以下の通りです：

- title{*和文タイトル*}
- titleEN{*英文タイトル*}
- author{*著者（日本語表記）*}
- authorEN{*著者（英語表記）*}
- studentid{*学籍番号*}
- faculty{*所属（日本語表記）*}
- facultyEN{*所属（英語表記）*}
- advisor{*指導教員*}
- date{*日付*}

これらのコマンドで必要事項を定義したあと（すべて定義しなくても動作します），titlepage 環境内で \epmaketitle を宣言すれば，表紙ページが作成されます．テストファイル（[test.tex](https://github.com/matryo-sika/epmaketitle/blob/master/test.tex)）を upLaTeX で処理して出力した PDF ファイルが [test.pdf](https://github.com/matryo-sika/epmaketitle/blob/master/test.pdf) です．

## 微調整

### テキストブロックの配置

EPmaketitle では，各記載情報の配置（相対位置）は固定されており，記載情報の量によっては表紙がかっこ悪くなるかもしれません．その場合は，テキストブロックの位置を微調整するとよいでしょう．

パッケージ内で，紙面上端から測ったテキストボックスの高さを指定する量が定められています：

|位置を定める量|対応する事項|デフォルト値|
|:---|:---|:---|
|\titlecenterline|和文タイトル・英文タイトル|0.25\paperheight|
|\authorcenterline|著者（日本語表記）・著者（英語表記）|0.5\paperheight|
|\studentidtopline|学籍番号|0.55\paperheight|
|\facultycenterline|所属（日本語表記）・所属（英語表記）・指導教員|0.75\paperheight|
|\datecenterline|日付|0.92\paperheight|

必要があれば，たとえば以下のように定義し直してみてください（日付の位置を再定義した例です）：
```TeX:
\renewcommand{\datecenterline}{0.88\paperheight}
```

### 飾り文字

所属や指導教員の欄のテキストブロックを囲む飾り文字は \epmktdeco で定義されています．別の文字等に変更することも可能ですし，飾り文字が不要な場合は，
```TeX:
\renewcommand{\epmktdeco}{}
```
と再定義してください．

## 不具合
\documentclass コマンドでデフォルトフォントサイズを変更した場合に，レイアウトが崩れると報告がありました（2020年1月28日）．対応予定ですが，時間的に間に合わなければ，\documentclass でフォントサイズを変更せずに，titlepage よりも後の本文中で \large などを唱えるなどしてください．

## ライセンス LICENSE
本パッケージは クリエイティブコモンズ 表示 4.0・国際 （CC-BY 4.0）の下で配布を行う．

This work is licensed under a Creative Commons Attribution 4.0 International License.

## 参考にしたもの
- 奥村晴彦氏の pLaTeX2e 新ドキュメントクラス中の jsarticle.cls
- Norman Gray 氏の textpos package
