# 機械学習タスク

## 教師あり学習の主なタスク：

1. 分類（Classification）
- 画像認識：写真から物体やシーンを識別
- テキスト分類：文書のカテゴリー分類やスパム検出
- 音声認識：音声を文字に変換
- 出力が離散的なカテゴリーである

1. 回帰（Regression）
- 株価予測、売上予測などの数値予測
- 画像からの年齢推定
- センサーデータからの物理量予測
- 出力が連続量である

1. 物体検出（Object Detection）
- 画像中の物体の位置と種類を特定
- 自動運転での歩行者や車両の検出

1. セグメンテーション（Segmentation）
- 画像の各ピクセルをカテゴリーに分類
- 医療画像での腫瘍領域の特定

## 生成系のタスク：

1. 生成モデル（Generative Models）
- 画像生成：GANやDiffusionモデルによる画像作成
- テキスト生成：ChatGPTなどの大規模言語モデル(Transformerモデル)
- 音声合成：自然な人間の声の生成

2. 変換・翻訳（Translation/Transformation）
- 機械翻訳：ある言語から別の言語への変換
- 画像変換：写真のスタイル変換
- 音声変換：声質の変換

## 自己教師あり学習のタスク：

ここらへんよくわかんない

1. 表現学習（Representation Learning）
- データの特徴量を教師なしで学習
- BERTなどの事前学習モデルの作成

2. 異常検知（Anomaly Detection）
- 正常データから逸脱したパターンの検出
- 製造ラインでの不良品検出
