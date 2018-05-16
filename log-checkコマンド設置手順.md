# 設置手順（Github使えないとき）

### rootでSSHログイン

### /root/binディレクトリ作成（あれば不要）

```
# mkdir /root/bin
```

### /root/binにPATHを通す。

ディレクトリはなくても/root/binにはパスが通ってるっぽい。


```
確認
# printenv PATH
/usr/lib64/qt-3.3/bin:/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/root/bin

/root/binが存在していればOK

なければ
# export PATH="$PATH:/root/bin"
```

### コマンドファイル作成

```
# vim /root/bin/log-check
でvim起動。

vimで
:set paste	 貼付けモード
「i」		挿入モード（貼付け）モード
→log-checkの内容をペースト
[Esc]		で挿入モード抜ける
:wq		保存して終了

```

### log-checkのパーミッション変更

```
# chmod 700 /root/bin/log-check

確認
# ls -l /root/bin
-rwx------ 1 root root 4247  5月 10 14:19 log-check
```

### 除外リストディレクトリ（/root/bin/ignorelist）の作成

```
# log-check -c
※ディレクトリとlstファイルの有無をチェックして作成してくれます。

確認
# ls -l /root/bin
drwxr-xr-x 2 root root   54  5月 10 14:29 ignorelist
-rwx------ 1 root root 4247  5月 10 14:19 log-check
```

### 除外リストの編集
```
messagesのGrep除外ワード
# vim /root/bin/ignorelist/messages.lst

secureのGrep除外ワード
# vim /root/bin/ignorelist/messages.lst

```
※ 除外(grep -v)したい文字列を改行区切りで

```
（例）
# cat /root/bin/ignorelist/messages.lst
systemd
org.freedesktop.problems

# cat /root/bin/ignorelist/secure.lst
192.168.0.11
192.168.0.12
session opened for user
session closed for user
```

### お試し
```
# log-check
# log-check -d
当日と前日分のログを抽出
（オプションを省略した場合-dと同等）

# log-check -w
当日含め7日分のログを抽出
```

