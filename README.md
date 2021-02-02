# Pythonプロジェクトのテンプレート　レベル2

- @author kazurayam
- @date Feb 2021

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
<details>
<summary>Table of Contents</summary>

- [これは何か](#%E3%81%93%E3%82%8C%E3%81%AF%E4%BD%95%E3%81%8B)
- [前提条件](#%E5%89%8D%E6%8F%90%E6%9D%A1%E4%BB%B6)
- [達成目標](#%E9%81%94%E6%88%90%E7%9B%AE%E6%A8%99)
- [手順](#%E6%89%8B%E9%A0%86)
  - [pyenv経由でAnacondaをインストールする](#pyenv%E7%B5%8C%E7%94%B1%E3%81%A7anaconda%E3%82%92%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB%E3%81%99%E3%82%8B)
  - [プロジェクトのためにディレクトリを作る](#%E3%83%97%E3%83%AD%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88%E3%81%AE%E3%81%9F%E3%82%81%E3%81%AB%E3%83%87%E3%82%A3%E3%83%AC%E3%82%AF%E3%83%88%E3%83%AA%E3%82%92%E4%BD%9C%E3%82%8B)
  - [pipenvで仮想環境を作る](#pipenv%E3%81%A7%E4%BB%AE%E6%83%B3%E7%92%B0%E5%A2%83%E3%82%92%E4%BD%9C%E3%82%8B)
    - [pipenvをインストールする](#pipenv%E3%82%92%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB%E3%81%99%E3%82%8B)
    - [プロジェクト固有のPython開発環境を作る](#%E3%83%97%E3%83%AD%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88%E5%9B%BA%E6%9C%89%E3%81%AEpython%E9%96%8B%E7%99%BA%E7%92%B0%E5%A2%83%E3%82%92%E4%BD%9C%E3%82%8B)
    - [外部パッケージを追加する](#%E5%A4%96%E9%83%A8%E3%83%91%E3%83%83%E3%82%B1%E3%83%BC%E3%82%B8%E3%82%92%E8%BF%BD%E5%8A%A0%E3%81%99%E3%82%8B)
    - [プロジェクト固有のPython仮想環境を別マシンで再現する](#%E3%83%97%E3%83%AD%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88%E5%9B%BA%E6%9C%89%E3%81%AEpython%E4%BB%AE%E6%83%B3%E7%92%B0%E5%A2%83%E3%82%92%E5%88%A5%E3%83%9E%E3%82%B7%E3%83%B3%E3%81%A7%E5%86%8D%E7%8F%BE%E3%81%99%E3%82%8B)
    - [開発環境だけで使うパッケージを別枠で管理する](#%E9%96%8B%E7%99%BA%E7%92%B0%E5%A2%83%E3%81%A0%E3%81%91%E3%81%A7%E4%BD%BF%E3%81%86%E3%83%91%E3%83%83%E3%82%B1%E3%83%BC%E3%82%B8%E3%82%92%E5%88%A5%E6%9E%A0%E3%81%A7%E7%AE%A1%E7%90%86%E3%81%99%E3%82%8B)
    - [Pipfileにスクリプトを登録する](#pipfile%E3%81%AB%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%97%E3%83%88%E3%82%92%E7%99%BB%E9%8C%B2%E3%81%99%E3%82%8B)
    - [仮想環境に入ってシェルを実行する](#%E4%BB%AE%E6%83%B3%E7%92%B0%E5%A2%83%E3%81%AB%E5%85%A5%E3%81%A3%E3%81%A6%E3%82%B7%E3%82%A7%E3%83%AB%E3%82%92%E5%AE%9F%E8%A1%8C%E3%81%99%E3%82%8B)
    - [.envの自動読み込み](#env%E3%81%AE%E8%87%AA%E5%8B%95%E8%AA%AD%E3%81%BF%E8%BE%BC%E3%81%BF)
    - [Pipfileからrequirements.txtを生成する](#pipfile%E3%81%8B%E3%82%89requirementstxt%E3%82%92%E7%94%9F%E6%88%90%E3%81%99%E3%82%8B)
  - [IntelliJ IDEAでPythonプロジェクトを開発する準備をする](#intellij-idea%E3%81%A7python%E3%83%97%E3%83%AD%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88%E3%82%92%E9%96%8B%E7%99%BA%E3%81%99%E3%82%8B%E6%BA%96%E5%82%99%E3%82%92%E3%81%99%E3%82%8B)
    - [Platform SDKとして追加する](#platform-sdk%E3%81%A8%E3%81%97%E3%81%A6%E8%BF%BD%E5%8A%A0%E3%81%99%E3%82%8B)
    - [Project SDKとして登録する](#project-sdk%E3%81%A8%E3%81%97%E3%81%A6%E7%99%BB%E9%8C%B2%E3%81%99%E3%82%8B)
  - [ユニットテストを実行する](#%E3%83%A6%E3%83%8B%E3%83%83%E3%83%88%E3%83%86%E3%82%B9%E3%83%88%E3%82%92%E5%AE%9F%E8%A1%8C%E3%81%99%E3%82%8B)
    - [pytestをインストールする](#pytest%E3%82%92%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB%E3%81%99%E3%82%8B)
    - [ユニットテストのコード](#%E3%83%A6%E3%83%8B%E3%83%83%E3%83%88%E3%83%86%E3%82%B9%E3%83%88%E3%81%AE%E3%82%B3%E3%83%BC%E3%83%89)
    - [テストコードを格納するためにディレクトリ構造をどうするか](#%E3%83%86%E3%82%B9%E3%83%88%E3%82%B3%E3%83%BC%E3%83%89%E3%82%92%E6%A0%BC%E7%B4%8D%E3%81%99%E3%82%8B%E3%81%9F%E3%82%81%E3%81%AB%E3%83%87%E3%82%A3%E3%83%AC%E3%82%AF%E3%83%88%E3%83%AA%E6%A7%8B%E9%80%A0%E3%82%92%E3%81%A9%E3%81%86%E3%81%99%E3%82%8B%E3%81%8B)
    - [コマンドラインでpytest実行時にimportがエラーになるで問題](#%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89%E3%83%A9%E3%82%A4%E3%83%B3%E3%81%A7pytest%E5%AE%9F%E8%A1%8C%E6%99%82%E3%81%ABimport%E3%81%8C%E3%82%A8%E3%83%A9%E3%83%BC%E3%81%AB%E3%81%AA%E3%82%8B%E3%81%A7%E5%95%8F%E9%A1%8C)
    - [IntelliJ IDEAのエディタでimportがエラーになる件](#intellij-idea%E3%81%AE%E3%82%A8%E3%83%87%E3%82%A3%E3%82%BF%E3%81%A7import%E3%81%8C%E3%82%A8%E3%83%A9%E3%83%BC%E3%81%AB%E3%81%AA%E3%82%8B%E4%BB%B6)
- [まとめ](#%E3%81%BE%E3%81%A8%E3%82%81)
- [補足](#%E8%A3%9C%E8%B6%B3)
  - [READMEに目次をつけた](#readme%E3%81%AB%E7%9B%AE%E6%AC%A1%E3%82%92%E3%81%A4%E3%81%91%E3%81%9F)

</details>
<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## これは何か

Python言語でプログラムを自作したい。そのために環境を作り道具を揃えて使えるようにする必要がある。アプリケーションが何であれ環境と道具は概ね同じであり、繰り返し利用しつつ磨き上げていくものだ。Python初心者のわたしがやってきた準備作業を細かく記録しつつレポジトリとして保存しよう。さまざまなPythonプロジェクトの雛形として使えるだろう。

Gitレポジトリを4つ作る。

1. [PythonProjectTemplateLevel1](https://github.com/kazurayam/PythonProjectTemplateLevel1) --- Python処理系をインストールする。pipenvで仮想環境を構築する。わたし流のディレクトリ構造を決める。IntelliJ IDEAを設定する。pytestでユニットテストする。
1. [PythonProjectTemplateLevel2](https://github.com/kazurayam/PythonProjectTemplateLevel2) --- つまりこのレポジトリ。わたしのPythonコードをpipでライブラリにしてPyPIにアップロードして共有可能にする。そのライブラリを仕込んだDockerイメージを作りDocker Hubにアップロードして共有可能にする。
1. [PythonProjectTemplateLevel3](https://github.com/kazurayam/PythonProjectTemplateLevel3) --- 単純なWebサーバアプリケーションを作る。Laravelフレームワークで。Dockerイメージを作る。
1. [PythonProjectTemplateLevel4](https://github.com/kazurayam/PythonProjectTemplateLevel4) --- Laravelで作ったWebサーバアプリのユーザインタフェースをSeleniumでテストする。Page Objectモデルで。

このプロジェクトを最初に作るにあたっては [GitHubのレポジトリテンプレート機能](https://dev.classmethod.jp/articles/github-template-repository/) を利用した。すなわちGitHubのサイトで Level1のレポジトリを Template RepositoryとするようチェックボックスをONした。そしてLevel2のレポジトリをNewするにあたって、Level1のレポジトリをTemplate Repositoryとして指定した。するとLevel1のファイルとディレクトリがコピーされて下書きとして使えるようになっていた。便利ですね。

## 前提条件

1. マシンはMac Book Air、OSは macOS 11.1 Big Sur。
1. MacにHomebrewをインストール済み、説明は省略する
1. MacにGitをインストール済み、Git Hubに自分のアカウントを持っていて、Gitの操作に熟達していると前提するので説明は省略する。
1. MacでIntelliJ IDEAを開発環境として使う。IDEAのライセンスを持っていてPythonプラグインをインストール済みと前提する。

## 達成目標

Level2では下記のことを達成目標とする。

1. 自作したPythonアプリケーションをライブラリ化する。つまり任意のマシン上で pip install xxxxx とやればインストールして再利用できるようにする。そのために `setup.py` と `requirements.txt` と `MANIFEST.in` などのファイルを書く。PyPIに自分のためのアカウントを作り、自作したライブラリをPyPIにアップして共有できるようにする。
1. 自作したPythonアプリケーションを組み込んだDockerイメージを作る。Docker Hubに自分のためのアカウントを作り、自作したDockerイメージをDocker Hubにアップして共有できるようにする。

## 手順

Python処理系のインストール、ディレクトリ構造の決定、pipenvで仮想環境を作る、IntelliJ IDEAの設定、pytestによるユニットテストの作成と実行 --- これらについては下記のLevel1のREADMEを参照のこと。

- [PythonProjectTemplateLevel1](https://github.com/kazurayam/PythonProjectTemplateLevel1) 

パッケージ化の手順については下記の記事を参照した。

- [あとで後悔しないPythonのディレクトリ構成をつくってみる](https://qiita.com/kobori_akira/items/aa42790354654debb655)

### Pipfileから仮想環境を再現する

Gitレポジトリから`Pipfile`と`Pipfile.lock`を取得してると前提する。Pipfile.lockに基づいて仮想環境を再現しよう。
```
$repos/pyproject/ $ pipenv install
Installing dependencies from Pipfile.lock (4e9768)...
  🐍   ▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉ 0/5 — 0  🐍   ▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉ 1/5 — 0  🐍   ▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉ 2/5 — 0  🐍   ▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉ 3/5 — 0  🐍   ▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉ 4/5 — 0  🐍   ▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉ 5/5 — 0  🐍   ▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉ 5/5 — 00:00:02
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.
```

これによってこのLevel2プロジェクトのために新しいPython仮想環境が自動的に作られる。

なお新しいPython仮想環境をIntelliJ IDEAの設定に繁栄すべきところがが、自動的に修正されない。手作業で修正せよ。

### コマンドラインで実行可能にしておく

[cli.py](pyproject/src/mypkg/cli.py)を追加します。

```
def execute(name='World'):
    print(f'Hello,{name}!')
```

このプログラムをコマンドラインから実行できるように setup.py に記述します。

### pipでライブラリ化する

#### setup.pyファイルを書く

`$repos/pyproject`ディレクトリの下に [`setup.py`](pyproject/setup.py) ファイルを作る。setup.pyは自作のPythonプログラムをpip installできるライブラリにするのに必須のもの。

ライブラリの名前を決定する。パッケージ名と同じにするのが常道だろう。
```
setup(
    name="mypkg",
```

`src`ディレクトリの下に`mypkg`ディレクトリを作りそのなかに`__init__.py`ファイルを入れておく。中身は空でいい。`mypkg/__init__.py`ファイルを作ることにより`mypkg`がPythonパッケージとして宣言され流。つまり利用者がわのPythonプログラムが

```
from mypkg import ...
```

という風に書けるようになる。`mypkg/__init__.py`ファイルを作り忘れると `from mypkg ...`がエラーになるから注意せよ。

#### Pipfileからrequirements.txtを生成する

pipコマンドでライブラリ化するには [`requirements.txt`](pyproject/requirements.txt) ファイルが必要になる。当該ライブラリを実行するときに必要となる外部ライブラリの名前とバージョンを列挙したファイルである。

下記のコマンドで生成する。

```
$ cd $repo/pyproject
$ pipenv run pip freeze > requirements.txt
```

このテクニックを使えば外部依存ライブラリの管理をPipenvに一元化しつつ、pipコマンドでライブラリ化する作業をすることができます。

#### MANIFEST.inファイルを作る

tarファイルを作るために `python setup.py sdist` コマンドを実行するとき `requirements.txt` ファイルを読み込ませる必要がある。そのために MANIFEST.in を新規作成しておく。

[pyproject/MANIFEST.in](pyproject/MANIFEST.in)

#### ライブラリを作る

```
:~/github/PythonProjectTemplateLevel2/pyproject (master *+)
$ pipenv run python setup.py sdist
```
とやる。するといろいろファイルができる。

```
$ tree .
.
└── pyproject
    ├── MANIFEST.in
    ├── Pipfile
    ├── Pipfile.lock
    ├── dist
    │   └── mypkg-1.0.tar.gz
    ├── mypkg.egg-info
    │   ├── PKG-INFO
    │   ├── SOURCES.txt
    │   ├── dependency_links.txt
    │   ├── entry_points.txt
    │   ├── requires.txt
    │   └── top_level.txt
    ├── requirements.txt
    ├── setup.py
    ├── src
    │   └── mypkg
    │       ├── __init__.py
    │       └── greeting.py
    └── tests
        ├── __init__.py
        ├── conftest.py
        └── test_greeting.py
```

`dist/mypkg-1.0.tar.gz` がPyPIにアップロードされるべきライブラリの実体だ。

#### distディレクトリに作られたtarをpip installしてみる

distディレクトリに作られたtarファイルをPyPIにアップロードする前に、ローカルにpip install してみよう。

```
$repos/pyproject (master *+)
$ pipenv run pip install dist/mypkg-1.0.tar.gz
```

コマンドラインで実行してみよう。

```
$ pipenv run greeting
Hello, World!
```

greetingは引数を1個受けとることができる。

```
$ pipenv run greeting Simon
Hello, Simon!
```

### PyPIにアップロードする

The Python Package Index略してPyPIに自作ライブラリをアップロードすれば、別マシンでそれを pip install xxxxx で簡単にインストールして利用することができます。やりましょう。

#### Twineをインストールする

Twineというツールを使ってPyPIにアップロードします。下記の記事を参考にインストールしよう。

- [Python: Twine を使って PyPI にパッケージをアップロードする](https://blog.amedama.jp/entry/2017/12/31/175036)

```
$repos/pyproject (master *)
$ pipenv run pip install twine
```

#### PyPIに自分のためのアカウントを作る。

本番リリース用のサイト https://pypi.org/ の Register 画面で自分のアカウントを作ろう。

同じくテスト用のサイト https://test.pypi.org/ の Register 画面で自分のアカウントを作ろう。

UsernameとPasswordをメモっておけ。

[`~/.pypirc`](https://packaging.python.org/specifications/pypirc/) ファイルを作る。そこには本番リリース用PyPIのURLとわたしのアカウントに関する情報、テスト用TestPyPIのURLとわたしのアカウントに関する情報を書いておく。これによってtwineコマンドを実行するときにURLやアカウント情報を繰り返し入力する手間を省くことができる。当然ながら~/.pypircファイルを他人の目に晒さないように注意せよ。

#### ビルドしてPyPIにアップロードする

ビルドしてテスト用のPiPIにアップロードしてみよう。

```
$repos/pyproject/ $ pipenv run python setup.py sdist
...
$repos/pyproject/ $ pipenv run twine upload --repository pypitest dist/

$ pipenv run twine upload --repository pypitest dist/*
Uploading distributions to https://test.pypi.org/legacy/
Uploading mypkg-1.0.tar.gz
100%|█████████████████████████████████████]100%|██████████████████████████████████████| 4.13k/4.13k [00:01<00:00, 2.72kB/s]
NOTE: Try --verbose to see response content.
HTTPError: 403 Forbidden from https://test.pypi.org/legacy/
The user 'kazurayam_test' isn't allowed to upload to project 'mypkg'. See https://test.pypi.org/help/#project-name for more information.
```

あれ？エラーになっちゃった。https://test.pypi.org/help/#project-name の説明を読んで考えるに、`mypkg` という名前がよくないのだろう。誰かほかの人がこの名前で作ったことがあって重複しタンだろう。

まあ、こういうエラーが出たということは、PyPIとのやりとりがほとんど成功した証拠だ。いいことにしよう。

#### 

## まとめ

以上でLevel1の準備作業をした。つまり

1. pyenvでPython処理系を複数バージョン、Macにインストールした
2. プロジェクトのディレクトリ構造を決めた
3. pipenvで仮想環境を作り、その仮想環境に本プロジェクのための外部ライブラリをインストールした
4. IntelliJ IDEAを使ってPythonコードを開発できるよう、IDEAを設定した
5. pytestを使ってユニットテストを実行できるように準備した


