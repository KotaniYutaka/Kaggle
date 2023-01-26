# XGBを用いたKaggleコンペへの取組
## コンペ概要
ユーザーセッションの過去のイベントに基づいてeコマースのクリック、カートへの追加、注文の予測を行う
[OTTO – Multi-Objective Recommender System](https://www.kaggle.com/competitions/otto-recommender-system/overview)

## 手順
### 1.訓練用データの作成(clickに対してのみ)
　1.[Candidate ReRank Model](https://www.kaggle.com/code/cdeotte/candidate-rerank-model-lb-0-575)を改良した[create-150-candidates](https://github.com/yutakakunn/Kaggle/blob/master/create-150-candidates.ipynb)で1ユーザーあたり150個の候補を作成．

　2.[val-click-candidates-features](https://github.com/yutakakunn/Kaggle/blob/master/val-click-candidates-features.ipynb)において，前ステップで作成した結果に特徴量を加え，実際にclickされたかどうかといった正解データを与える．
### 2.テスト用データの作成(clickに対してのみ)
訓練用データを作成した時と同様に作成．しかし，1ユーザーあたり100個の候補を作成（150個だとメモリ不足となるため）
