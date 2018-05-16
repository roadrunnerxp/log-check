## Description

日次チェック用コマンド

## 概要

### DFコマンド

`df -h`

### ログの抽出

`grep -h "$GrepDays" $FileName |grep -vf /root/bin/ignorelist/messages.lst |tac`

+ 2日間or7日間のログを抽出（オプションで選択）

`GrepDays=$(date "+%b %e")"\|"$(date -d "$CheckDay 1day ago")`

```
while [ "$CheckDay" != "$StartDay" ]; do
    GrepDays=$GrepDays"\|"
    CheckDay=$(date -d "$CheckDay 1day ago")
    GrepDays=$GrepDays$(date -d "$CheckDay" "+%b %e")
done
```

+ 1世代前のログファイルもチェック対象に含める

`FileName=$(ls -t1 /var/log/messages*|head -2)`

+ IgnoreListにある単語を含む行は無視

+ 逆順に出力（直近のログが上に来る）

## 準備

### /root/bin/ディレクトリに配置。

```
# cd /root/bin
# git clone git@github.com:roadrunner/log-check.git
```
+ /root/binディレクトリにパスを通しておく

### /root/bin/ignorelistディレクトリが必要

+ log-check -c で確認・作成可

## 使用方法

```
# log-check -h

Usage:
  ${0##*/} [-d][-w][-h]
Options：
  -d           当日および前日分のログから抽出します。
  -w           当日を含む7日間分のログから抽出します。
  -c           除外リストディレクトリのチェック・作成
  -h           ヘルプ・使用方法
```
