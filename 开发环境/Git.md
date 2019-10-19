# Git

## SSH 公钥

大多数 Git 服务器都会选择使用 SSH 公钥来进行授权。系统中的每个用户都必须提供一个公钥用于授权，没有的话就要生成一个。生成公钥的过程在所有操作系统上都差不多。

```bash
# 直接进入.ssh目录
cd ~/.ssh
ls
```

关键是看有没有用 something 和 something.pub 来命名的一对文件，这个 something 通常就是 id_dsa 或 id_rsa。有 .pub 后缀的文件就是公钥，另一个文件则是密钥。假如没有这些文件，或者干脆连 .ssh 目录都没有，可以用 ssh-keygen 来创建。

```bash
$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/schacon/.ssh/id_rsa): d:/Git/ssh/id_rsa_gitlab
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /Users/schacon/.ssh/id_rsa.
Your public key has been saved in /Users/schacon/.ssh/id_rsa.pub.
The key fingerprint is:
43:c5:5b:5f:b1:f1:50:43:ad:20:a6:92:6a:1f:9a:3a schacon@agadorlaptop.local
```

它先要求你确认保存公钥的位置（d:/Git/ssh/id_rsa_gitlab），然后它会让你重复一个密码两次，如果不想在使用公钥的时候输入密码，可以留空。

现在，所有做过这一步的用户都得把它们的公钥给你或者 Git 服务器的管理员（假设 SSH 服务被设定为使用公钥机制）。他们只需要复制 .pub 文件的内容然后发邮件给管理员。公钥的样子大致如下：

```bash
$ cat d:/Git/ssh/id_rsa_gitlab.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDHZiQ394CcNEdCtmG7A5dxc2hkkYgCB3IfW9440UpuinONDuQClIJsiloETrwXXWFSuunHyFrOJ4yElbCKplbyTu/yuQiXCxsofLE7k1IuGCY5YRyDS384a4Y+imqbZk1FcTobuGQU9bqHYWm/6Wo6SoVco5ELh9fzMREF/8lE/UL5SuPzdTCqUMrOVQtzZdb8u+//dGJ7IHuRRk0qYvHf6rlTPGo/31WXURD2q329B+yDt52I1aclA5DvaNnLx2sK2BhfuAn/w34sTCuR/gtMBO7mJdG+rNTj5Ef7AeWvVsn4iXMBFFWlRVUU9eLKN9bsdFc3zR6Omxo+yITEs10IJPGRjhO95O8VqRHxLe75FA3e61GjKWbEKLGcEW1cHZDi/jypw/N+sT/EZ5nny/ER+PpcljgbLXZfZXH5Ekarc+7tA2grV9ZScdrKQj3QOrWVC81K8ib7faofE69bS/zuFEyB1ppF6gleBfoZI0BJXkeY2czYwdQxhsqK65z6pWU= td-01@DESKTOP-04PS533
```

```bash
eval $(ssh-agent -s)
ssh-add ~/.ssh/other_id_rsa
```

配置SSH host keys

~/.ssh/config下面是一个示例：

```config
Host gitlab.com
  Hostname altssh.gitlab.com
  User git
  Port 443
  PreferredAuthentications publickey
  IdentityFile ~/.ssh/gitlab
```
