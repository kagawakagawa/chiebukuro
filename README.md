
# Recommendation-Improved
推薦システム - 実験 + 再現 + イノベーション
## 書籍の読解と再現段階
+ 実践的なレコメンドシステム https://item.jd.com/11007625.html

## 論文の読解と再現段階
+ DeepCoNN https://arxiv.org/abs/1701.04783 Done
+ NRPA https://arxiv.org/abs/1905.12480v1 Done
+ DAML https://dl.acm.org/doi/10.1145/3292500.3330906 Done

## 自身の論文
+ DAML-Improved - DAMLモデルにおけるID情報の融合におけるNRPAモデルのアイデアの借用 完了（モデルは /pic/IDAML.png を参照）
DAML-Distance - DAMLモデルにおけるID情報の融合におけるNRPAモデルのアイデアの借用と距離式の研究 完了
  ユークリッド距離（通常 + 標準化重み付け）
  ピアソン相関係数

![image](/pic/IDAML.png)

## データセット
+ MOVIE LINES (http://www.grouplens.org/node/73)
+ Amazon 5-core(https://nijianmo.github.io/amazon/index.html)
+ YELP (https://www.yelp.com/dataset/download)

## パラメータ(reviews_Sports_and_Outdoors_5 Best)

### ⚠️このリポジトリのDropOut確率パラメータはすべて1に設定されており、参考価値はありません。デモ目的のみであり、実際のシナリオに応じて調整してください

```python3
#DeepCoNN
BATCH_SIZE          = 64
EPOCHS              = 50
LEARNING_RATE       = 0.02
CONV_LENGTH         = 3
CONV_KERNEL_NUM     = 32
FM_K                = 1 #Cross-vector dimension of the Factorization Machine
LATENT_FACTOR_NUM   = 64
GPU_DEVICES         = 0

#NRPA
BATCH_SIZE          = 128
EPOCHS              = 50
LEARNING_RATE       = 0.01
CONV_LENGTH         = 3
CONV_KERNEL_NUM     = 28
FM_K                = 1 #Cross-vector dimension of the Factorization Machine
LATENT_FACTOR_NUM   = 56
GPU_DEVICES         = 0
ID_EMBEDDING_DIM    = 32
ATTEN_VEC_DIM       = 32

#DAML
BATCH_SIZE          = 128
EPOCHS              = 50
LEARNING_RATE       = 0.001
CONV_LENGTH         = 3
CONV_KERNEL_NUM     = 16
FM_K                = 1 #Cross-vector dimension of the Factorization Machine
LATENT_FACTOR_NUM   = 58
GPU_DEVICES         = 0
ID_EMBEDDING_DIM    = 32
ATTEN_VEC_DIM       = 16
ATT_CONV_SIZE       = 3

#ImprovedDAML
BATCH_SIZE          = 24
EPOCHS              = 75
LEARNING_RATE       = 0.001
CONV_LENGTH         = 3
CONV_KERNEL_NUM     = 16
FM_K                = 1 #"Cross-vector dimension of the Factorization Machine
LATENT_FACTOR_NUM   = 32
GPU_DEVICES         = 0
ID_EMBEDDING_DIM    = 32
ATTEN_VEC_DIM       = 16
REVIEW_SIZE         = 15
ATT_CONV_SIZE       = 3

#DistanceImprovedDAML (Standardized Euclidean distance )
BATCH_SIZE          = 24
EPOCHS              = 75
LEARNING_RATE       = 0.001
CONV_LENGTH         = 3
CONV_KERNEL_NUM     = 16
FM_K                = 1 #Cross-vector dimension of the Factorization Machine
LATENT_FACTOR_NUM   = 32
GPU_DEVICES         = 0
ID_EMBEDDING_DIM    = 32
ATTEN_VEC_DIM       = 16
REVIEW_SIZE         = 15
ATT_CONV_SIZE       = 3
```
  
## トレーニング結果
testフォルダー内のjsonファイルです。

命名形式:
>> train\_{model_name}\_{dataset_name}\_{reviews_length}\_{reviews_size}\_{user_num}\_{item_num}

## 環境
+ python3.7
+ pytorch => torch             1.0.0 && torchvision       0.2.1   
+ gensim => gensim            3.8.1   
+ numpy => numpy             1.16.0 
+ pandas => pandas            0.25.3  
+ tqdm => tqdm              4.42.0
+ py2neo => py2neo            4.3.0 
>>>>>>> origin/master
