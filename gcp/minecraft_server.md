```
タスク 1: VM を作成する
詳細オプションを使用して VM を定義する
GCP Console のナビゲーション メニュー（ナビゲーション メニュー）で、[Compute Engine] > [VM インスタンス] をクリックします。
[作成] をクリックします。
次のように指定し、残りの設定はデフォルトのままにします。
プロパティ	値（値を入力するか、指定されたオプションを選択）
名前	mc-server
リージョン	us-central1
ゾーン	us-central1-a
ブートディスク	Debian GNU/Linux 9 (stretch)
ID と API へのアクセス > アクセス スコープ	各 API にアクセス権を設定
ストレージ	読み取り / 書き込み
[管理、セキュリティ、ディスク、ネットワーク、単一テナンシー] をクリックします。
[ディスク] をクリックします。 ゲーム ストレージに使用するディスクを追加します。
[新しいディスクを追加] をクリックします。
次のように指定し、残りの設定はデフォルトのままにします。
プロパティ	値（値を入力するか、指定されたオプションを選択）
名前	minecraft-disk
タイプ	SSD 永続ディスク
ソースの種類	空のディスク
サイズ（GB）	50
暗号化	Google が管理する鍵
[完了] をクリックします。ディスクが作成され、VM の作成時にこのディスクが自動的に VM に接続されます。
[ネットワーキング] をクリックします。
次のように指定し、残りの設定はデフォルトのままにします。
プロパティ	値（値を入力するか、指定されたオプションを選択）
ネットワーク タグ	minecraft-server
ネットワーク インターフェース	[default] をクリックしてインターフェースを編集
外部 IP	IP アドレスを作成
名前	mc-server-ip
[予約] をクリックします。

[完了] をクリックします。

[作成] をクリックします。

タスク 2: データディスクを準備する
ディレクトリを作成し、ディスクのフォーマットとマウントを行う
ディスクはインスタンスに接続されていますが、マウントやフォーマットはまだ行われていません。

mc-server で [SSH] をクリックし、ターミナルを開いて接続します。

データディスクのマウント ポイントとなるディレクトリを作成するには、次のコマンドを実行します。

sudo mkdir -p /home/minecraft
ディスクをフォーマットするには、次のコマンドを実行します。

sudo mkfs.ext4 -F -E lazy_itable_init=0,\
lazy_journal_init=0,discard \
/dev/disk/by-id/google-minecraft-disk
結果（コピーしないでください。これは出力例です）:

mke2fs 1.42.12 (29-Aug-2014)
Discarding device blocks: done
Creating filesystem with 13107200 4k blocks and 3276800 inodes
Filesystem UUID: 3d5b0563-f29e-4107-ad1a-ba7bf11dcf7c
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424
Allocating group tables: done
Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done
ディスクをマウントするには、次のコマンドを実行します。

sudo mount -o discard,defaults /dev/disk/by-id/google-minecraft-disk /home/minecraft
ディスクのマウント後に出力は表示されません。

[進行状況を確認] をクリックして、目標に沿って進んでいることを確認します。

VM を作成してデータディスクを準備する
タスク 3: アプリケーションをインストールして実行する
Minecraft サーバーは Java 仮想マシン（JVM）上で実行されるため、Java Runtime Environment（JRE）が必要です。このサーバーにはグラフィック ユーザー インターフェースが必要ないため、ヘッドレス バージョンの JRE を使用します。これによりマシンでの JRE のリソース使用量が少なくなり、Minecraft サーバーのリソース使用量を必要に応じて拡張できる十分な容量が確保されます。

Java Runtime Environment（JRE）と Minecraft サーバーをインストールする
mc-server の SSH ターミナルで、次のコマンドを実行して VM 上の Debian リポジトリを更新します。

sudo apt-get update
リポジトリの更新後にヘッドレス JRE をインストールするには、次のコマンドを実行します。

sudo apt-get install -y default-jre-headless
永続ディスクがマウントされているディレクトリに移動するには、次のコマンドを実行します。

cd /home/minecraft
wget をインストールするには、次のコマンドを実行します。

sudo apt-get install wget
続行のプロンプトに従い、[Y] と入力します。

現在の Minecraft サーバーの JAR ファイル（1.11.2 JAR）をダウンロードするには、次のコマンドを実行します。

sudo wget https://launcher.mojang.com/v1/objects/d0d0fe2b1dc6ab4c65554cb734270872b72dadd6/server.jar
Minecraft サーバーを初期化する
Minecraft サーバーを初期化するには、次のコマンドを実行します。

sudo java -Xmx1024M -Xms1024M -jar server.jar nogui
結果（コピーしないでください。これは出力例です）:

[21:01:54] [main/ERROR]: Failed to load properties from file: server.properties
[21:01:54] [main/WARN]: Failed to load eula.txt
[21:01:54] [main/INFO]: You need to agree to the EULA in order to run the server. Go to eula.txt for more info.
Minecraft サーバーを稼働させるには、エンドユーザー使用許諾契約（EULA）の条件に同意する必要があります。

[進行状況を確認] をクリックして、目標に沿って進んでいることを確認します。

Java Runtime Environment（JRE）と Minecraft サーバーをインストールする
Minecraft サーバーの最初の初期化で作成されたファイルを表示するには、次のコマンドを実行します。

sudo ls -l
server.properties ファイルを編集して、Minecraft サーバーのデフォルトの動作を変更できます。

EULA を編集するには、次のコマンドを実行します。

sudo nano eula.txt
ファイルの最後の行を eula=false から eula=true に変更します。
Ctrl+O キー、ENTER キーの順に押してファイルを保存してから、Ctrl+X キーを押して nano を終了します。
Minecraft サーバーはまだ再起動しないでください。次の手順で別の方法を使用します。

screen で仮想ターミナルを作成して Minecraft サーバーを起動する
この時点で Minecraft サーバーを再起動すると、サーバーは SSH セッションに連動します。つまり、SSH ターミナルを閉じるとサーバーも終了します。この問題を回避するには、screen を使用します。これは、「接続解除」してバックグラウンド プロセスになったり、「再接続」してフォアグラウンド プロセスになったりする仮想ターミナルを作成できるアプリケーションです。接続解除されてバックグラウンド プロセスになっている場合、仮想ターミナルはユーザーがログインしているかどうかに関係なく実行されます。

screen をインストールするには、次のコマンドを実行します。

sudo apt-get install -y screen
Minecraft サーバーを screen の仮想ターミナルで起動するには、次のコマンドを実行します（-S フラグを使用してターミナル名を mcs に設定します）。

sudo screen -S mcs java -Xmx1024M -Xms1024M -jar server.jar nogui
結果（コピーしないでください。これは出力例です）:

...
[21:06:06] [Server-Worker-1/INFO]: Preparing spawn area: 83%
[21:06:07] [Server-Worker-1/INFO]: Preparing spawn area: 85%
[21:06:07] [Server-Worker-1/INFO]: Preparing spawn area: 86%
[21:06:08] [Server-Worker-1/INFO]: Preparing spawn area: 88%
[21:06:08] [Server-Worker-1/INFO]: Preparing spawn area: 89%
[21:06:09] [Server-Worker-1/INFO]: Preparing spawn area: 91%
[21:06:09] [Server-Worker-1/INFO]: Preparing spawn area: 93%
[21:06:10] [Server-Worker-1/INFO]: Preparing spawn area: 95%
[21:06:10] [Server-Worker-1/INFO]: Preparing spawn area: 98%
[21:06:11] [Server-Worker-1/INFO]: Preparing spawn area: 99%
[21:06:11] [Server thread/INFO]: Time elapsed: 55512 ms
[21:06:11] [Server thread/INFO]: Done (102.484s)! For help, type "help"
screen から接続解除して SSH セッションを閉じる
screen ターミナルから接続解除するには、Ctrl+A キー、Ctrl+D キーの順に押します。ターミナルは引き続きバックグラウンドで実行されます。ターミナルを再接続するには、次のコマンドを実行します。

sudo screen -r mcs
必要に応じて、Ctrl+A キー、Ctrl+D キーの順に押して screen ターミナルを終了します。

SSH ターミナルを終了するには、次のコマンドを実行します。

exit
お疲れさまでしたここでは VM の設定とカスタマイズを行い、アプリケーション ソフトウェア（Minecraft サーバー）のインストールと構成を行いました。

タスク 4: クライアント トラフィックを許可する
この時点でサーバーには外部静的 IP アドレスがありますが、ファイアウォール ルールが適用されていないためトラフィックを受信できません。Minecraft サーバーはデフォルトで TCP ポート 25565 を使用しており、この接続を許可するファイアウォール ルールを構成する必要があります。

ファイアウォール ルールの作成
GCP Console のナビゲーション メニュー（ナビゲーション メニュー）で、[VPC ネットワーク] > [ファイアウォール ルール] をクリックします。
[ファイアウォール ルールを作成] をクリックします。
次のように指定し、残りの設定はデフォルトのままにします。
プロパティ	値（値を入力するか、指定されたオプションを選択）
名前	minecraft-rule
ターゲット	指定されたターゲットタグ
ターゲットタグ	minecraft-server
ソースフィルタ	IP 範囲
ソース IP の範囲	0.0.0.0/0
プロトコルとポート	指定したプロトコルとポート
tcp にはポート 25565 を指定します。

[作成] をクリックします。 これで、ユーザーが自分の Minecraft クライアントからこのサーバーにアクセスできるようになりました。

サーバーの可用性を確認する
左側のペインで [外部 IP アドレス] をクリックします。
mc-server VM の 外部 IP アドレスを見つけてコピーします。
次のウェブサイトで Minecraft サーバーをテストします。https://mcsrvstat.us/
上記のウェブサイトが動作しない場合は、別のサイトまたは Chrome 拡張機能を使用できます。

https://dinnerbone.com/minecraft/tools/status/
[進行状況を確認] をクリックして、目標に沿って進んでいることを確認します。

クライアント トラフィックを許可する
タスク 5: 定期バックアップをスケジュールする
一般的なアクティビティのひとつに、アプリケーション データのバックアップがあります。ここでは、Minecraft ワールドデータを Cloud Storage にバックアップするようシステムを構成します。

Cloud Storage バケットの作成
ナビゲーション メニュー（ナビゲーション メニュー）で、[Compute Engine] > [VM インスタンス] をクリックします。

mc-server の [SSH] をクリックします。

グローバルで一意になるようなバケット名を作成し、環境変数 YOUR_BUCKET_NAME に格納します。プロジェクト ID を一意のバケット名として使用できます。次のコマンドを実行します。

export YOUR_BUCKET_NAME=<バケット名をここに入力>
echo で確認します。

echo $YOUR_BUCKET_NAME
Cloud SDK の一部である gsutil ツールを使用してバケットを作成するには、次のコマンドを実行します。

gsutil mb gs://$YOUR_BUCKET_NAME-minecraft-backup
このコマンドが失敗した場合、一意のバケット名が作成されていないことが考えられます。その場合、別のバケット名を選択し、環境変数を更新してから、もう一度バケットの作成を試行してください。

この環境変数を永続的にするには、次のコマンドを実行してルートの.profile に追加します。 echo YOUR_BUCKET_NAME=$YOUR_BUCKET_NAME >> ~/.profile
バックアップ スクリプトを作成する
mc-server SSH ターミナルで、ホーム ディレクトリに移動します。

cd /home/minecraft
スクリプトを作成するには、次のコマンドを実行します。

sudo nano /home/minecraft/backup.sh
次のコードをコピーしてファイルに貼り付けます。

#!/bin/bash
screen -r mcs -X stuff '/save-all\n/save-off\n'
/usr/bin/gsutil cp -R ${BASH_SOURCE%/*}/world gs://${YOUR_BUCKET_NAME}-minecraft-backup/$(date "+%Y%m%d-%H%M%S")-world
screen -r mcs -X stuff '/save-on\n'
Ctrl+O キー、ENTER キーの順に押してファイルを保存してから、Ctrl+X キーを押して nano を終了します。
このスクリプトはサーバーのワールドデータの現在の状態を保存し、サーバーの自動保存機能を一時停止します。次に、サーバーのワールドデータのディレクトリ（world）をバックアップし、その内容を Cloud Storage バケット内のタイムスタンプ付きのディレクトリ（<timestamp>-world）に配置します。スクリプトがデータのバックアップを完了した後に、Minecraft サーバーの自動保存機能を再開します。
スクリプトを実行可能にするには、次のコマンドを実行します。

sudo chmod 755 /home/minecraft/backup.sh
バックアップ スクリプトをテストし、cron ジョブをスケジュールする
mc-server SSH ターミナルで、バックアップ スクリプトを実行します。

. /home/minecraft/backup.sh
スクリプトが終了したら、GCP Console に戻ります。

バックアップ ファイルが書き込まれていることを確認するには、ナビゲーション メニュー（7a91d354499ac9f1.png）で [Storage] > [ブラウザ] をクリックします。

バックアップ バケット名をクリックします。日時スタンプ名があるフォルダが表示されます。バックアップが正常に動作していることを確認したら、タスクを自動化するための cron ジョブをスケジュールできます。

mc-server SSH ターミナルで、cron テーブルを編集のために開きます。

sudo crontab -e
エディタを選択するよう要求されたら、nano に対応する番号を入力して ENTER キーを押します。

cron テーブルの最後に、次の行を貼り付けます。

0 */4 * * * /home/minecraft/backup.sh
この行により、cron は 4 時間ごとにバックアップを実行します。

Ctrl+O キー、ENTER キーの順に押して cron テーブルを保存してから、Ctrl+X キーを押して nano を終了します。
この結果、1 か月に約 300 件のバックアップが Cloud Storage に作成されることになるため、料金がかからないよう定期的な削除が必要となります。Cloud Storage では、オブジェクトの有効期間（TTL）の設定、古いバージョンのアーカイブ、コスト管理を容易にするためのストレージ クラスのダウングレードなど、オブジェクトのライフサイクル管理機能を提供しています。

[進行状況を確認] をクリックして、目標に沿って進んでいることを確認します。

定期バックアップをスケジュールする
タスク 6: サーバーのメンテナンス
サーバーのメンテナンスを実行するには、サーバーをシャットダウンする必要があります。

SSH 経由でサーバーに接続して停止し、VM をシャットダウンする
mc-server SSH ターミナルで、次のコマンドを実行します。

sudo screen -r -X stuff '/stop\n'
GCP Console のナビゲーション メニュー（7a91d354499ac9f1.png）で、[Compute Engine] > [VM インスタンス] をクリックします。
mc-server をクリックします。
[停止] をクリックします。
確認ダイアログで [停止] をクリックして確定します。 SSH セッションからログアウトされます。
インスタンスを再起動するには、インスタンス ページを開き、[起動] をクリックします。Minecraft サーバーを再度起動するには、インスタンスとの SSH 接続を確立し、永続ディスクを再マウントして、新しい screen ターミナルで Minecraft サーバーを起動します。この手順は、前に行った操作と同じです。

起動スクリプトとシャットダウン スクリプトでサーバーのメンテナンスを自動化する
永続ディスクのマウントと screen でのサーバー アプリケーションの起動を手動で行う代わりに、メタデータ スクリプトを使用して起動スクリプトとシャットダウン スクリプトを作成し、これらの作業を自動化できます。

mc-server をクリックします。

[編集] をクリックします。

[カスタム メタデータ] で次のように指定します。

鍵	値
startup-script-url	https://storage.googleapis.com/cloud-training/archinfra/mcserver/startup.sh
shutdown-script-url	https://storage.googleapis.com/cloud-training/archinfra/mcserver/shutdown.sh
[項目を追加] をクリックして shutdown-script-url を追加します。インスタンスを再起動すると、起動スクリプトが自動的に Minecraft ディスクを所定のディレクトリにマウントし、Minecraft サーバーを screen セッションで起動して、セッションを接続解除します。インスタンスを停止すると、シャットダウン スクリプトが Minecraft サーバーをシャットダウンしてから、インスタンスがシャットダウンします。これらのスクリプトは Cloud Storage に保存することをおすすめします。
[保存] をクリックします。
```
