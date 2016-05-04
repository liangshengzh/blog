title: Mac OS创建的用户在登陆界面中无法显示
date: 2016-03-02 22:04:30
categories: OS
tags:
- Mac OS
---

如果有多人共用一个Mac电脑的情况，比较好的做法是为不同的人创建各自的帐号。在登陆界面可以选择自己
的帐号登陆。但是最近遇到一旦Mac重启之后，除了Mac上的主帐号，其他帐号就会从登陆列表里面消失。


如果你也遇到了这种情况，并且你也启动了[FileVault][]加密，可以尝试以下方法。

1. 打开System Preferences
2. 点击Privacy & Security
3. 选择FileVault Tab

找到Enable Users,然后你就可以启用你想要的帐号了。
![FileVault](/post_images/FileVault.jpg)

这是因为一旦你启动了FileVault加盟，你需要设置哪些用户在启动的时候可以登陆并解锁加密的信息。

在Mac的帮助文档里你也可以找到相关信息.
![FileVault Help](/post_images/mac_filevalut_help.jpg)

Reference:
1. [User account doesn't appear on first login screen](http://apple.stackexchange.com/questions/115670/user-account-doesnt-appear-on-first-login-screen)
[FileVault]: http://baike.baidu.com/view/9077432.htm
