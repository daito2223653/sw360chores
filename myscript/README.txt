# config_info.pl 変数展開できる形のコンフィグ.
# config.yaml    yamlで記述した人が見やすい形の設定ファイル.

共有される主な変数: @=配列　$=変数
@CONTAINERS: コンテナの名前が完全名として格納. $CONTAINERS[$cno] で名前を取得できる.
@container_nos: コンテナの番号(0,1,2,3,...n-1)が格納.        それぞれ, @CONTAINERSの[i番目]と対応している.
@USING:         各コンテナが使っている コマンド(json, journaldなど)が コンテナの番号に合うように格納. @USING[$コンテナ番号] でそのコンテナが使用しているコマンドを取得できる

@CMD      :         コマンドの完全名 
@CMD_nos  :         コマンドの番号
@cmd_names:         コマンドの短い名前.

@DEFAULT_CONTAINERS:  デフォルトで使うコンテナの番号を格納.

my $cno : コンテナ番号.
my $cname : コンテナ名
my @targets: ユーザーが選択したコンテナ番号
my $logstr : get_log()した結果. ログが文字列として格納.


setup.pl  -----
option : --checkSetting, --setup
基本動作: 
1. setup.pl --setupオプション:
config_yamlから読み込んだ設定(read_yaml())をconfig_info.plに変数展開できる形で上書き.(write_pl())
2. setup.pl --checkSetting: 
config_info.plからの情報を書き出す. 

main.pl -----
option : --interactive, --look, --save, --update, --html, --timestamp

--interactive: mainの前で、@targetsに入れる、コンテナ番号を動的に選択する。

mainの後⇓
--timestamp  get_log() 中に -t をつけるなど.
$logStr = get_log()

--look       : 
--save       :
--update     : 少しややこしいです。 まだ不具合中。
--html       : ややこしいです. make_modified_log.plを各コンテナごとに呼び出します. generate_html.plを最後に呼び出します



ｃ


