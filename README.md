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
アカウントを要求されるウィザード

これでDocker Desktopのインストールは完了です。

<hr>

#### 3.DockerにWordPressをインストールしてみよう

> [https://note.com/ssltokyo_tech/n/n7581b77f2255](https://note.com/ssltokyo_tech/n/n7581b77f2255)

このページを参考にしながら進めて見てください。

<hr>

##### 参考文献
> [Docker&仮想サーバー完全入門]() <br>

##### 資料資料
> https://qiita.com/tatsuya-tamura-business/items/7356508137ece45caca4
> https://note.com/ssltokyo_tech/n/n7581b77f2255
