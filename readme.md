## Description

�����`�F�b�N�p�R�}���h

## �T�v

### DF�R�}���h

`df -h`

### ���O�̒��o

`grep -h "$GrepDays" $FileName |grep -vf /root/bin/ignorelist/messages.lst |tac`

+ 2����or7���Ԃ̃��O�𒊏o�i�I�v�V�����őI���j

`GrepDays=$(date "+%b %e")"\|"$(date -d "$CheckDay 1day ago")`

```
while [ "$CheckDay" != "$StartDay" ]; do
    GrepDays=$GrepDays"\|"
    CheckDay=$(date -d "$CheckDay 1day ago")
    GrepDays=$GrepDays$(date -d "$CheckDay" "+%b %e")
done
```

+ 1����O�̃��O�t�@�C�����`�F�b�N�ΏۂɊ܂߂�

`FileName=$(ls -t1 /var/log/messages*|head -2)`

+ IgnoreList�ɂ���P����܂ލs�͖���

+ �t���ɏo�́i���߂̃��O����ɗ���j

## ����

### /root/bin/�f�B���N�g���ɔz�u�B

```
# cd /root/bin
# git clone git@github.com:roadrunner/log-check.git
```
+ /root/bin�f�B���N�g���Ƀp�X��ʂ��Ă���

### /root/bin/ignorelist�f�B���N�g�����K�v

+ log-check -c �Ŋm�F�E�쐬��

## �g�p���@

```
# log-check -h

Usage:
  ${0##*/} [-d][-w][-h]
Options�F
  -d           ��������ёO�����̃��O���璊�o���܂��B
  -w           �������܂�7���ԕ��̃��O���璊�o���܂��B
  -c           ���O���X�g�f�B���N�g���̃`�F�b�N�E�쐬
  -h           �w���v�E�g�p���@
```
