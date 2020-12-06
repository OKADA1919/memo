# LAMP Webサーバーを建ててWordPressを動かす
##### LAMPはLinux,Apache,MySQL,PHPの頭文字を合わせたもの

## 1.下準備
ラズパイの環境を最新バージョンにアップデートしておく。
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

## 2.Apacheインストール
Apatch(アパッチ)はフリーでオープンソースのWebサーバーソフトウェア。
```
sudo apt-get install apache2 -y
```
インストールが完了したらWebブラウザで下記アドレスにアクセスするとデフォルトのindex.htmlが見れるはず。
```
http://ラズパイのIPアドレス
```
ラズパイのIPアドレスを見つけるには下記コマンドでも見れる。
```
hostname -I
```
デフォルトのindex.htmlのディレクトリは下記。
```
/var/www/html/index.html
```

## 3.PHPインストール
PHPは、動的にWebページを生成できるサーバーサイドのスクリプト言語。動的なWebページとは、アクセスしたタイミングや状況によって表示される内容が変わるページの事とする。掲示板や問い合わせフォーム、ECサイトのショッピングカートなどがまさにそれだ。
```
sudo apt-get install php -y
```

## 4.MySQL(MariaDB)インストール
MySQLは、データベース管理システム。データの保管、更新、削除、検索を行う。ぶっちゃけよくわからん。MariaDBはMySQLの派生システムで互換性がある。今回はMariaDBとPHP-MySQLパッケージの２つをインストールする。
```
sudo apt-get install mariadb-server php-mysql -y
```
インストールが完了したらApacheを再起動。
```
sudo service apache2 restart
```

## 5.WordPressダウンロード
WordPressは、Webサイト作成の特別な知識がなくても簡単なブログから本格的なWebサイトまで簡単に作成できるコンテンツマネジメントシステム(CMS)。

下記ディレクトリに移動してファイルを消去する。
```
cd /var/www/html
sudo rm *
```
WordPressをダウンロード。
```
sudo wget http://wordpress.org/latest.tar.gz
```
からの解凍。
```
sudo tar xzf latest.tar.gz
```
mvコマンドでwordpressフォルダ内の全てのファイルを現在のカレントディレクトリ(/var/www)へ移動させる。
```
sudo mv wordpress/* .
```
空になったwordpressフォルダと解凍前のファイルlatest.tar.gzを削除する。
```
sudo rm -rf wordpress latest.tar.gz
```
下記コマンドで何が入ってるかツリー表示できたりする。
```
tree -L 1
```
そしておまじない
```
sudo chown -R www-data: .
```

## 6.WordPressのデータベースをセットアップ
### MySQL/MariaDBセットアップ
WordPressサイトをセットアップするにはデータベースが必要だ。
```
sudo mysql_secure_installation
```
rootのパスワードを聞かれるので入力。

ホンマにこれかと聞かれるのでyと入力。

WordPressのパスワードを入力。

Remove anonymous usersはyと入力。

Disallow root login remotelyはyと入力。

Remove test database and access to itはyと入力。

Reload privilege tables noはyと入力。

これを済ませるとAll done! Thanks for using MariaDB!と表示される。

### WordPressデータベースを作る
```
sudo mysql -uroot -p
```
rootで設定したパスワードを入力して以下のコマンドを入力。
```
create database wordpress;
```
下記が表示されたら成功。
```
Query OK, 1 row affected(0.00sec)
```
以下のおまじないを入力。
```
GRANT ALL PRIVILEGES ON wordpress.* TO 'root'@'localhost' IDENTIFIED BY 'さっき設定したパスワード';
```
```
FLUSH PRIVILEGES;
```

ctrl+DでMariaDBを終了させてラズパイを再起動する。
```
sudo reboot
```

## 7.WordPressの設定
### ラズパイのipアドレスを固定する
現在割り当てられているIPアドレスの確認
```
ifconfig
```
![ifconfig](https://github.com/OKADA1919/memo/blob/master/images/Raspberry_pi/ifconfig1.png?raw=true)

無線LANを利用している場合、wlan0のセクションを確認。
（有線LANの場合は、eth0を確認。）

上から2行目に、"inet 10.0.1.7" と書いてあり、これがいま割り当てられているIPアドレスとなる。

固定IPアドレスを設定する際は、デフォルトゲートウェイとDNSサーバーのIPアドレスも必要になるため、これらも先に確認しておく事。

次に、固定IPアドレスを設定するためのファイルを編集する。
```
sudo nano /etc/dhcpcd.conf
```
ファイルを開いたら、一番下までスクロールし、下記の項目を追加。
```
interface wlan0
static ip_address=ラズパイのIPアドレス
static routers=デフォルトゲートウェイのIPアドレス
static domain_name_servers=DNSサーバーのIPアドレス
```
入力が終わったら、設定ファイルを上書き保存して閉じてラズパイを再起動。
```
sudo reboot
```

### WordPressの設定
WebブラウザでラズパイのIPアドレスにアクセスする。
```
http://ラズパイのIPアドレス
```
![wordpress](https://github.com/OKADA1919/memo/blob/master/images/Raspberry_pi/wordpress1.png?raw=true)
言語を選択して、次へ。
![ifconfig](https://github.com/OKADA1919/memo/blob/master/images/Raspberry_pi/ifconfig2.png?raw=true)
さあ、始めましょう！をポチ。
![ifconfig](https://github.com/OKADA1919/memo/blob/master/images/Raspberry_pi/ifconfig3.png?raw=true)
項目を埋めていく。
```
Database Name:      wordpress
User Name:          root
Password:           さっき決めたパスワード
Database Host:      localhost
Table Prefix:       wp_
```
