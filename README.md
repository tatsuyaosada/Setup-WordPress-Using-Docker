### [Docker実践編] ローカルPC上にWordPressの開発環境を構築してみよう

<hr>

#### 1. [Docker Desktop](https://www.docker.com/ja-jp/products/docker-desktop/)をインストールする

コントロールパネルから「Windowsの機能と有効化」を開き

- Linux用Windowsサブシステム
- 仮想マシンプラットフォーム

のチェックボックスを両方ともonにします。

※再起動が要求される場合はメッセージの指示に従って下さい。

<hr>

#### 2. [WSL2]()をインストールする

PowerShellかコマンドプロンプトを<strong>管理者権限</strong>で起動します。
> ※スタッフ、インストラクターの権限が必要になるので、その都度お呼び下さい

<code>
wsl --install
</code>

と言うコマンドを実行して下さい。インストールが完了したら

<code>
wsl --version
</code>


> https://learn.microsoft.com/ja-jp/windows/wsl/install

##### 参考文献,資料
> [Docker&仮想サーバー完全入門]() <br>
> https://note.com/ssltokyo_tech/n/n7581b77f2255
