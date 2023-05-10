# jma-earthquake-data-converter
## プログラムについて
- 本プログラムは、気象庁が公開している、[地震月報(カタログ編)の震度データ及び震度観測点一覧](https://www.data.jma.go.jp/eqev/data/bulletin/shindo.html)を読みやすい形式（GISデータ）に変換するプログラムです。
- オープンソースソフトウェアで構築

## データの入手
- 以下の気象庁のサイトより地震月報(カタログ編)の震度データ（zip形式）や震度観測点一覧を入手します。
- https://www.data.jma.go.jp/eqev/data/bulletin/shindo.html
- なお、一括で震度データ（zip形式）をダウンロードするPythonスクリプトは以下にあります。
- https://github.com/shi-works/jma-earthquake-data-converter/blob/main/src/shindo_zip_dl.py

## 震度観測点一覧を読みやすい形式へ変換（code_p2csv.py）
- 震度観測点一覧（datファイル）を読みやすい形式（csvファイル）に変換するプログラムです。
### 使用データ
`https://github.com/shi-works/jma-earthquake-data-converter/blob/main/data/code_p.dat`
### 出力結果
`https://github.com/shi-works/jma-earthquake-data-converter/blob/main/data/code_p.csv`

## 震源データ及び震度データの抽出（dat_converter.py）
- 震度データ（datファイル）から震源データ（csvファイル）及び震度データ（csvファイル）を抽出するプログラムです。
- ※震源データは１番上のレコードが代表値（採用値）となっており、本プログラムでは代表値（採用値）のみ出力します。
### 使用データ
- 震度データ（datファイル）一式
### 出力結果
#### 震源データ
`https://pmtiles-data.s3.ap-northeast-1.amazonaws.com/jma-earthquake/hypocenter.csv`,28.7MB
#### 震度データ
`https://pmtiles-data.s3.ap-northeast-1.amazonaws.com/jma-earthquake/shindo.csv`,199.3MB

## 震源データを読みやすい形式へ変換（hypocenter_converter.py）
- 震源データ（csvファイル）を読みやすい形式（csvファイル）に変換するプログラムです。
### 使用データ
`https://pmtiles-data.s3.ap-northeast-1.amazonaws.com/jma-earthquake/hypocenter.csv`,28.7MB
### 出力結果
`https://pmtiles-data.s3.ap-northeast-1.amazonaws.com/jma-earthquake/hypocenter_convert.csv`,19.6MB

## 震度データを読みやすい形式へ変換（shindo_converter.py）
- 震度データ（csvファイル）を読みやすい形式（csvファイル）に変換するプログラムです。
### 使用データ
`https://pmtiles-data.s3.ap-northeast-1.amazonaws.com/jma-earthquake/shindo.csv`,199.3MB
### 出力結果
`https://pmtiles-data.s3.ap-northeast-1.amazonaws.com/jma-earthquake/shindo_convert.csv`,180.2MB

## 震源データ及び震度データをGISデータ（FaltGeobuf形式）へ変換
- 震度データ及び震源データのGISデータ（FaltGeobuf形式）への変換にはQGISを使用します。
### 使用データ
#### 震源データ
`https://pmtiles-data.s3.ap-northeast-1.amazonaws.com/jma-earthquake/hypocenter_convert.csv`,19.6MB
#### 震度データ
`https://pmtiles-data.s3.ap-northeast-1.amazonaws.com/jma-earthquake/shindo_convert.csv`,180.2MB
### 出力結果（FaltGeobuf形式）
#### 震源データ
`https://pmtiles-data.s3.ap-northeast-1.amazonaws.com/jma-earthquake/hypocenter_convert.fgb`,51.6MB
#### 震度データ
`https://pmtiles-data.s3.ap-northeast-1.amazonaws.com/jma-earthquake/shindo_convert.fgb`,453.8MB

## FaltGeobuf形式からPMTiles形式への変換
FaltGeobuf形式から[PMTiles形式](https://github.com/protomaps/PMTiles)への変換には[feltのtippecanoe](https://github.com/felt/tippecanoe)を使用します。
### 使用データ（FaltGeobuf形式）
#### 震源データ
`https://pmtiles-data.s3.ap-northeast-1.amazonaws.com/jma-earthquake/hypocenter_convert.fgb`,51.6MB
#### 震度データ
`https://pmtiles-data.s3.ap-northeast-1.amazonaws.com/jma-earthquake/shindo_convert.fgb`,453.8MB
### 出力結果（PMTiles形式）
#### 震源データ
`https://pmtiles-data.s3.ap-northeast-1.amazonaws.com/jma-earthquake/hypocenter_convert.pmtiles`,177.4MB
#### 震度データ
`https://pmtiles-data.s3.ap-northeast-1.amazonaws.com/jma-earthquake/shindo_convert.pmtiles`,541.7MB

### ベクトルタイル設計情報
- 震源データ及び震度データそのものを可能な限り生かしたデータです。
- tippecanoeによるデータの間引き（自動）は行っていません。

### ズームレベル範囲
- 0-14

### 属性
- 震源データ及び震度デーの属性はそのまま生かしています。

### PMTiles Viewer
- PMTilesはPMTiles Viewerで閲覧することができます。
- https://protomaps.github.io/PMTiles/

## デモサイト
- （作成中）

## ライセンス
本データセットはCC-BY-4.0で提供されます。使用の際には本レポジトリへのリンクを提示してください。

また、本データセットは、気象庁が公開している、地震月報(カタログ編)の震度データ及び震度観測点一覧を加工して作成したものです。本データセットの使用・加工にあたっては、[気象庁の利用規約](https://www.jma.go.jp/jma/kishou/info/coment.html)を必ずご確認ください。

## 免責事項
利用者が当該データを用いて行う一切の行為について何ら責任を負うものではありません。
