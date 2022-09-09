# Docker-Django-
DockerfileとDocker Composeで簡単なブログサイトを作成
参照: https://docs.docker.jp/compose/django.html

◆大まかな手順（備忘録） ※アプリケーションのセッティングは割愛
1.作業用ディレクトリにDockerfile、docker-compose.yml、requirements.txtファイルを移動
2.docker-compose run web django-admin startproject {プロジェクト名} のコマンドを実行し、コンテナ作成
3.{プロジェクト名}/setting.py のデータベース欄を以下の通りに編集

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'postgres',
        'USER': 'postgres',
        'PASSWORD': 'postgres',
        'HOST': 'db',
        'PORT': 5432,
    }
}

4.docker-compose up コマンドでコンテナ起動、サーバー立ち上げ
5.サーバーを立ち上げた状態で docker ps コマンドで起動中のコンテナの名前を確認
6.docker exec -it {起動中のコンテナの名前} bash コマンドでコンテナに入る
7.code# python3 manage.py startapp {App名} コマンドでアプリケーションのディレクトリを作成
8.code# exit コマンドで一旦コンテナから抜け、各py.ファイルを編集しアプリケーションを完成させる
