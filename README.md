# RdJUFiles

JU410で記録した win formatのファイルを読む関数

## rdwin1_ch

* rdwin1_ch(data; nch=3)
* win format のファイルを読み込んだデータから波形などの情報を取り出す．
* data: win format のファイル１つをバイナリで読み込んだデータ
* nch: チャンネル数．ファイルを読めばチャンネル数も決まるが，たとえば，６チャンネル記録する設定になっているが，３チャンネル分しかデータとして記録されていないというような場合に対応するため，引数としている．初期設定は，nch = 3 である．
* rdjusngl，rdjumultから引いており，普通は使用しない．波形のリストを作成するときなどに使用する．

## rdjusngl

* rdjusngl(wvdir, obs ; coef=1.2310680e-07, rm_offset=1)
* 図１のようなフォルダ構造の win file を読む．
* イメージとしては，単点測定．
* wvdir：文字型変数：測定点の上のディレクトリの名前
* obs：文字型ベクトル：複数の測定の名前

## rdjumult

* rdjumult(wvdir, obs, pnt; coef=1.2310680e-07, rm_offset=1)
* 図２のようなフォルダ構造の win file を読む．
* イメージとしては，アレイ測定のように１測定で複数のセンサーを設置している場合．
* wvdir：文字型変数：測定点の上のディレクトリの名前
* obs：文字型ベクトル：複数の測定の名前
* pnt：文字型ベクトル：複数のセンサーの名前

<img src="./rdjufig.png" width=400>

## 共通事項

* オプション
  * coef=1.2310680e-07：地動換算係数をゲイン ×100 のときの値を初期設定としている．
  * rm_offset=1：オフセットを除いた波形を返す．
* 返す値：named tupleで返している．
* wave = rdju( ) のように返した場合
  * wave.headtime：先頭時刻を配列で返す．［年，月，日，時，分，秒］
  * wave.nwave：波形のサンプル数/チャンネル
  * wave.hz：サンプリング周波数
  * wave.nch：チャンネル数
  * wave.chid：チャンネルID．ju410で設定している値．文字型ベクトル
  * wave.waveF：波形データ：実数型配列．大きさは (nwave，nch)


[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://nmaedajp.github.io/RdJUFiles.jl/stable/)
[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://nmaedajp.github.io/RdJUFiles.jl/dev/)
[![Build Status](https://github.com/nmaedajp/RdJUFiles.jl/actions/workflows/CI.yml/badge.svg?branch=main)](https://github.com/nmaedajp/RdJUFiles.jl/actions/workflows/CI.yml?query=branch%3Amain)