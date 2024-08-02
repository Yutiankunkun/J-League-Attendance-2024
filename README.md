**【デロイトトーマツリスクアドバイザリー合同会社】 Jリーグの観客動員数予測 2024**
Jリーグ公式戦の試合結果やスタジアム等の時系列データから観客動員数を予測しよう。
そこで本コンペでは、過去の観客動員数やチーム名、天候などをヒントに、「J1リーグにおけるスタジアム観客動員数を予測するモデル」を作成し、その予測精度を競っていただきます。

**評価方法**
精度評価は、評価関数「RMSE（Root Mean Squared Error 平均二乗誤差）」を使用します。

**データ概要**
学習用：2006 ~ 2017年のJ1リーグ各試合の観客動員数、チーム名、開催スタジアム、天候、出場メンバー、試合結果等の情報
評価用：2018～2019年のJ1リーグの試合の情報

**最終成績**
LB：5256.6451146
PB：5179.0369024
Ranking：14/311

**分析方法**
前処理：onehot encoding, creating new feature(eg.discomfort,latitude,longitude)
モデル：catboost＋optuna
Feature：'section', 'round', 'temperature', 'humidity', 'capacity',
       'latitude', 'longitude', 'year', 'month', 'day', 'day_of_week',
       'kick_off_hour', 'is_holiday', 'is_weekend', 'media', 'nhk', 'G大阪',
       '甲府', 'FC東京', '磐田', '名古屋', '大宮', '川崎F', '広島', '横浜FM', '浦和', '千葉', '新潟',
       '清水', '鹿島', '京都', '福岡', '大分', 'C大阪', '柏', '横浜FC', '神戸', '札幌', '東京V',
       '山形', '湘南', '仙台', '鳥栖', '徳島', '松本', 'Ｃ大阪', 'Ｇ大阪', '川崎Ｆ', '長崎',
       'weather_encoded','discomfort'
Target：'attendance'

**まとめ**
本コンペの難点はoverfittingだと考える。また、データの使用はかなり制限されているので、人口などのデータが使われなかった。lightGBM、xgboostとのensemble modelを作るのも今後の改善点だと考えている。
