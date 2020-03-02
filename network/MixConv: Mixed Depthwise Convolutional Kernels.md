# [MixConv: Mixed Depthwise Convolutional Kernels](https://arxiv.org/abs/1907.09595)

git: [tf](https://github.com/tensorflow/tpu/tree/master/models/official/mnasnet/mixnet), [pytorch](https://github.com/rwightman/gen-efficientnet-pytorch)

## 概要

+ パラメータ数を激減させる新しい畳み込みMixConvを提案
+ MixConv層を含んだモデルをAIに自動生成させることでMixNetを開発 
+ MixNetはMobileNet-V3やMnasNetなどの小型画像認識モデルのみならずResNet-153に対してはパラメータ数1/9程度で性能を凌いだ

## Depthwise conv

各入力チャネルに対してフィルタを一つだけにしたもの。(MobileNetなどに使用されている)
[詳細](https://qiita.com/omiita/items/77dadd5a7b16a104df83)

## MixConv

チャネル(のグループ)ごとに異なる大きさのフィルターを使うようにしたDepthwise Convのこと。 