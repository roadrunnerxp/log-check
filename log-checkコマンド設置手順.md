# �ݒu�菇�iGithub�g���Ȃ��Ƃ��j

### root��SSH���O�C��

### /root/bin�f�B���N�g���쐬�i����Εs�v�j

```
# mkdir /root/bin
```

### /root/bin��PATH��ʂ��B

�f�B���N�g���͂Ȃ��Ă�/root/bin�ɂ̓p�X���ʂ��Ă���ۂ��B


```
�m�F
# printenv PATH
/usr/lib64/qt-3.3/bin:/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/root/bin

/root/bin�����݂��Ă����OK

�Ȃ����
# export PATH="$PATH:/root/bin"
```

### �R�}���h�t�@�C���쐬

```
# vim /root/bin/log-check
��vim�N���B

vim��
:set paste	 �\�t�����[�h
�ui�v		�}�����[�h�i�\�t���j���[�h
��log-check�̓��e���y�[�X�g
[Esc]		�ő}�����[�h������
:wq		�ۑ����ďI��

```

### log-check�̃p�[�~�b�V�����ύX

```
# chmod 700 /root/bin/log-check

�m�F
# ls -l /root/bin
-rwx------ 1 root root 4247  5�� 10 14:19 log-check
```

### ���O���X�g�f�B���N�g���i/root/bin/ignorelist�j�̍쐬

```
# log-check -c
���f�B���N�g����lst�t�@�C���̗L�����`�F�b�N���č쐬���Ă���܂��B

�m�F
# ls -l /root/bin
drwxr-xr-x 2 root root   54  5�� 10 14:29 ignorelist
-rwx------ 1 root root 4247  5�� 10 14:19 log-check
```

### ���O���X�g�̕ҏW
```
messages��Grep���O���[�h
# vim /root/bin/ignorelist/messages.lst

secure��Grep���O���[�h
# vim /root/bin/ignorelist/messages.lst

```
�� ���O(grep -v)����������������s��؂��

```
�i��j
# cat /root/bin/ignorelist/messages.lst
systemd
org.freedesktop.problems

# cat /root/bin/ignorelist/secure.lst
192.168.0.11
192.168.0.12
session opened for user
session closed for user
```

### ������
```
# log-check
# log-check -d
�����ƑO�����̃��O�𒊏o
�i�I�v�V�������ȗ������ꍇ-d�Ɠ����j

# log-check -w
�����܂�7�����̃��O�𒊏o
```

