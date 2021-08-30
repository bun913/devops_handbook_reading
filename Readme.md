# The DevOps HANDBOOK の読書とメモ

# イントロダクション

筆者は共同でこの本を記載しているが、全員に共通することは DevOps に関してみんなアハ体験をしていること。

「あっわかった」その正体にはっと気づくような体験のことらしい。

またイントロの中で DevOps によくある誤解が述べられている。

- DevOps は単なる自動化・もしくはインフラのコード化だ

↑ の認識は結構ある気がする。

実際のところは DevOps は IT 組織全体で共通の目標を達成するための文化や規範をも必要とする。

オートメーションは DevOps という文化を成すための一つの構成要素や手段に過ぎないのではないか。

## 序章

技術的負債とは「私たちの判断で引きおきされた問題が将来の選択肢を狭めていくこと」

IT がうまくいかないと組織全体がうまくいかず、ダメージがゆっくり現れても、急に現れても破壊は同じように起こる。

「恐怖で支配する文化」ではなく、高信頼マネジメントにより「リスクを追う人が評価される協力を尊ぶ文化を作る。」

問題を解決するためには問題を直視しなければならないのだ。

DevOps の実践をしている会社とそうでない会社では以下のような違いがあった

- コードの変更とデプロイ 30 倍
- コードと変更のデプロイのリードタイム 200 倍
- 本番デプロイ(成功率が 60 倍高い)
- サービス復元の時間(168 倍早い)

## 1 章

DevOps はトヨタ生産方式（リーン生産方式）を IT に応用したもの

- フロー
- フィードバック
- 継続的な学習と実験

継続的デリバリーはコードとインフラストラクチャを常にデプロイ可能な状態に保ちトランクにチェックインされたコードは全て本番環境に安全にデプロイできるようにする
という考え方

日々習慣的に業務の改善を行うという改善のカタを作り上げることが重要

IT バリューストリームとは

- ビジネス上の仮説を立案してから顧客に価値を送り届ける技術サービスを生み出すまでの間に必要なプロセス

↑ を図るための指標が２つ

- リードタイム
  - 顧客が要求をした時から要求が満たされるまでの間の時間
- プロセスタイム
  - 顧客の要求のための作業を開始した時から満たされるまでの間の時間

DevOps では開発者は自分の仕事に対するフィードバックをコンスタントに受け取り、他部門からの制約を受けずに素早くコードを実装、〜本番環境へのデプロイができる。

### DevOps の 3 つの道

- 開発 → 運用 → 顧客の左から右へのワークフローを高速にする
  - 仕事を可視化し、バッチサイズと作業のインターブルを削減し、品質を組み込み、下流のワークセンターに不良品を渡さない
  - 絶えず改善を続けていく
- バリューストームのあらゆるステージで素早くてコンスタントな右から左へのフィードバックフローを受け取ること
- 成功と失敗の両方から組織として学習し教訓をえていく生産的な高信頼マネジメントの企業文化を生み出すこと
  - チーム内の発見を組織全体の経験の蓄積とする

### 2 章

開発　 → 　運用　への作業を素早く、かつミスなく届けるにはカンバンによる管理が良い。

この時カンバンはできるだけバリューストリーム全体を対象としていて、作業完了が右端に達した時に限るようにすればよい。

![カンバンイメージ](./images/kanban.png)

- マルチタスクで仕事をしている時には単純なタスクでも作業効率が大きく下がる
- 看板で各段階において、WIP(仕掛かり)として良いカードの数を制限する
- バッチサイズを小さく（問題ごとを小さくして、確実に解消していく）
  - 作業を小分けにすることで作業ミスによる手戻りもすくなくなり、生産性が上がる
- 日常業務からムダを削減する
  - 組織の目標達成のために継続的に学習することによって日常業務から苦痛と重労働を取り除くこと
  - 結果に影響を及ぼさずに省略できる皇帝など
    - 部分的に完成した仕事（途中のドキュメントとか）
    - 余分な処理
    - 余分な機能
    - など

作業を可視化し、WIP を減らし、バッチサイズを縮小して作業の受け渡しの負荷を減らして、制約条件を継続的に見つけ出して評価し、日常業務から苦痛を取り除く

### 3 章

- IT に限らず複雑なシステムにおいてエラーは必然であり不可避なので、あらゆる障害を発見できるという自身の元、恐怖を感じずに仕事ができる安全なシステムを設計しなければならない
- パフォーマンスが高い工場であらゆるバリューストリームの中に作業が測定、モニタリングされていて、不良や大きな逸脱があればすぐに誰かが見つけて対処する
- 問題が発生した時に一丸となって解決し、下流に影響を与えない。この一丸というのが、プロセス全体を止めるようであるが、学習が可能になる。
  - 記憶が薄れたり、状況が変化したりすることによって極めて重要な情報が失われることを防ぐ
- 本番環境のインシデントであれ、バリューストリームの早い段階のエラーであれ、なんか問題を起こした時に非難されずに、むしろそうすることが推奨される文化を作ることが重要
- バリューストリームないの全ての人々が、日常業務の一部として自分の担当分野の問題を見つけて修正していく日つゆがある。
- 開発・運用の特定の部門に責任が追及されないように、QA や情報セキュリティチームの品質チェックを自動化する
  - また、開発者がテストをリクエストするのではなく、開発者がオンデマンドでテストを実行できるようにする

素早くフィードバックを返して学習する。
問題の発生時には組織が一丸となって問題解決にあたり、新しい知識・知恵を生み出して上流で品質を確保する。

### 4 章

第３の道は継続的な学習の文化を作り出すことに着目する。

個人がコンスタントに知識を生み出して、それをチームや組織の知識に転化していくための原則。

- 事故や問題が起きた時に対応を誤ると、人々の心に注意深さではなく恐怖を植え付け、注意深い組織ではなく官僚主義的な組織を作り上げてしまう
- インシデントが起きた時は必ず「非難なしのポストモーテム（事後検証）を実施すると良い」
  - 非難を取り除けば恐怖が取り除かれ、恐怖が取り除かれれば正直になれる。正直になれば予防ができるようになる

#### 日常業務の改善を制度化する

- 問題の根本的な解決を避け、日常的な予防策に頼っていると、問題と技術的負債が蓄積し、やることなすこと全てがその予防策にすがり大きな障害から逃げ回ることになる
  - 日常業務より大切なのは日常業務の改善だ
  - 逆に技術的負債の解消のために正式に時間をとって、リファクタ改善をすれば日常業務を改善できる

### 5 章

実際に組織で DevOps 改革を起こすためにはどこから手をつけていけば良いのか。
この章から解説が始まる

DevOps の導入初期の段階では、比較的保守的なグループを巻き込もうとしない。
それよりもリスクを比較的怖がらないグループで成功を収めて、そこを基盤にしてしまう。
（これをイノベーターとアーリーアダプターを見つけると表現する）

- 最初の段階では問題解決を早くしたいと考えている人たちとグループを作る
- 次の段階でより多くのチームに DevOps を普及させていく。↑ で作ったチームを派遣したりとか（マキシンがやったことやん）
- 抵抗派を明らかにする。ここと対峙するのは ↑ で基盤をつくって、大勢を味方につけてから

### 6 章

バリューストリームないの作業を理解し、それを可視化して組織全体に広げる

- DevOps への変革の候補となるアプリ・サービスを選択したら顧客に対して価値を生み出すために協力しなければならないバリューストリームのなかの全てのメンバーを明らかにする必要がある
  - 製品オーナー
  - 開発
  - 品質保証（QA）
  - 運用
  - 情報セキュリティ
  - リリースマネージャー
  - IT 担当役員・バリューストリームマネージャー
- 次にバリューストリームに具体的にどのような作業があるか把握する（イメージは以下)
  - 要望ヒアリング
  - 設計と分析(1 週間, 完全正確率: 60%)
    - 例えば 60%の要望しか正しくヒアリングできていないなど。
    - 前段で正しくバリデーションできていればもっと正確率をあげて効率化することができるのか。などみていく
- 専任の変革チームを編成する
  - 測定可能なシステムレベルの成果を生み出すことに専念させる
    - git システムにコードをプッシュしてから本番環境にデプロイをするまでのリードタイムを 50%にするみたいな
  - DevOps の仕事だけを与える
  - チームメンバーにはあらゆる分野のジェネラリストを選ぶ
- 改善の計画期間を儲ける時は小さく、一個の期間を短くする
  - 数週間から最悪での数ヶ月
- ポジティブでユーザーからは見えない価値を生み出す作業に 20%のサイクルを投資する
  - アーキテクチャー・非機能要件・プロセスの改善・リファクタ・メンテナンス性・セキュリティ
  - 組織が 20%ルールを守らないと、技術的負債がいっぱいになり、それらの解消に全てを当てる必要が出てくる

### 7 章

バリューストリームの目標を達成するために、どのような専任の組織を作る必要があるか。

- Conway の法則
  - システムを設計する組織は組織内のコミュニケーション構造のコピーになっているような設計しか出せない。
  - 組織が大きいほど柔軟性が低くなり、この現象は明白になる
  - どのような構造の組織を作るかで、作られるソフトウェアやアーキテクチャに強い影響を与える
  - 組織間で互いに依存する仕事があると、コードも密結合になってしまい、安全な変更ができなくなる。
- 組織の構造
  - 職能型組織
    - IT の伝統。データベースグループ、ネットワークグループ、開発グループみたいに求められる職務上の能力に応じて組織を分ける。情シス時代もこうだった。
    - 互いに他のチームに依存するようになるためリードタイムは長くなる。
    - 人員は自分の仕事がバリューストリームのどこになるかわかりにくい。
      - 言われたからやっているだけ。モチベーションもクソもない。
    - 職能組織だと無理というわけではなく、共通の目標として顧客と全体としての組織が生み出す結果を意識できていれば DevOps の成果を実現可能
    - パフォーマンスの高い組織では、社員が共通の目標を目指している。
  - DevOps の成果を得たいなら、職能思考の影響を抑え、市場指向（スピードのために最適化）を実現して独力で安全に仕事を進められる小さなチームを編成して、顧客に価値を早く届けられるようにする必要がある。
  - Facebook の例
    - Facebook はむかしコードのデプロイに大きな問題を抱えていて、長時間労働も状態かしていた
    - そんなかで有効だったのが「自分が作らせた機能・システムの電話サポートをエンジニア・技術系管理職にさせること」だった
      - The Unicorn Project でもマキシンがやっていた
    - 全てのチームメンバーがジェネラリストになれるようにする
      - 高度に専門化された部署だとそれぞれが主権国家のように、要求や権利を主張する
        - わかる。これ。公務員時代がそうで、みんな自分の部署の仕事をすることしか頭になくて、他の仕事なんてわからなかった（組織としてなんでその仕事が必要かということもわかっていなかったような気がする)
      - アプリケーションデプロイに必要な全ての皇帝の理解がある「フルスタックジェネラリストエンジニア」という言葉も使われるようになった
      - 専門家よりもジェネラリストの方がバリューストリーム全体でみた時に、キューを消費するのが圧倒的に早いとのこと
    - ジェネラリストにならせるには組織として社員に学習できる機会を提供する必要がある。
      - チーム間のコミュニケーションに問題があるなら、仕事として「他のチームに LT を発表させる」時間を提供させたりすれば良い
      - 会社として顧客ともそのような時間を取ることを合意しておき、「仕事」として学習の機会を提供すれば良い
  - Amazon の場合
    - チームを小さく保つ。ピザ２枚で満足できるように、5 人から 10 人程度にする。
      - 自分たちが取り組んでいるシステムの明確な理解を共有できる
      - 開発しているものの成長スピードが抑えられる。チームがしすてむについて共通理解を維持するのに役立つ
      - 権力を分散し、チームが独立して動ける。
      - 社員が多くリーダー経験を積むことができる。（しかも失敗の影響を局所化できる）

### 8 章

- セルフサービスで運用プラットフォームを手に入れられなければ、クラウドは高くつくホスティングの 2.0 に過ぎない
- 製品チームに運用エンジニアを配置する
  - 運用エンジニアは社内外の顧客とみせっつに関われる
  - 人が作ったものをただ使うのではなく、自分で良いものを生み出すことに協力しようとする
  - 開発と組ませることで運用の知識と能力を開発チームに伝えることもできる
  - 運用の知識を自動化コードにすることもしやすい
- 全てのチームに運用を配置することができなければ
  - 個々のチームに連絡担当をつける
  - 指名運用エンジニア
    - この人たちには以下のようなことが求められる
    - 新しい製品の機能。なぜそれを作るのか
    - 運用可能性・スケーラビリティ・可観測性に関しての製品はどうなっているのか

開発の日常に運用を統合する。

## 感想・メモ

### DevOps の 3 つの道

- フロー
  - 開発フローの左から右へのフローを早くする
- フィードバック
  - ↑ と逆で右から左へのフィードバックを早くする
- 継続的な学習と実験

ここを大前提として捉えておく。

### どのような組織づくりが必要か

バリューストリーム（顧客に価値を届けるための全ての作業の流れ）の目標を達成するためには組織づくりの重要性が説かれていた。

IT では職能型の組織（データベース専門チーム、ネットワーク専門チーム、開発チームのように職務能力に応じて組織を作る）が多かった。

しかしこれでは、他のチームに依存する作業を産む（例えばデプロイをするために、まず QA チームにテストをしてもらって・・・のような）

これによりバリューストリームの流れが遅くなり、顧客に価値を届けるのが遅くなる。

小さくチームを作って、必要な能力を持った人を配置し、チームが独力で顧客に価値を届けれるようにするべき。

実は私が公務員の時にも情報システム課の上司がこのような考えを持っていた。

- 情シスに全てを集中させるというよりも、各部署に情シスの職員のような能力を持った人員を配置
- その人が情シスとの掛橋にもなりつつ、部署内の問題を素早く解決する

ということだ。

その時の私は例に漏れず「意識高いなぁ・・・・そんな体制実現できるわけないだろ・・・」と思っていたものです。

しかしその時に何が必要だったのかと考えると、「役人組織自体がダメ。お役所仕事しかできないんだから。」と短絡的に考えるのはよくないだろう。

The Unicorn Project でマキシン達がやったように

- 同じ意思を持つ仲間を集め（他の組織の人でもよい）
- その人達と小さな目標を達成し
- 反対派が誰かを把握して
- 準備ができたら体制を変えるように働きかける

という流れが必要だったのかもしれない。

非公式な部署横断な組織みたいなものをどこかの課とやってしまい、無理矢理にでも成果が出たことをアピールできればよかったのだろうか。
（もちろん組織の目標に反するものではなく、それに則った形の結果は必要なのだろうが）

残酷なことにこれは私にも言えること。

「DevOps 専任のチームを作って、作業を効率化させましょう！」とか言っても誰も相手にしてくれない・・

まずは私と同じ意思を持った人を探して、組織の目にも見える形で結果を出す必要がある
（コミュ障を言い訳にしていられないということ）

または普段から素行をよくして、「こいつにならチャレンジさせてもよいか」という印象を持っておいてもらう必要があるという・・・

### すぐに使えそうと思ったテクニック

- カンバン管理で、各段階に配置できるチケット・カードの数を制限する
  - これによりマルチタスクを制限できる
  - また、作業の完成を妨げている問題も見えやすくなる
