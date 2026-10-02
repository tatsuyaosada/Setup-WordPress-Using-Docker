### [Docker実践編] ローカルPC上にWordPressの開発環境を構築してみよう

<hr>

#### 1. [Docker Desktop](https://www.docker.com/ja-jp/products/docker-desktop/)をインストールする手順

1-1.コントロールパネルから「Windowsの機能と有効化」を開き

- Linux用Windowsサブシステム
- 仮想マシンプラットフォーム

のチェックボックスを両方ともonにします。

※再起動が要求される場合はメッセージの指示に従って下さい。

1-2.[WSL2](https://learn.microsoft.com/ja-jp/windows/wsl/install)をインストールする

PowerShellかコマンドプロンプトを<strong>管理者権限</strong>で起動します。
> ※スタッフ、インストラクターの権限が必要になるので、その都度お呼び下さい

<code>
wsl --install
</code>

と言うコマンドを実行して下さい。少々時間が掛かります。インストールが完了したら

<code>
wsl --version
</code>


で、wslのバージョンが2.0以上になってる事を確認して下さい。

> https://learn.microsoft.com/ja-jp/windows/wsl/install

<hr>

#### 2. [Docker Desktop](https://www.docker.com/ja-jp/products/docker-desktop/)本体をインストールする

2-1. [公式ページ](https://www.docker.com/ja-jp/products/docker-desktop/)より、クライアントをダウンロードします。
幾つか種類がありますが「<strong>Windows用をダウンロード - AMD64</strong>」を選択して下さい。ダウンロードが完了したら、インストーラを走らせます。

2-2.「<strong>Use WSL2 instead of Hyper-V (recommend)</strong>」にチェックが入っている事を確認した後、指示に従って下さい。

これでDocker Desktopのインストールは完了です。起動するとライセンス規約への同意に続きアカウント作成画面になりますが、Skipで飛ばして下さい。
その後、職業調査の様なアンケートへの入力を求められますが、適当で構いません。

<hr>

#### 3.DockerにWordPressをインストールしてみよう

> [https://note.com/ssltokyo_tech/n/n7581b77f2255](https://note.com/ssltokyo_tech/n/n7581b77f2255)

基本的にはこのページを参考にしながら進めて見てください。

3-1. 任意の場所に作業ディレクトリを作成して下さい。GUIからでもコマンドからでも構いません。
3-2. 3-1で作成したディレクトリに、<code>docker-compose.yml</code>と言うファイルを作り、中身に以下をコピペします。

<details><summary>docker-compose.ymlのコード</summary>

```yml
services:
  db:
    image: mysql:5.7
    container_name: mysql
    restart: always
    volumes:
      - db_data:/var/lib/mysql
    environment:
      MYSQL_ROOT_PASSWORD: rootpass
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wpuser
      MYSQL_PASSWORD: wppass

  wordpress:
    image: wordpress:latest
    container_name: wordpress
    depends_on:
      - db
    restart: always
    ports:
      - "8080:80"
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wpuser
      WORDPRESS_DB_PASSWORD: wppass
      WORDPRESS_DB_NAME: wordpress
    volumes:
      - wordpress_data:/var/www/html

  phpmyadmin:
    image: phpmyadmin/phpmyadmin:latest
    container_name: phpmyadmin
    depends_on:
      - db
    restart: always
    ports:
      - "8081:80"
    environment:
      PMA_HOST: db
      PMA_USER: wpuser
      PMA_PASSWORD: wppass
      UPLOAD_LIMIT: 64M

volumes:
  db_data:
  wordpress_data:
```
</details>

3-3. コマンドプロンプトかPowerShellで、該当の作業ディレクトリに移動した後、以下のコマンドを投げます。

<code>docker compose up -d</code>

これでWordPressとそれに必要なコンポーネントがコンテナ上に生成され、起動しました。試しに http://localhost:8080 にアクセスしてみましょう。WordPressの初期設定画面が表示されれば成功です。尚、 http://localhost:8081 にアクセスするとPhpmyadminになります。

#### 4.
TODO::

##### 参考文献
> [Docker&仮想サーバー完全入門]() <br>

##### 資料資料
> https://zenn.dev/upgradetech/articles/8e8b82e9d5c494
> https://qiita.com/tatsuya-tamura-business/items/7356508137ece45caca4
> https://note.com/ssltokyo_tech/n/n7581b77f2255
