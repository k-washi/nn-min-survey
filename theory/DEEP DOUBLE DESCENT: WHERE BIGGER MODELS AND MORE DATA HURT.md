# [DEEP DOUBLE DESCENT: WHERE BIGGER MODELS AND MORE DATA HURT](https://arxiv.org/pdf/1912.02292.pdf)

従来の機械学習では、学習量が多すぎると過学習と呼ばれる状態に陥り、精度が悪化すると考えられていたが、さらに学習するとDeep Double Descentと呼ばれる、さらなる精度向上が起きる場合がある。
(特にモデルが大きいと発生する)

モデルが学習できる量(EMCと呼ばれる, モデルのサイズによる)より少ない学習データ量であれば、Double Descentが商事、学習すればするほど精度が向上する。
