# [RandAugment: Practical automated data augmentation with a reduced search space](https://arxiv.org/abs/1909.13719)

画像認識分野では、画像データを少し回転させたり左右反転させたりなどの操作をすることで、画像データ数を増やすDataAugmentationが良く使用される。

強化学習を使用して自動的にDAを最適に行う方法が提案されているが、計算量や適用部分がミニバッチなため本来のタスクにとって最適であるかわからない。
そのため、ランダムにNこのAugumentation手法(=transformation)を選択するRandAugmentを提案。

## パラメータ

+ N: 選択するtransformationの数
+ M: Augmentationをどれだけ強くかけるか

以上をグリッドサーチで探索

## N

rotateやcolor, contrast, identityなど論文中ではtransform(14個)からN個選択している。

## M

回転の強さなど、、、、

最小M=0, 最大M=10の整数

## コード例

```python
transforms = [’Identity’, ’AutoContrast’, ’Equalize’, ’Rotate’, 
’Solarize’, ’Color’, ’Posterize’, ’Contrast’, ’Brightness’,
’Sharpness’, ’ShearX’, ’ShearY’, ’TranslateX’, ’TranslateY’]

def randaugment (N, M):
  sampled_ops = np.random.choice(transforms, N) 
  return [(op, M) for op in sampled_ops]

```