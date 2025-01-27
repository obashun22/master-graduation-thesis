# スマートフォンを用いたローイング競技向け衝突防止システム

## 第 1 章 序論

### 1.1 研究背景

#### ローイング競技とその現状

##### ローイング競技の概要

ローイング競技（以下、ローイング）とは、オールを用いてボートを漕ぎ進め、その着順を競う水上スポーツである。
2000m の直線コースを個人またはチームで漕ぎ進める。筋力や持久力に加え、チーム全体の動作に統一感が求められるスポーツである。

ローイングに使用されるボートは艇と呼ばれ、乗員人数等によって幾つかの艇の種類（以降、艇種）に分かれている。
いずれの艇種も細長い形状であり、乗組員（以降、クルー）は縦並びに座る形で乗艇する。進行方向に対して背中を向けて漕ぐという点が大きな特徴である。\*

<!-- MEMO: 詳細は第2章の前提知識で述べればいいかも -->
<!-- IMG: 競技中の艇の様子／4x -->

##### 艇種

クルーは、漕手と舵手から構成される。漕手は艇を漕ぎ進める役割を担い、舵手は操舵や艇全体に対して動作の指示を行う役割を担う。漕手のみから構成される艇種も存在する。

ローイングで使用される艇は、漕手の人数や舵手の有無、オールの種類によって種類が分かれる。
漕手の人数は艇種によって 1 人、2 人、4 人あるいは 8 人で構成される。\*
それに加えて、舵手が 1 人加わる場合がある。\*
オールの種類はスカルとスイープの 2 種類あり、スカルは 左右の手それぞれで 1 本ずつオールを持ち、スイープは両手で 1 本のオールを持つ。\*

<!-- IMG: 漕手人数がわかる写真 -->
<!-- IMG: 舵手がわかる写真 -->
<!-- IMG: オールの種類がわかる画像 -->

漕手の人数と舵手の有無、オールの種類の組み合わせにより、艇は次のように分類される。

| 艇種                 | 艇種記号 | 漕手人数 | 舵手人数 | オールの種類 |
| -------------------- | -------- | -------- | -------- | ------------ |
| シングルスカル       | 1x       | 1        | 0        | スカル       |
| ダブルスカル         | 2x       | 2        | 0        | スカル       |
| ペア                 | 2-       | 2        | 0        | スイープ     |
| クォドルプル         | 4x       | 4        | 0        | スカル       |
| 舵手付きクォドルプル | 4x+      | 4        | 1        | スカル       |
| フォア               | 4-       | 4        | 0        | スイープ     |
| 舵手付きフォア       | 4+       | 4        | 1        | スイープ     |
| エイト               | 8+       | 8        | 1        | スイープ     |

##### 競技環境

ローイングの競技環境としては、ローイング専用に設けられた漕艇場の他に、河川や湖、池などの自然の水域が用いられることが多い。水域に直線状のコースを設けて片側航行で往復して使用することが多い。

<!-- IMG: 競技環境の例 -->

##### 漕艇動作

艇を漕ぐ上での基本動作には次のようなものがある。

- 前進: オールを使って艇を漕ぎ進め前進させる。
- 停止: オールを水中に入れて水の抵抗力で停止させる。
- 静止: 水面にブレード（オールの先端部分）を水平に置く形でバランスをとり静止させる。
- 旋回: 片側のオールを強く漕ぎ、もう片側のオールを弱く漕ぐことで旋回させる。

<!-- IMG: 漕艇動作の例 -->

##### ローイング競技の現状

昨今、スポーツにおける安全管理に関心が集まっている。ローイングにおいても安全管理の重要性が認識され、[ガイドライン策定](日ボ安全マニュアル)や競技者の安全意識向上のための教育などが行われている。

しかしながら、ローイングにおける事故は依然として発生している。英国のローイング統括団体である British Rowing が公開している統計データ「Analysis of Incidents Reported in 2022」によると、
2022 年の英国内での年間事故数は 1434 件発生しており、そのうち 827 件が衝突事故となっており約 58%を占めている。\*
衝突事故の衝突対象としては、他艇が 57%、土手・堰・桟橋・植物等が 30% である。\*
事故の主な原因として、[前方不注意、および航行ルールの不遵守](Analysis of Incidents Reported in 2022 の該当行)が挙げられている。

<!-- IMG: 事故件数の推移 -->
<!-- IMG: 事故の衝突対象割合 -->

このうち前方不注意については、後方を向いて漕ぐ特性により、常に前方の状況を把握するのが難しいことが前方不注意に繋がっていると考えられる。
また、乗艇時は視点が低くなり周囲の物体との距離が掴みづらくなることも前方不注意が発生する原因として考えられる。
これらに加えて、天候や日照による視界への影響や風や水流による航路への影響も前方不注意が発生する原因として考えられる。

こうした状況から、人の目による物体認識のみでは衝突事故を十分に防ぐことは難しいと考えられる。
人の目視による認識だけでなく、デジタル技術による物体認識を活用した衝突防止策の導入が必要とされている。

<!-- MEMO: 既存の衝突防止策の課題を簡単に挙げておくか？ -->

### 1.2 研究目的

上述の背景を踏まえ、デジタル技術を活用したローイング競技向け衝突防止システムを開発し、競技の安全性を向上させたいと考えた。

そこで本研究では、低コストなローイング競技向け衝突防止システムを開発し、競技の安全性を向上させることを目的とする。
具体的には、スマートフォンを用いて、他艇および静的障害物の接近を警告する衝突防止システムを開発し、競技の安全性を向上させる。

<!-- MEMO: 安全性向上より具体的に衝突防止と言ったほうがいいかもしれない -->

本研究の貢献は次の通りである。

<!-- TODO: 貢献はどの程度まで貢献とするか要検討 -->
<!-- MEMO: 他の研究を参考にして貢献を挙げる -->

- ローイング競技特有の安全管理上の課題を明らかにした
- ローイング競技向けの既存の衝突防止システムを調査した
  - 海洋船舶向けのスマートフォンを用いた衝突防止システムを調査し、ローイング競技に適用する場合の課題を明らかにした
- スマートフォンを用いたローイング競技向け衝突防止システムを提案・実現した
  - ローイングの特性を踏まえた衝突防止システムの提案を行った
  - 提案システムを実際に実装し、その有用性を検証した
- ローイング環境における基礎的な計測データを提供した
  - ローイング環境におけるスマートフォンの測位精度を計測し、参考値を提供した
  - 艇種ごとの停止距離を計測し、艇速と停止距離の関係を求めた
- 実装したシステムの評価を通じて実用化に向けた知見を得た
  - システムを実現する上での課題を明らかにし、後の研究に示唆を与えた
- 実装したシステムのソースコードを公開した

### 1.3 本論文の構成

本論文は、全 5 章で構成される。
第 2 章では、ローイングに関する前提知識と現状の衝突防止策について述べた後、本研究に関連の深い既存の事故防止システムを示した上で既存システムの課題について議論する。
第 3 章では、提案システムの要件を整理した上で、設計について述べる。続いて、予備実験について述べた後、提案システムの実装に関して、使用技術や実装上の工夫を詳解する。
第 4 章では、提案システムの機能と性能、および安全性・コスト・使用性・拡張性について評価し、考察する。
第 5 章では、本研究のまとめと今後の課題を述べる。

## 第 2 章 前提知識・既存システム

<!-- INSERT: ローイング競技の基礎知識 -->

### 2.1 現状の衝突防止策

ローイングにおいて現在とられている衝突防止策として、一定時間またはストローク（オールの回転数）間隔で進行方向の確認を行う、他艇の接近に気付いたら声を掛ける、水域ごとに航行ルールを定める、陸やモーターボートから監視するといった対策がなされている。
水域ごとに航行ルールを定める対策では、航行経路、レーンの利用規則、視界不良時のライト点灯などのルールが定められている。\*

これらの対策を徹底することで、ある程度の安全は確保できると考えられる。
一方で、いずれの対策にも課題がある。

一定時間またはストローク間隔で進行方向の確認を行う対策では、後方確認の失念や目測の誤り、確認動作による練習の質の低下が問題となっている。他艇の接近に気づいたら声をかける対策では、声に気づけない場合があることが課題となっている。また、水域ごとに航行ルールを定める対策では、航行ルールの不理解や失念、不遵守が課題となっている。また、陸やモーターボートから監視する対策では、監視が難しい環境や条件では監視ができないという課題がある。

<!-- IMG: 航行ルールの掲示板 -->

### 2.2 既存のローイング競技向け衝突防止システム

既存のローイング競技向け衝突防止システムとして、Rowcus が挙げられる。
Rowcus は LiDAR を搭載した組み込みデバイスを艇の船首に装着し、艇の前方にある障害物を検知し、衝突の可能性がある場合に音声により回避方向を指示するシステムである。音声による回避方向の指示は「right」「left」で行われ、漕手は直感的に避けるべき方向を理解できる。使用にあたり Bluetooth によるペアリングや配線等は不要で、USB で充電可能である。

<!-- IMG: Rowcus の画像引用 -->

Rowcus の利点として、未知の障害物に対して警告を発することができること、視界不良時でも警告を発することができること、音声で回避方向がわかること、他艇へシステムを搭載せずとも使用可能であることが挙げられる。

一方、Rowcus の課題として、LiDAR を搭載した専用のデバイスが必要であり金銭的なコストが高いこと、前方方向の衝突しか警告できないこと、水中障害物に対して警告を発することができないことが挙げられる。
Rowcus で用いられている LiDAR は数万円程度の高価なモジュールであり、これを搭載した専用のデバイスを全ての艇の船首に装着することは金銭的なコストの面から容易ではない。
また、Rowcus は前方からの接近のみを検知する仕組みとなっているため、横方向や後方から接近してくる艇や障害物に対しては警告を発することができないという課題もある。
加えて、水中障害物に対して警告を発することができないことも課題となっている。Rowcus は LiDAR を用いて前方の障害物を検知する仕組みとなっているため、水中にある浅瀬や岩、杭などの障害物を検知することは困難である。

### 2.3 スマートフォンを用いた船舶向け事故防止システム

スマートフォンを用いた船舶向け事故防止システムとして、[SmartAIS](https://www.mlit.go.jp/common/001141266.pdf) が挙げられる。\*

SmartAIS はスマートフォンの位置情報と AIS を連携させ、船舶間で位置情報を共有し、他船や障害物の接近を検知して警告するシステムである。
AIS（船舶自動識別装置）とは、船舶の位置、速度、進行方向などの航行情報を VHF 帯の電波を用いて送受信し船舶間で共有するシステムである。AIS を搭載する船舶は、自身の航行情報を定期的に送信し、周辺船舶の情報を受信することで、船舶間の位置関係を把握し、衝突防止に役立てている。AIS は国際海事機関（IMO）により、国際航海に従事する 300 総トン以上の全ての船舶、および国内航海に従事する 500 総トン以上の全ての船舶への搭載が義務付けられている。
AIS は数万円から数十万円程度する高価な機器である。そのため、AIS の搭載義務のない小型船舶の場合は導入費用が大きな障壁となり搭載していないことが多い。そこで SmartAIS では、スマートフォンを AIS と連携させることで小型船舶でも安価に AIS 情報を利用して衝突防止を行えるようにしている。

<!-- IMG: SmartAIS の画像引用 -->

SmartAIS はスマートフォンのアプリとして実装されており、共有される位置情報はスマートフォンの GPS を用いて取得される。
SmartAIS の基本機能として、海上情報図の表示、危険検知および警告、緊急通報、船舶間通信、航行ログの記録がある。
海上情報図の表示では、地図上に現在地や他船を表示し、他船との位置関係を把握できるようにしている。
危険検知および警告では、他船が警戒範囲内に侵入した場合や、浅瀬に侵入した場合に警告を発する。警告は警告文の表示とスマートフォンのアラーム、バイブレーションにより行われる。
緊急通報では、GPS 情報がサーバーに一定時間送信されていない場合に、その船舶に緊急事態が発生していると判断して、周辺の船舶や指定された連絡先に緊急事態のメッセージと GPS 情報を送信する。
船舶間通信では、指定した送信範囲内の船舶とメッセージのやり取りを行うことができる。
航行ログの記録では、収集された船舶、気象、潮汐、波浪といった情報を記録し、オープンデータとして公開する。これにより将来、統計による海上事故の予測などに役立てることができる。

SmartAIS では、他船が衝突回避エリアに侵入した場合に警告を発する。
衝突回避エリアは危険エリアと注意エリアの 2 つのエリアに分かれており、それぞれのエリアに他船が侵入した場合に警告を発するようになっている。\*
危険エリアは自船の全長を L として、左右後方 4L、前方 12L を設定している。
注意エリアは周囲 3km×3km を設定している。

<!-- IMG: 注意エリアと危険エリアの画像引用 -->

SmartAIS の利点として、AIS と連携しているため、AIS を利用している船舶との衝突防止が可能であること、安価であり身近なデバイスであるスマートフォンを使用しておりコストが低いことが挙げられる。

また、SmartAIS をローイングに適用する場合の課題として、小さなスケールの障害物との衝突を考慮していないこと、警告条件が船速を考慮したものでないことが挙げられる。
SmartAIS は海上を航行する小型船舶に向けた衝突防止システムであり、浅瀬への侵入は警告が行われるものの、橋脚や杭、消波ブロックといった小さな障害物の接近については警告が行われない。
また、SmartAIS の警告条件では船速を考慮していない。SmartAIS では、固定長の 2 つのエリアに他艇が侵入した場合にそれぞれ警告を発するようになっている。海上の場合、十分に広いエリアを設定しても、水域が広大なため過剰な警告が発生することは考えにくい。一方、ローイングの場合、十分に広いエリアを設定してしまうと、水域が狭いため対象物と十分な距離を置くことができず過剰な警告が発生してしまう。また、エリアの範囲を小さくすると船速によっては警告後の衝突回避に必要な距離を確保できない可能性がある。そのため、ローイングの競技環境においては、エリアの範囲を適度な大きさにするとともに艇速が速い場合は早めに警告を行い、艇速が遅い場合は遅めに警告するといった工夫が必要となる。

## 第 3 章 提案システム

### 3.1 システム概要

上述の既存システムの課題を踏まえ、ローイング競技向け衝突防止システムを提案する。
本研究で提案するシステムは、スマートフォンを用いて他艇および既知の静的障害物の接近を警告するというものである。
専用アプリをインストールしたスマートフォンを各艇に搭載し、艇の位置・速度・針路といった航行情報を取得して他艇と共有し、自艇に他艇または静的障害物が接近した場合に音声による警告を行う。静的障害物については、その位置を予めシステムに登録しておき、接近した場合に警告を行う。

### 3.2 システム要件

本システムの要件は以下の通りとした。

- 他艇および既知の静的障害物の接近を警告できること
- システムの導入コストが安価であること
- 練習の質を低下させないこと
- 拡張性があること

本システムでは、衝突防止の対象を他艇および既知の静的障害物とした。ローイングでは、他艇との衝突に加え、障害物との衝突が多く発生している。障害物は、橋脚や消波ブロック、ブイなどの位置が変わらない静的障害物と、漂流物などの位置が変わる動的障害物に分けられる。静的障害物は、位置が変わらないためその存在を予め把握することが容易であり、水中に存在する場合でも経験的にその存在が把握されている場合が多い。一方で、動的障害物は主に流木やゴミなどの漂流物であり、その存在を予め把握することは難しい。そのため、本システムでは、事前に存在を把握することが可能な静的障害物のみを衝突防止の対象とした。
また、システムの導入コストを抑えることを要件とした。Rowcus を用いた場合、数万円から数十万円程度の高価なデバイスを搭載する必要があるが、一般のローイングの競技者や競技団体にとって、このような高価なデバイスの導入は容易ではない。特に、競技団体全体での導入を考えた場合、一艇につき一台を導入する必要があるため、その費用は大きな負担となってしまう。そのため、本システムでは導入コストを抑えることで、より導入しやすいシステムとなることを目指した。
衝突防止システムによって練習の質を低下させないことも重要な要件である。過度な操作を必要としたり過剰に警告が行われると、ローイングの練習の質が低下してしまうため避けなければならない。
また、拡張性についても要件とした。衝突防止の他にローイングの安全性を高めるための機能として救助要請機能や航行ログ機能などが考えられる。航行ログ機能は事故時の状況把握・分析や練習状況の記録・分析に活用できる。そこで、本システムでは将来的にこうした機能を追加できるよう拡張性を要件に加えた。

本システムは、ローイングの練習中の使用のみを想定し、試合中の使用は考慮しない。また、水域は漕艇場の他、河川や湖、池などの自然の水域も想定する。また、衝突防止の対象となるものは他艇と既知の静的障害物とし、モーターボートなどの競技艇以外の船舶や漂流物などの動的障害物は衝突防止の対象としないものとする。

### 3.3 システム設計

#### 3.3.1 スマートフォンの活用

車両や船舶の衝突防止システムに用いられるセンシング技術として、カメラ、レーダー、GPS、超音波センサー、ミリ波レーダー、BLE、加速度センサー、地磁気センサーといったものが挙げられる。一般的なスマートフォンは、これらの技術のうち GPS、BLE、加速度センサー、地磁気センサーを標準的に搭載しており、衝突防止システムのセンサとして適している。加えて、スマートフォンは通信機器・データ処理・警報機としても利用可能である。インターネット接続により、将来的な機能追加や拡張が容易である。また、現在スマートフォンは広く普及しているため、個人が所有するスマートフォンを利用することで導入コストを抑えることができる。
以上の利点から、本システムではスマートフォンを用いることとした。

#### 3.3.2 設計

##### 全体設計

上述の要件を踏まえて、スマートフォンを用いた衝突防止システムを設計する。
専用アプリをインストールしたスマートフォンを各艇に搭載し、艇の位置・速度・針路といった航行情報を取得して他艇と共有し、自艇に他艇または静的障害物が接近した場合に音声による警告を行う。静的障害物については、その位置を予めシステムに登録しておき、接近した場合に警告を行う。各艇が 1 台のスマートフォンを搭載するものとする。スマートフォンは漕手の足を固定するストレッチャーの下、あるいは COX シートの床面に設置するものとする。本システムはスマートフォンのネイティブアプリとして提供される。アプリには 2 つのモードがあり、水域情報を表示するオブザーバーモードと、自艇の艇情報を共有し衝突警告を行うナビゲーションモードがある。

##### 機能

###### 水域情報の表示

オブザーバーモードでは、水域マップおよび航行中の艇を画面上に表示する。水域マップは、地図情報に静的障害物の存在する領域（以降、障害物領域と呼ぶ）を重ね合わせたものである。この水域マップ上に航行中の艇のマーカーを重ね合わせて表示する。艇のマーカーは、艇の位置と針路を表す。
航行中の艇の艇情報は、サーバーを介して一定の時間間隔で共有される。艇情報には、位置、速度、針路、艇種、識別子、タイムスタンプが含まれる。航行中の艇に搭載されたスマートフォンは、スマートフォンのセンサーから位置、速度、針路を取得し、艇種、識別子、タイムスタンプを含めて艇情報をサーバーへ送信する。同時に、サーバーから他艇の艇情報を取得する。
艇の位置は、スマートフォンの GNSS センサから得られる地理座標を用いる。艇の速度については、スマートフォンの GNSS センサから得られる地理座標から算出される速度を用いる。艇の針路については、スマートフォンの地磁気センサから得られる方位角を用いる。
針路としてスマートフォンの地磁気センサから得られる方位角を用いるため、スマートフォンを艇に搭載する際にスマートフォンの姿勢を定める必要がある。本システムでは、スマートフォンを画面上向きで、端末上部を艇首方向に向けて平置きするものとする。
艇の位置について、センサから取得した地理座標をそのまま艇の中心位置として扱うと、スマートフォンを設置するシートの位置によっては実際の艇の中心位置との間に大きな誤差が生じる。最も全長が長い艇種である 8+では、COX シート にスマートフォンを設置した場合、実際の艇の中心位置から約 5m 程度の誤差が生じる。そのため、艇の位置については、スマートフォンの設置先のシート位置を考慮して地理座標の補正を行い、艇の位置を求める。

###### 水域マップの編集

水域マップを編集するための機能を提供する。水域マップは地図情報に障害物領域を重ね合わせたものである。障害物領域は静的障害物の存在する領域を表しており、二次元の多角形で表現される。ユーザーは障害物領域を登録および削除することができる。登録された障害物領域の情報はサーバーに保存され、他のスマートフォンに共有される。

###### 衝突警告

他艇や静的障害物について衝突警告を行う場合、ナビゲーションモードを開始する。ナビゲーションモードでは、自艇の艇情報を一定間隔でサーバーへ送信すると共に、自艇に他艇または静的障害物が接近した場合、音声による警告を行う。警告を行うかどうかは後述の警告条件に基づいて判定する。警告音は断続的なビープ音とし、衝突の危険性に応じて 2 段階の警告音とする。障害物領域については、練習前にあらかじめ水域マップに登録するものとする。また、ナビゲーションモードへ切り替える際に、艇種とシート位置を設定する。

##### システム構成

本システムは、専用アプリとサーバー・DB から構成される。専用アプリは、水域情報の表示や水域マップの編集、衝突警告の機能を提供する。サーバー・DB は、艇情報や水域マップの情報を保持する。

<!-- IMG: システム構成図 -->
<!-- MEMO: パワポから引用 -->

##### シーケンス図

本システムの主要な処理フローを示すシーケンス図を示す。本システムは、クルー、専用アプリ、サーバー、DB の 4 つのアクターで構成される。

システムの処理フローは大きく 5 つのフェーズに分かれる。
アプリ起動フェーズでは、クルーがアプリを起動すると、アプリはサーバーを介して DB から水域マップ情報を取得し、水域情報画面を表示する。
水域マップ編集フェーズでは、クルーが水域マップの編集を開始すると、アプリは編集画面を表示する。クルーが障害物領域の登録・削除を行うと、その情報がサーバーを介して DB に保存される。
ナビゲーション開始フェーズでは、クルーがナビゲーションを開始すると、アプリは艇情報入力画面を表示する。クルーが艇種とシート位置を入力することで、ナビゲーションが開始される。
航行中の艇情報共有フェーズでは、定期的な情報更新のループが実行される。アプリはセンサーデータを取得し、艇情報をサーバーへ送信する。同時に他艇の情報をサーバーから取得し、警告の有無を判定する。
警告フェーズでは、警告条件を満たした場合にクルーへ警告音を再生する。

このように、本システムは艇情報の定期的な共有と警告判定を繰り返し実行することで、衝突防止を実現する。

<!-- IMG: シーケンス図 -->
<!-- @startuml
title 主要処理シーケンス

actor クルー as crew
participant "専用アプリ" as app
participant "サーバー" as server
database "DB" as db

== アプリ起動 ==
crew -> app: アプリ起動
app -> server: 水域マップ情報要求
server -> db: 水域マップ情報取得
db -> server: 水域マップ情報送信
server -> app: 水域マップ情報送信
app -> crew: 水域情報画面

== 水域マップ編集 ==
crew -> app: 水域マップの編集開始
app -> crew: 水域マップ編集画面
crew -> app: 障害物領域の登録・削除
app -> server: 水域マップ情報送信
server -> db: 水域マップ情報保存

== ナビゲーション開始 ==
crew -> app: ナビゲーション開始
app -> crew: 艇情報入力画面表示
crew -> app: 艇種・シート位置入力
activate server

== 航行中の艇情報共有 ==
loop 定期的な情報更新
    app -> app: センサーデータ取得
    app -> server: 艇情報送信
    server -> db: 艇情報保存
    app -> server: 他艇情報要求
    server -> db: 他艇情報取得
    db -> server: 他艇情報送信
    server -> app: 他艇情報送信
    app -> app: 警告の有無判定
end

== 警告時 ==
alt 警告有り
    app -> crew: 警告音再生
end

@enduml
-->

##### 警告条件

- 衝突警告アルゴリズム
  - 概要
    - 警告を発するか否かの判定を行うアルゴリズム
    - 衝突の危険性が高い場合に警告を発する
    - 衝突対象は他艇と障害物
  - コンセプト
    - 艇の一定の周辺領域に他艇あるいは障害物が侵入した場合に警告を発する
    - 艇速を考慮して警告を発するタイミングを調整する
      - 艇速が速い場合は早めに警告する
      - 艇速が遅い場合は遅めに警告する
      - 固定領域の欠点 // 領域について別で述べるなら不要
    - 段階的に警告を発する
  - アルゴリズム
    - 領域
      - アルゴリズムを記述する上で必要な領域を定義する
      - 3 つの領域を定義する
        - 船体領域
          - 艇のオールを含めた船体が占める領域
        - 排他領域
          - 静止状態の艇が他艇や障害物を避けるために必要な領域
        - 障害物領域
          - 障害物が占める領域
    - アルゴリズム // もうちょっと整理したい
      - 前提
        - 自艇は現在の進路を維持すると仮定する
        - 他艇は現在の速度と進路を維持すると仮定する
      - 手順
        - 現在の時刻を 0、自艇の速度を v、他艇の速度を u とする
        - 停止距離を SD、注意距離を AD=SD+v\*AT とする
        - AT は停止距離に差し掛かるまでの猶予時間
        - 自艇が現在の速度と進路を維持すると仮定して、他艇の船舶領域が自艇の排他領域に侵入するか否かを判定する
        - 侵入する場合はその時刻を t、衝突までの距離を CD とする
        - 警告条件
          - SD < CD <= AD: 注意の警告を発する
          - CD <= SD: 停止の警告を発する
        - この警告条件に従い警告するか否かを判定
        - 注目する艇を自艇と他艇の 2 艇に分けて、それぞれの艇に対して衝突警告アルゴリズムを実行する
  - 既存の衝突警告判定手法 // 掲載するか否か悩む
    - 固定領域
      - 固定の領域を設定し、その領域に他艇あるいは障害物が侵入した場合に警告を発する
      - 避航や停止などの衝突回避を行うのに十分余裕のある領域幅を設定する
      - 海上船舶など、水域が十分に広く船舶同士の接近が稀であるような場合に有効
      - しかし、ローイングは比較的狭い水域で競技を行うため、艇同士あるいは艇と障害物との接近がある程度許容されなければならない
    - 動的領域
      - 艇の速度を考慮して領域を設定し、その領域に他艇あるいは障害物が侵入した場合に警告を発する
      - CPA（Closest Point of Approach：最接近点）に触れるか否か...
      - ...

### 3.4 予備実験 // 一旦書かない

#### 3.4.1 停止距離計測

- 実験概要

  - 衝突警告アルゴリズムを実装するにあたり、艇速と停止距離の関係を把握する必要がある
    - 停止距離とは、空走距離と制動距離を足した距離
    - 求めた関係式を用いることで艇速に応じた停止距離を計算できる
  - 本実験では艇種毎の艇速と停止距離の関係式を求める
  - 艇速を 4 段階に分けてそれぞれ 5 回ずつ停止距離を計測し、関係式のフィッティングを行う

- 実験目的

  - 艇種毎の艇速と停止距離の関係式を求める

- 実験方法

  - 艇を一定の艇速で航行させ、警告音を鳴らしてから艇が停止するまでの距離を計測する
  - 艇速を 4 段階に分け、それぞれ 5 回ずつ計測を行う
  - 全ての計測を行ったのち、全計測データを用いて関係式のフィッティングを行い艇速と停止距離の関係式を求める

  - 停止距離の計測
    - 停止距離の計測方法
      - 高精度測位装置 Ichimill を用いて常時艇の位置を計測し、警告を出した地点から艇が停止した地点までの直線距離を停止距離として計測する
      - 水流による影響は考慮しない
      - Ichimill について
        - 概要
        - 測位方法の概説
    - 警告の出し方
      - 艇に警告音を鳴らすための端末を搭載
      - 艇外から任意の時点で警告音を鳴らす
      - IP 通話で警告音の音声を送信
      - 通信遅延は考慮しない
      - 警告音はビープ音
      - 警告を行った時刻を警告時刻として記録
    - 停止動作
      - 警告音を認識した漕手が艇を停止させる
      - 抵抗の掛け方はブレードを水面に水平に水中に入れる方法で統一
    - 実験手順
      - 高精度位置情報の取得を開始
      - 一定の艇速で艇を直進させる
      - 警告音を鳴らす
      - 警告音が鳴ったら艇を停止させる
      - 警告地点から停止距離までの直線距離を停止距離として記録
      - 以上を計 5 回繰り返す
      - 艇速を変えて繰り返す
      - 以上の計測を艇種ごとに行う
  - 計測する艇種
    - 艇種は 1x, 2x, 4x, 8+の 4 種類
    - 漕手は名古屋大学漕艇部に所属する漕手経験者
  - 艇速の決定
    - 目安とする艇速は、計測の前に最高艇速を計測し、その艇速以下で 4 段階に分けて計測を行う

- 実験結果

  - 艇速

    - 計測前に最高艇速を計測し、その艇速を上限の艇速として艇種ごとに以下の 4 段階に分けて計測を行った

    | 艇種 | 艇速 1 | 艇速 2 | 艇速 3 | 艇速 4 |
    | ---- | ------ | ------ | ------ | ------ |
    | 1x   | 3:00   | 2:40   | 2:20   | 2:00   |
    | 2x   | 2:40   | 2:20   | 2:00   | 1:40   |
    | 4x   | 2:40   | 2:20   | 2:00   | 1:50   |
    | 8+   | 2:40   | 2:25   | 2:10   | 2:00   |

  - 艇速と停止距離をプロット
    - 警告時刻は警告音を鳴らした時刻
    - 変化量が 1m 以下となったら停止と判断
    - Speed vs. Stopping Distance for Various Boat Types (Adjusted Axes)のグラフ掲載

- 考察

  - 結果について

    - 艇速が大きくなると停止距離が大きくなる傾向
      - 明らかである
      - 8+の例外について
        - なぜ単調増加でないか
        - 以下のような複合的な要因の影響で期待される大小関係に対して結果が逆転したと考えられる
          - 警告のタイミング
            - 漕ぎ動作の中のどのタイミングで警告が発せられるかで停止動作をとるまでの時間が大きく変わる
          - 風や水流などの要因
        - 計測回数を増やすことで単調増加するより正確な結果が得られると考えられる
    - 艇種による停止距離の違い
      - 実際には 1x の停止距離が 2x の停止距離よりも大きいという結果が得られた
      - 艇あるいは艇種によって、艇の重量や形状、オールの種類、漕手の技量などが異なり、船体やオールにかかる抵抗力、安定性に違いが生まれるため一概に艇の総重量の大きい艇種の停止距離が大きいとは言えない
      - 小艇が大艇よりも停止距離が大きい可能性があることを示唆している
      - より条件を揃えることで艇種の違いによる停止距離の違いをより正確に把握することができる
    - 計測した範囲の中では直線的な艇速と停止距離の関係が見て取れる

  - 艇と艇速の関係式を求める

    - 直線的な関係が見て取れる
    - 当初は対数関数を用いてフィッティングを行う予定だったが、得られたデータについて一次関数の方が適合したため、一次関数を用いてフィッティングを行った
    - フィッティングする関数
      - 関数は原点を通す
        - 艇速が 0 の時は停止距離も 0 であるため
      - 原点を通る対数関数
        - 最小二乗法でフィッティング
      - 原点を通る一次関数
        - 最小二乗法でフィッティング
        - 式は d = (Tp+Td+Tr)*V + A*V
        - Tp: 認識時間
        - Td: 判断時間
        - Tr: 反応時間
        - A: 定数
        - Td は本実験では判断する必要がないことから Td=0 である
        - また、Tp, Tr は経験的に Tp=0.5、Tr=1.0 とした
      - 対数関数と一次関数のフィッティング結果の比較
        - 一次関数の方が適合した
        - なぜか？
          - 似たようなモデルで考えると対数関数の関係になると考えられたが実際は直線的な関係になった
          - モデルでは考慮できていなかった要素、オールの抵抗の影響が大きく対数関数より一次関数の方が適合する結果となった？
    - 一時関数でフィッティングした結果

      - Linear Model Fit/ d = (Tp+Tr)*V + A*V (Tp=0.5, Tr=1.0)のグラフ
      - 艇種毎のフィッティング結果

        | 艇種 | フィッティング結果               |
        | ---- | -------------------------------- |
        | 1x   | d = (0.5 + 1.0)V + 3.45V = 4.95V |
        | 2x   | d = (0.5 + 1.0)V + 3.10V = 4.60V |
        | 4x   | d = (0.5 + 1.0)V + 3.18V = 4.68V |
        | 8+   | d = (0.5 + 1.0)V + 4.65V = 6.15V |

  - フィッティング結果の補正

    - 本実験では警告音が鳴った時点で即時停止動作を行なっているが、実際の状況では警告音を認識してから停止動作を行うまでに停止動作を行うかどうかを判断するための時間が必要である
    - その時間を停止距離に加算することでより正確な停止距離を求めることができると考えられる
    - 本研究では判断時間を 2.0 秒として停止距離に加算した
    - 補正後のフィッティング結果は以下の通り

      | 艇種 | フィッティング結果                     |
      | ---- | -------------------------------------- |
      | 1x   | d = (0.5 + 2.0 + 1.0)V + 3.45V = 6.95V |
      | 2x   | d = (0.5 + 2.0 + 1.0)V + 3.10V = 6.60V |
      | 4x   | d = (0.5 + 2.0 + 1.0)V + 3.18V = 6.68V |
      | 8+   | d = (0.5 + 2.0 + 1.0)V + 4.65V = 8.15V |

#### 3.4.2 測位精度計測

- 実験概要

  - スマートフォンの測位には誤差が含まれる
  - より安全な衝突防止システムとするには測位誤差に耐性を持たせる必要がある
  - 測位誤差に耐性を持たせるためのアルゴリズムを提案する上で、その誤差がどの程度であるかを知ることは重要
  - 当実験ではローイングの環境においてスマートフォンの測位誤差がどの程度であるかを計測する
  - 得られた誤差は一つの目安の誤差として、システムに誤差耐性を持たせる際に参考にする
  - 現段階では測位誤差の影響を吸収するようなアルゴリズムを実装できていないことに注意したい

- 実験目的

  - ローイングの水域においてスマートフォンでどの程度の測位精度が得られるのかを計測し、（今後の研究において）システムにどの程度誤差耐性を持たせるべきかを考える際の目安値を得ることが目的
  - 現段階では測位誤差の影響を吸収するようなアルゴリズムを実装できていないことに注意したい

- 実験方法
  - 誤差の計測方法
    - 高精度測位装置 Ichimill で得られた地理座標を真値として、スマートフォンで得られた地理座標の誤差を計測する
  - 静止時の測位誤差
    - スマートフォンを静止させて測位精度を計測する
    - 完全な静止が難しいため、水域付近の河岸にスマートフォンを固定して測位精度を計測する
  - 移動時の測位誤差
    - スマートフォンを艇に搭載し、艇を水域内で航行させて測位精度を計測する
- 実験結果
  - 静止時の測位誤差
    - 統計情報
    - プロット
  - 移動時の測位誤差
    - 統計情報
    - プロット
- 考察
  - ローイングの環境においてスマートフォンで測位を行うと N m の誤差が含まれることが明らかになった
    - センサ性能や周囲の立体物、気象条件、衛星の位置などの要因が誤差に影響しているため一概にこの程度の誤差になるとは言えない
    - あくまで目安値に留まることに注意したい
  - 移動時の誤差が大きくなったのは処理遅延あるいは時刻が同期していないことが原因であると考えられる
    - 処理遅延
      - 地理情報の取得には時間がかかるため、すでに取得した地理情報を用いる仕様になっている
      - これにより時間誤差が生じていると考えられる
    - 時刻の同期
      - 時刻の同期が正確でない可能性
      - 本体の時刻がズレることで衛星電波を解析する際に位置情報に誤差が生じる
    - どっちも実際にシステムを使用する際に時間差の原因として生じ得る
    - 時刻同期は自動で行われるので、処理遅延もあるかもだけどどのみち時刻の同期誤差と処理遅延が生じて誤差が生じると考えられる

### 3.5 実装

本システムの有効性を評価するため、システムの実装を行なった。その詳細を以下に述べる。

#### 3.5.1 使用技術

本システムを実装するにあたり、以下の技術を使用した。\*
本実装では、Android および iOS のスマートフォンを動作対象とした。開発効率を高めるため、クロスプラットフォームフレームワークの Flutter を採用した。Flutter は、Google が開発したオープンソースの UI フレームワークで、単一のコードベースから Android と iOS の両プラットフォーム向けにネイティブアプリケーションをビルドできる。また、豊富なウィジェットライブラリが提供されており、これらの利点により、本システムの開発における生産性と品質の向上が期待できる。\*
また、サーバ・DB として Firestore を採用した。Firestore は Google が提供するクラウドベースの NoSQL データベースで、リアルタイムデータ同期、オフラインサポート、自動スケーリングなどの機能を備えている。\*本システムでは、艇情報のリアルタイム共有や障害物領域の永続化が必要となるが、Firestore のリアルタイムデータ同期機能により、これらの要件を容易に実現できる。また、モバイルアプリケーション向けに最適化されており、Flutter との親和性が高いことも採用の理由である。

| 項目                 | 使用技術         |
| -------------------- | ---------------- |
| フレームワーク       | Flutter (3.7.12) |
| 言語                 | Dart (2.19.6)    |
| サーバ・データベース | Firestore        |
| 地理情報 API         | GoogleMaps API   |

#### 3.5.2 アプリケーション

##### 画面実装

本実装では、水域情報画面、水域マップ編集画面、艇情報設定画面、ナビゲーション画面の 4 つの画面を実装した。

水域情報画面では、水域情報を表示する。具体的には、水域マップに航行中の艇のマーカーを重ね合わせたものを表示する。艇のマーカーは二等辺三角形の図形とし、頂角を艇の進行方向に向けて表示する。また、水域マップに設定された障害物領域を、赤色の多角形で表示する。
ナビゲーションの開始ボタンを画面下部中央に配置し、アプリケーション起動後、煩雑な操作を行わずに直ぐにナビゲーションを開始できるようにしている。
水域情報は地図表示と航空写真表示を切り替えることができ、画面左下のボタンで表示モードを選択できる。
水域マップ編集画面に遷移するためのボタンは画面右側に配置した。

水域マップ編集画面では、現在登録されている障害物領域を表示するとともに、障害物領域の編集機能を提供する。障害物領域を登録する際は、画面右下の追加ボタンを押してから、指で領域を描くことで登録することができる。障害物領域を削除する場合は、表示されている障害物領域をタップすることで削除することができる。
水域マップ編集画面ではデフォルトの表示モードを航空写真表示としている。航空写真上に領域を描くことで、障害物領域の登録を正確に行うことができる。

艇情報設定画面では、ナビゲーション開始前に艇種およびシート位置を設定する機能を提供する。本実装では、艇種として 1x, 2x, 4x, 8+を用意し、シート位置は艇種に応じたシートを選択可能とした。

ナビゲーション画面では、自艇を含めた水域情報と自艇の航行情報を表示する。自艇を含めた水域情報は、水域情報画面と同様の表示となるが、自艇のマーカーについてのみ赤色で表示し識別しやすくしている。また、航行支援などの応用的な利用を見据えて、現在の自艇の艇速、航続距離、航続時間といった航行情報を表示している。

<!-- IMG: 水域情報画面 -->
<!-- IMG: 水域マップ編集画面 -->
<!-- IMG: 艇情報設定画面 -->
<!-- IMG: ナビゲーション画面 -->

##### 機能実装

各機能の実装の詳細について述べる。

- システムの実装詳細
  - アプリケーション
    - 障害物領域の登録
    - ナビゲーション
      - 位置情報の取得
      - 速度の取得
      - 方位角の取得
        - スマートフォンの地磁気情報を利用すると精度が保証されない
        - 利用する際はスマホ上部を艇の進行方向に向けて足元に置くものとする
      - 艇情報の共有 // 毎秒
      - 艇情報の取得 // リアルタイム
      - 衝突警告アルゴリズム
        - 領域の実装
          　- GoogleMapsAPI の Polygon
        - ポリゴンの重複判定
        - 衝突予測
          - 停止距離までステップに分割
      - 警告
        - 音声による警告
        - 警告種別と形式
  - サーバ・データベース
    - データベース
      - Firestore で NoSQL
    - 障害物領域の登録
      - 点群を記録
    - 艇情報の共有
      - ナビゲーション中の艇情報をリアルタイムで反映

## 第 4 章 システム評価

### 4.1 評価方針

- 評価の観点
  - システムの機能および性能について述べた後、安全性・コスト・使用性・拡張性について評価し、研究目的に対する達成度を考察する

### 4.2 機能評価

- 重要な機能にどんなものがあるのか挙げる
  - 次の機能を実現している
    - 艇情報の取得・共有・確認
      - 地理座標
      - 速度
      - 方位角
      - 艇の種類
      - クルーの識別子
    - 障害物領域の登録・確認
      - 範囲をなぞるだけの直感的な操作で障害物領域を登録できる
    - 衝突警告機能
      - 艇の形状を考慮した警告
      - 速度を考慮して最小限の警告
- 既存システムとの機能比較

  - 既存システムとの比較は次のとおりである

    | 機能/特徴                    | 提案システム | Rowcus | SmartAIS         |
    | ---------------------------- | ------------ | ------ | ---------------- |
    | 他艇との衝突警告             | ○            | ○      | ○                |
    | 水上の静的障害物との衝突警告 | ○            | ○      | ×                |
    | 水中の静的障害物の検知       | ○            | ×      | △(浅瀬に限る)    |
    | 艇速を考慮した警告           | ○            | -      | ×                |
    | 全方位の衝突検知             | ○            | ×      | ○                |
    | オフライン動作               | △(対物のみ)  | ○      | △(対物のみ)      |
    | 専用デバイス不要             | ○            | ×      | ○                |
    | 導入コスト                   | 低           | 高     | 低               |
    | 位置情報の記録・共有         | ○            | ×      | ○                |
    | 段階的警告                   | ○            | ×      | ○                |
    | 針路補助                     | ×            | ○      | ×                |
    | 他艇の搭載要否               | 必要         | 不要   | 必要(AIS でも可) |

  - Rowcus は、
    - 水中の静的障害物の検知ができない
    - 全方向の衝突検知ができない
    - 専用デバイスが必要である
    - 導入コストが高い
    - 位置情報の共有ができない
  - SmartAIS は、
    - 静的障害物の検知ができない
    - 艇速を考慮した警告ができない
  - 本システムは、他のシステムに比べて以下の点で優れているといえる
    - 導入コストが低い
    - 艇速を考慮した警告が行える
    - 静的障害物に対する衝突警告が行える
  - 逆に次の点で劣っているといえる
    - オフラインでは他艇との衝突警告が行えないためインターネットへの接続が必要
    - 進路補助を行えない // これは改良することで改善できる
    - 他艇も搭載する必要がある

### 4.3 性能評価

- リソース使用量
  - バッテリー消費
- 通信データ量の評価
  - データ量を計測
- スケーラビリティの評価
  - 接続台数の増加に伴う通信量の変化
  - データベースの負荷
- Android での正常動作をまだ確認できていない
  - iOS では正常な動作が確認できた

### 4.4 安全性評価

- 3 つの評価を行う

  - 衝突シミュレーションによる衝突警告アルゴリズムの有効性評価
  - 衝突ケースを模して衝突防止の有効性評価

    - 衝突ケースを模して衝突防止の有効性評価

      - 概要
        - 橋脚との衝突ケースを模擬して艇を接近させ、本システムの衝突防止機能が有効かどうかを評価
      - 実験環境: 大蟷螂橋の橋脚／庄内川
      - 使用する艇: 4x
      - 評価方法
        - ナビゲーションを行いながら一定の艇速で橋脚に艇を接近させる
        - 警告を受け周囲を確認した後、艇を停止させ、警告のタイミングや停止位置を確認
        - 試行後、クルー全員にアンケートを行い、評価を行う
        - 評価内容は次のとおり／各 7 段階評価
          - 他艇または障害物との衝突を回避する上で警告のタイミングは適切か
          - 艇を停止させた後、艇を操船するのに必要な領域 が周囲に確保できていると感じるか
          - 警告（警告音）は認識できるか
        - 艇速を 2:50 と 2:30 の 2 段階に分けて評価する
      - 安全に十分配慮して評価を行った
        - 警告によらずクルーの判断で艇を停止させる
        - 橋上から監視を行い必要に応じてクルーに警告を行う
      - 評価結果
        - アンケート結果
          - 艇速 2:50 の場合
            - 他艇または障害物との衝突を回避する上で警告のタイミングは適切か
              - 4, 5, 4, 4／4.25pt
            - 艇を停止させた後、艇を操船するのに必要な領域が周囲に確保できていると感じるか
              - 5, 7, 7, 5／6pt
            - 警告（警告音）は認識できるか
              - 7, 7, 6, 2／5.5pt
          - 艇速 2:30 の場合
            - 他艇または障害物との衝突を回避する上で警告のタイミングは適切か
              - 4, 5, 4, 4／4.25pt
            - 艇を停止させた後、艇を操船するのに必要な領域が周囲に確保できていると感じるか
              - 6, 7, 7, 6／6.5pt
            - 警告（警告音）は認識できるか
              - 7, 7, 7, 3／6pt
        - インタビュー調査
          - A「艇が長いとスマホから遠いシートだと聞こえづらいかも」
          - A「レートが高かったりすると音が聞こえづらい。低速時は聞こえたが、高速時は聞こえづらかった」
          - A「警告タイミングはバッチリで航路を補正する余裕もあってちょうどいい」
          - B「よく聞こえた」
          - C「誰が伝えるか問題になる」
          - C「音量は良かった」
        - 評価の様子
          - GoPro の映像
          - スマホの画面録画
      - 考察

        - 艇速 2:50 の場合
          - 警告タイミング
            - タイミングは適切という評価が多く、インタビュー調査でもタイミングは適切だったという評価があった
            - 漕手が艇を停止させる、あるいは艇の航路を補正することのできるタイミングで警告できていると言える
            - また、警告が早すぎるということはなく必要に応じて警告できていることがわかる
          - 停止位置
            - 操船するのに必要な領域が周囲に確保できているという評価が多い一方で、個人によってはやや確保できていないという評価があった
            - インタビュー調査によると、... // おんけんにインタビュー
          - 警告音
            - 警告音は認識できているという評価が多く、インタビュー調査でも警告音は認識できたという評価があった
            - 一方で、スマートフォンのあるバウからシートが離れると警告が聞こえづらくなることがわかる
        - 艇速 2:30 の場合
          - 警告タイミング
            - タイミングは適切という評価が多く、インタビュー調査でもタイミングは適切だったという評価があった
            - 漕手が艇を停止させる、あるいは艇の航路を補正することのできるタイミングで警告できていると言える
            - また、警告が早すぎるということはなく必要に応じて警告できていることがわかる
          - 停止位置
            - 操船するのに必要な領域が周囲に確保できているという評価が多い一方で、個人によってはやや確保できていないという評価があった
            - インタビュー調査によると、... // おんけんにインタビュー
          - 警告音
            - 警告音は認識できているという評価が多く、インタビュー調査でも警告音は認識できたという評価があった
            - 一方で、スマートフォンのあるバウからシートが離れると警告が聞こえづらくなることがわかる
            - また、艇速が速いと警告が聞こえづらくなることがわかる。インタビュー調査からもレートが高かったりすると音が聞こえづらい。低速時は聞こえたが、高速時は聞こえづらかった。とのコメントがあった。これは高速時に漕艇音や水の音が大きくなり警告音が聞こえづらくなることが原因であると考えられる。// そのため、艇速に応じて警告音の音量を調整できるようにするといった改善が必要であると考えられる（警告音の対象は全員？）

        // 次回、周囲に余裕があるかについて考察

  - 練習時に導入して有効性評価

#### 4.4.1 実環境での評価実験

##### 4.4.1.1 実験目的

- 実験目的
  - 研究目標（より詳細に）がどの程度達せられているかを定量・定性的に評価する
  - 提案システムの課題を明らかにする
    - e.g. 消費電力が大きい
    - e.g. 静止時は鳴る必要がない

##### 4.4.1.2 実験方法

- 評価指標
  - 研究目標と対応した評価項目・指標を設ける

##### 4.4.1.3 実験結果

- 実験結果を淡々と掲載

##### 4.4.1.4 考察

### 4.5 コスト評価

- 本研究でのコストは導入コストと通信コストの 2 つに分けられる
- スマートフォンは安価なものから高額なものまであるが、既に多くの人が所持しているため、個人のスマートフォンを活用できると考えられる
  - それを踏まえ、本システムの導入コストは Rowcus に比べて低いといえる
- 一方で、通信コストが掛かることに注意したい // 具体的な費用については言及しない
  - 通信量
    - Android で通信料を計測
  - 通信回数
    - 毎秒 1 回で艇が増えると...

### 4.6 使用性評価

- ユーザーアンケート/インタビュー結果
  - 練習時に導入して評価
    - 操作性
      - 障害物領域を容易に登録できるか
      - 画面の操作
        - ナビゲーションを開始しやすいか
    - 導入容易性
      - システムを導入することは容易か
        - アプリがストアにあるとして導入は容易だと思うか
      - 継続的に使用できると思うか
    - 本システムにどのような課題があると思うか

### 4.7 拡張性評価

- 次のような利用方法も考えられる
  - リアルタイムな艇情報の利用
    - 監視の際に艇位置を把握でき安否確認しやすい
    - コーチングの際にどこに艇がいるのかを把握できると効率的な指導が可能
- 次のような拡張が可能である

  - 緊急通報機能
    - 救助要請・緊急通報などに用いる
  - 位置情報を航行ログとして記録し確認できるようにする
    - 練習状況の記録や分析
    - 衝突事故時の状況把握

- memo
  - 拡張性がある // 補助的な要件／評価の方に書けばいいかも
    - 艇の位置把握
      - 監視やコーチング
    - 救助要請などの緊急通報
    - 航行ログ
      - 衝突事故時の状況把握
      - 練習状況の記録や分析

### 4.8 考察

- 評価結果の総括
  - 安全性・コスト・ローイング競技に適していることをそれぞれ対応付けて明示的に述べる
  - 既存システムよりも優れていることを述べる
- システムの課題
  - システムを実現する上での課題
  - システム自体の課題を把握する
  - 衝突防止システムにスマートフォンを用いる際の一般的な課題
    - 圏外だと他艇の位置情報が取得できない

## 第 5 章 結論

### 5.1 まとめ

- 本研究ではこういう目的を達成するためこんなシステムを作った
- また予備実験ではこういうことがわかった
- その上で評価実験を行いこれらの結果が得られこういうことが考察できた
- また課題としてこのような点が明らかになった

### 5.2 今後の課題

- 本システムで実現しきれなかった機能
  - 陸地との衝突防止が実装できていない
    - GoogleMaps の API である地点の地理属性が取得できるとかできないとか
    - 正確な地理属性を高頻度で取得する必要があるができるのか？
- 本システムの課題 // システム自体の課題
- 衝突防止システムを実現する上での一般的な課題
  - 圏外だと他艇の位置情報が取得できない
- 本研究で取り組めなかった課題等
  - 空走時間の計測とその内訳
  - 正確な停止距離の計測
    - 水流や風、漕手の経験による影響が排除できていない
    - 研究に協力してくれる環境が必要である

## 参考文献

- [Rowing Navigator リポジトリ](https://github.com/sample/rowing-navigator)

## 謝辞

本研究を進めるにあたり、ご多忙の中懇切丁寧なご指導をしていただきました名古屋大学大学院情報学研究科高田広章教授、ならびに同研究科松原豊准教授に深く感謝を申し上げます。また、本研究に数々の助言を頂きました情報プラットフォーム論講座の皆様に感謝を申し上げます。さらに、本研究の実験・評価にご協力いただきました名古屋大学漕艇部の皆様に感謝を申し上げます。最後に、本研究を進めるにあたり、精神的、経済的な支えとなった家族に心から感謝を申し上げます。

## メモ

- 停止時間がどのように変化するか確認したい
- 旋回回避する場合はもっと近付いてもよくなる
- 実用性で表現できる
- 衝突警告アルゴリズム -> 衝突警告条件
- 欠損値の話
- 松原先生のスライドレビュー反映
- どちらに向かうべきかを知らせるという改善点
- 想定していない事項について明示する
  - 回避動作（変針, 加速, 減速）、位置情報誤差(？)、水の流れ
- パラメータの詳細について掲載
- コスト負担により普及が進まない
- 通信量は Android で計測できる
- "不要な警告を出さない"という点については議論を控える
- 機能的な比較を行うのがいいかも
- ある程度の処理性能を必要とする旨
- 全艇が搭載していると言う前提
- 見えない範囲の監視・生存確認に使えるのはいい by マネ
- 速度（騒音）に合わせて音量を調整できるようにするといいかも
- 要件を満たしているかどうかの評価は行なっていないことを明確にする
- システムに依存するべきではなく人の衝突防止策に加えて補助的な利用に止めるべきであるという考察
- 提案システムは視界不良時でも有効であるという主張
- 危険水域の共有・把握に活用できる
- シート位置による補正
- 大きな橋の下に入ると位置情報が不安定になる
- 艇の乗り換えが多いため出艇時に艇情報を設定できるようにしている
- 圏外だと他艇の位置情報が取得できない
- 事故による影響を追記
- 艇速を考慮していないというより、警告条件がローイングに適していない、の方が適切
- 図 X に〜を示す、に修正

diff for PR
