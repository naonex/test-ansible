# 準備
1. docker desktopインストール
2. 【プロキシ環境の場合】docker desktopにプロキシ設定＆docker-compose.yml及び、同階層の`.env`にも設定
3. 【プロキシ環境の場合】ベースとなるイメージをpullしておく（`docker pull centos:7`）
4. docker-compose.ymlの設定値確認。portsのローカル側は空いているポートを設定
5. Dockerfileと同階層（コンテキスト設定階層）のhomeディレクトリに鍵認証に必要なファイルやansible.cfgファイル配置  

# ビルド＆実行
1. docker-compose.ymlのある階層にcdし、`docker-compose up -d --build`を実行
2. 起動後、volumeにansible-user以下の指定ディレクトリ（ansibleプログラム配置階層）と、  
   jenkins設定ファイル階層がマウントされるように設定してます

# おまけ
## 稼働中コンテナにログインする方法例
1. コマンドプロンプトを開く
2. `docker exec -it test-ansible_server_1 bash`コマンド実行

※docker-composeで設定したsshポートフォワードで接続することもできます  
例：`ssh -o "UserKnownHostsFile=/dev/null" -o "StrictHostKeyChecking=no" -p 10022 ansible-user@localhost`  
（dockerは起動毎にホストがリフレッシュされるので、チェック無効オプション付けてます）

## jenkinsログインURL例
http://localhost:8081/

（jenkinsからansible実行できると便利なので突っ込んでます）

## 停止してやり直したい時
以下コマンドでコンテナ＆イメージ削除（ボリュームは開発成果物含まれるので個別に削除推奨）  
`docker-compose down --rmi all`

※次回起動時、ボリューム下以外の変更はリフレッシュされます
