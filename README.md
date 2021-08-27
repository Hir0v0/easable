# easable

ECC COMPでのチーム開発作品
dockerとdocker-composeでnginx-proxyコンテナを作成しコンテナ間でURLルーティングを行うサービス

easable
   |
   |-----docker-compose.yml(nginx-proxyの構成ファイル)
   |
   |-----reverse-proxy(プロキシサーバーのコンテナ設定ファイルの格納ディレクトリ)
   |           |
   |           |-----nginx.conf(プロキシサーバー用の設定ファイル)
   |
   |-----web1-server(Webアプリ)
   |           |
   |           |-----docker-compose.yml(web1アプリの設定ファイル)
   |           |
   |           |-----web1-server(webアプリ1のドキュメントルート)
   |
   |-----web2-server(webアプリ)
   |           |
   |           |-----docker-compose.yml(web2アプリの設定ファイル)
   |           |
   |           |-----web2-server(webアプリ2のドキュメントルート)
   |
   |-----certs(SSL証明書の保管場所)
   
   
   上記がディレクトリのツリーと簡単な説明になります。
   
   
   実行する手順としては
   
   1./web1-serverのディレクトリ内でdocker-compose upを実行
   2./web2-serverのディレクトリ内でdocker-compose upを実行
   3./easableのディレクトリ内でdocker-compose upを実行
   
   
   webアプリを増やしたい場合
   1.新しいwebアプリのディレクトリとdocker-compose.tmlファイルを/easableディレクトリ内で作成しdocker-compose upを実行
   2./easable/reverse-proxy内のnginx.confのルーティングルールを追加
   3./easableのディレクトリ内でdocker-compose upを実行
