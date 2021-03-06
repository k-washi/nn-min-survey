# [Deep learning for multiple object tracking: a survey](https://www.researchgate.net/publication/330220368_Deep_Learning_for_Multiple_Object_Tracking_A_Survey)

codes: https://github.com/SpyderXu/multi-object-tracking-paper-list/blob/master/README.md

## abst

Deeplearningは、複数オブジェクトの追跡に効果があることが証明されている。しかし、頻繁なオクルージョン、紛らわしい外観、内外(in-and-out)オブジェクト?、十分なラベルつきデータの不足が課題である。
最近(2019, 3)は、深層学習理論とベンチマーク設定の開発の結果、表現学習からネットワークのモデリングへと急速に進歩している。

## 導入

手動で選択したオブジェクトの追跡は半教師付き学習タスクであるため、ターゲットの特徴を学習するのに十分なサンプルがないという問題がある。
初期の深層学習ベースの追跡アルゴリズムは、相関フィルタやスパース主成分分析と比較して劣っている。
深層学習をオブジェクト追跡に適用するために、大きく3つの戦略が考えられる。

1. オブジェクト追跡の特徴学習を促進するため、幅広いサンプルを作成する
2. CNNから低層または複数層の特徴を抽出することで、こうれ別の特徴より識別力が高い場合もある
3. End2endのDNNは、追跡結果を直接取得するように設計、訓練される

複数物体の追跡(MOT)は、単一オブジェクトを追跡する困難性に加えて、見失ったオブジェクトがサイド表示されたときに再識別が必要で、カメラの視野から出たときにオブジェクト追跡を終了する必要がある。
それに加えて、オクルージョン、背景の乱雑さ、ポーズの変更の問題もある。

例：
分類または認識のタスクから特徴が学習されていても、従来の手作りの特徴をディープニューラルネットワークから抽出された特徴に置き換えて検出結果を関連付けることが可能。
さらに、時間的および空間的アテンションマップや時間的順序など、MOTの属性を調査するとパフォーマンスが向上することが証明されている。
さらに、一部のエンドツーエンドのディープラーニングアーキテクチャは、外観記述子だけでなくモーション情報の特徴も抽出するように設計されている。


## 概要

Fig.1 にオンラインとオフラインのトラッキングフレームを示している。(詳細はTab.1.)

オンラインMOTフレームワークの課題は、
1. 検出結果に関連する堅牢な関連付けメトリックを学習すること
2. 真の検出結果と誤検出結果を区別して新しいトラックを作成するタイミング
3. 失われたトラックを終了するタイミング


[DeepSort](https://github.com/nwojke/deep_sort) および[CDA-DDAL](https://www.researchgate.net/publication/316023254_Confidence-Based_Data_Association_and_Discriminative_Deep_Appearance_Learning_for_Robust_Online_Multi-Object_Tracking) は、検出に関連付ける個人再識別タスクから外観の特徴を学習する。RAN およびAMIR は、自動回帰およびLong Short-Term Memory（LSTM）ネットワークを使用したマッチング分類により、動きと外観の特徴を予測する。[STAM-MOT](https://web.engr.oregonstate.edu/~lif/1925.pdf) は、空間的および時間的アテンションマップを適用して、追跡における部分オクルージョンの問題を処理します。リカレントニューラルネットワークLSTM（RNN-LSTM）は、エンドツーエンドのディープニューラルネットワークを設計して、AP-HWDPL のようなパーティクルフィルタのようなトラックの検出とステートメントの更新、ステートメントの更新、初期化と終了を関連付ける。オブジェクトの最適な位置を見つけるために、STAM-MOT は、単一のオブジェクトの追跡に一般的に使用される密な検索戦略を採用している。 MHTフレームワークを使用する2つの深層学習ベースの方法はMHT-DAM とMHT-bLSTM であり、CNNおよび双線形LSTMネットワークを使用して外観の特徴を学習する。

オフラインMOTフレームワークの課題は、
1. グラフとネットワークを構築すること
2. グローバルラベル付け問題を最適化すること
  
SiameseCNN およびCNNTCM で、検出と検出のペアワイズ類似性および短いトラック間の類似性を学習できる。より正確な類似性メトリックを取得するために、Quad-CNN で、時間的な順序などの追加情報が考慮された。これらのシーケンシャル特徴は、GCRA で強化されています。さらに、研究者は、マルチカットフローなどのネットワーク最適化を、JointMC の深いフロー機能とLMP のリフトエッジによって改善できることを発見している。また、ネットワークフローは、DeepNetWorkでエンドツーエンドの学習方法でグローバルに最適化することもできた。

深層学習が追跡予測とデータ関連付けの側面から追跡パフォーマンスを改善するのに効果的であることが証明された。
画像認識タスクと同様に、ディープCNNによる外観機能の自動学習は、オンライン追跡とオフライン最適化の両方で、識別とオクルージョンに対するロバスト性を促進できる。
RNNによるモーション特徴の学習は、モーション予測の精度を高めるのに役立ち、その結果、トラックと検出の間の2者間マッチングのパフォーマンスを向上する。
個人の再認識は、関連タスクから学習したDeepな特徴を組み合わせることで追跡パフォーマンスが向上するとともに、回帰精度が向上する。