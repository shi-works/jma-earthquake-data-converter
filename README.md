# jma-earthquake-data-converter
## プログラムについて
- 本プログラムは、気象庁が公開している、[地震月報(カタログ編)の震度データや震度観測点一覧](https://www.data.jma.go.jp/eqev/data/bulletin/shindo.html)を読みやすい形式（GISデータ）に変換するプログラムです。
- オープンソースソフトウェアで構築

## デモサイト
- （作成中）

### データの入手
- 以下の気象庁のサイトより地震月報(カタログ編)の震度データ（zip形式）や震度観測点一覧を入手します。
- https://www.data.jma.go.jp/eqev/data/bulletin/shindo.html
- なお、一括で震度データ（zip形式）をダウンロードするPythonスクリプトは以下にあります。
- https://github.com/shi-works/jma-earthquake-data-converter/blob/main/src/shindo_zip_dl.py

### 震度観測点一覧を読みやすい形式へ変換（code_p2csv.py）
- 震度観測点一覧（datファイル）を読みやすい形式（csvファイル）に変換するプログラムです。

## ライセンス
本データセットは[CC-BY-4.0](https://github.com/shi-works/traffic-accident-pmtiles/blob/main/LICENSE)で提供されます。使用の際には本レポジトリへのリンクを提示してください。

また、本データセットは交通事故統計情報のオープンデータ（2019年、2020年、2021年）の本票を加工して作成したものです。本データセットの使用・加工にあたっては、[警察庁Webサイトの利用規約](https://www.npa.go.jp/rules/index.html)を必ずご確認ください。

## 免責事項
利用者が当該データを用いて行う一切の行為について何ら責任を負うものではありません。
