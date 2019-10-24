# 添加SSH Key

终端输入以下命令:

```shell
cd ~/.ssh/
ssh-keygen -o -t rsa -b 4096 -C "邮箱"
```

会出现以下提示:

```shell
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/xxx/.ssh/id_rsa):xxx
```

>  命名可自己随意输入，也可直接回车采用默认命名(id_rsa).

后面会要求输入描述和密码，直接回车。

顺利的话会生成 xxx 和 xxx.pub



然后用编辑器打开`~/.ssh/config`文件，没有就手动创建。填入以下内容并保存

```bash
# 邮箱 gitlab.funi.local
Host gitlab.funi.local  # 这个名字可任意设置
  HostName gitlab.funi.local
  User xxx
  IdentityFile ~/.ssh/sshakey名（不带.pub)
```



打开gitlab.funi.local，头像-设置.

![image-20191015095515125](/Users/you/Library/Application Support/typora-user-images/image-20191015095515125.png)

然后在左侧边栏找到`SSH Keys`。

再回到终端:

```shell
cat ~/.ssh/xxx.pub //xxx表示之前生成的sshkey名字
```

复制公钥内容，打开gitlab，粘贴到以下地方.

<img src="/Users/you/Library/Application Support/typora-user-images/image-20191015100010707.png" alt="image-20191015100010707" style="zoom: 33%;" />