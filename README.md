# XGBを用いたKaggleコンペへの取組


## コンペ概要
ユーザーセッションの過去のイベントに基づいて将来クリック，カートへの追加，注文を行う品物の予測を行う

[OTTO – Multi-Objective Recommender System](https://www.kaggle.com/competitions/otto-recommender-system/overview)

## 手順(clickに対してのみ)
### 1.訓練用データの作成
 1.[Candidate ReRank Model](https://www.kaggle.com/code/cdeotte/candidate-rerank-model-lb-0-575)を改良した[create-150-candidates](https://github.com/yutakakunn/Kaggle/blob/master/create-150-candidates.ipynb)で1ユーザーあたり150個の候補を作成．

 2.[val-click-candidates-features](https://github.com/yutakakunn/Kaggle/blob/master/val-click-candidates-features.ipynb)において，前ステップで作成した結果に特徴量と実際にclickされたかどうかといった正解データを与える．
### 2.テスト用データの作成
[test-100-candidates](https://github.com/yutakakunn/Kaggle/blob/master/test-100-candidates.ipynb)において訓練用データを作成した時と同様に作成．しかし，1ユーザーあたり100個の候補を作成（150個だとメモリ不足となるため）

### 3.XGBのトレーニング
[xgb-click-train](https://github.com/yutakakunn/Kaggle/blob/master/xgb-click-train.ipynb)において，作成した訓練用データを用いてトレーニングを行う．

### 4.提出用データの作成
[xgb-click-test](https://github.com/yutakakunn/Kaggle/blob/master/xgb-click-test.ipynb)において，手順2で作成したテスト用データと手順3で作成したモデルを用いて，将来最もclickする可能性の高い上位20個の品物を1ユーザーごとに選出．


## 参考文献等
今回の取組は，Discussionに投稿された[How To Build a GBT Ranker Model](https://www.kaggle.com/competitions/otto-recommender-system/discussion/370210)を参考とした．
### ノートブック
[Candidate ReRank Model - [LB 0.575]](https://www.kaggle.com/code/cdeotte/candidate-rerank-model-lb-0-575) created by [CHRIS DEOTTE](https://www.kaggle.com/cdeotte)
### データセット
[OTTO Chunk Data in Parquet Format](https://www.kaggle.com/datasets/columbia2131/otto-chunk-data-inparquet-format) created by [COLUM2131](https://www.kaggle.com/datasets/columbia2131/otto-chunk-data-inparquet-format)

[OTTO train and validation (extracted from train)](https://www.kaggle.com/datasets/radek1/otto-train-and-test-data-for-local-validation) created by [RADEK OSMULSKI](https://www.kaggle.com/radek1)

