# Django環境構築

### dajngoのインストール
$ python3 -v\
$ mkdir overview\
$ cd overview\
$ python3 -m venv env\
$ source env/bin/activate\
(env)$

(env)$ pip install django==[バージョン]\
Successfully installed django-[バージョン]\
(env)$ python3 -m django --version

- 仮想環境を終了する時\
$ deactivate

### プロジェクトの作成
$ django-admin startproject mysite\
$ cd mysite

### アプリケーションの作成
$ python3 manage.py startapp news\
$ cd news

### settings.py 編集
- INSTALLED_APPSに'news.apps.NewsConfig'を追記
- LANGUAGE_CODE = 'ja' 編集
- TIME_ZONE = 'Asia/Tokyo'

### モデルからデータベースのテーブルを作成（マイグレーション）
※：モデルを記述後\
$ python3 manage.py makemigrations\
$ python3 manage.py migrate

### ORM操作（対話型シェルでモデル機能を確かめる）
$ python3 manage.py shell\
from news.models import Article, Reporter\
Reporter.objects.all()\
r = Reporter(full_name='John Smith')\
r.save()\
r.id\
Reporter.objects.all()\
<QuerySet [<Reporter: John Smith>]>
a = Article(pub_date=date.today(), headline='Django is cool', content='Year.', reporter=r)

### ユーザ作成
$ python3 manage.py createsuperuser
admin@example.com
