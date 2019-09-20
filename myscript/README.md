## logCollection script for SW360chores
OSS管理ツールの代表的なコンポーネントの2つ("Sw360chores"と"FOSSologyのDockerコンテナ")を対象にログを収集するスクリプトです。<br>
SW360chroesとは、SW360をDockerで動かすためのOSSです。[以下のurlより参照] : <br>
インターンシップの成果として、本レポジトリと以下の２つのレポジトリに分けて、せっかくなので公開します。 (許可とっています)
<br>利用よりも部分部分を何かの参考にしてください！！！


## What you can do
デフォルト設定でSW360choresのコンテナのうち、SW3660・couchdb・postgresqlのログをDocker logsコマンドを用いて一度に取得できます。<br> 

収集だけでなく、実際には、
1. 対話的なターゲットの選択
2. HTMlを生成して見る : --html
2-1 検索した文字に色をつける  : コマンド引数
2-2 過去に収集したログのアップデート : --update {group no}
3. 検索した文字のみを取る     :  *1
4. 一時保存するなどができます。 : --save
などが可能です。 

詳しくは、"Usage"を見てください。

設定ファイルへの追記と変更で、デフォルトでログを取得するターゲットコンテナの変更や、Dockerコンテナ名の変更やSW360chores以外のDockerコンテナの追加、journaldやsyslogを利用するその他のアプリケーション(Dockerでなくても良い)
のログを取ることが可能です。<br>.また、同じく設定ファイルへの追記と変更でjournaldとsyslogコマンド、ターゲットを引数に文字列を返すコマンド(*1)に対応可能です。
<br>その他、独自のログを使うアプリケーションと、デフォルト設定とsyslog、journald以外のログ収集方法を選んだDockerコンテナのログを収集することはできません。

*1: 例えば、 "docker logs [target] | grep -i error" とするとエラー行のみを取得することができます。

詳しくは、"Setting"を見てください。

* SW360choresの現安定versionで動作確認済み(9/20) 新しいversionの動作確認はできていません

## Prerequisites
SW360chores : 
perl cpan yaml : 

## Usage
setup.pl --checkを実行してみてください。（config_info.plの内容が表示される）<br>
"""<br>
 cmd_nos => <br>
 cmd     => <br>
 cmd names => <br>
 conteiner_no => <br>
 conteiners =>  <br>
 USING       => <br>
 defaults    => <br>
"""<br>
のように出る場合は、"Setting" より、setup.pl --setupを実行してからmain.plを実行してみてください。<br>
main.pl       :  デフォルトで読み込むコンテナのログを収集します。収集するだけで何も実行ないです。<br>
 --html　　　　:  HTMLを作成する.  <br>
 --html test testb testc : HTMLを生成して "test"と "testb", "testc"の文字に色をつける(errorなどはデフォルトで色がつく)<br>
 --look       : コマンドラインで確認する<br>
 --interactive : ログを収集するターゲットを対話的に決定する<br>
 --timestamp  : タイムスタンプをつける
 
以下のオプションは安定していません。<br>
--save       : 保存する <br>
--update     : 更新する<br>

## Setting
config.yaml    : ユーザが設定する設定ファイル <br>
config_info.pl : スクリプトから読み込まれる設定ファイル。共有変数が "setup.pl --setup"の実行で書き込まれます。<br>

必須!!<br>
setup.pl --setup : yamlを読み込んで、config_info.plに共有変数を書き込む<br> 
必須!!<br>
setup.pl --check : 設定の確認する<br>

## Test
今後にやります

## 動作模様

