```commands
# 在本地创建分支 dev 并拉取 develop 远程分支
git checkout -b dev（本地分支名称） origin/develop（远程分支名称）
```

```commands
# 查看分支
所有分支 git branch -a
本地分支 git branch
远程分支 git branch -r
```

```commands
# 删除分支
git branch -D dev（本地分支名称）
git branch -D dev（本地分支名称）
```

### Windows set multiple accounts

```step
# 删除全局账号配置
git config --global --list
git config --global --unset user.name
git config --global --unset user.email

# 生成 SSH key , rsa/ras.pub 文件
ssh-keygen -t rsa -C "email1@email.com"
ssh-keygen -t rsa -C "email2@email.com"

# Github 部署 SSH key
Github->Settings->SSH and GPG keys->New SSH key->Key 栏中填入 ras.pub 内容
将新 SSH 密钥添加到 ssh-agent
eval $(ssh-agent -s)
ssh-add ~/.ssh/id_rsa

# 测试 SSH 密钥是否生效
ssh -T git@github.com
提示：You've successfully authenticated 表示成功

# 配置 config 文件
Host 　　 主机别名
HostName 　　 服务器真实地址
IdentityFile 　　 私钥文件路径
PreferredAuthentications 　　认证方式
User 　　 用户
Host user1.github.com
HostName github.com
IdentityFile C:\\Users\\{username}\\.ssh\\id_rsa_1
PreferredAuthentications publickey
User user
Host user2.github.com
HostName github.com
IdentityFile C:\\Users\\{username}\\.ssh\\id_rsa_2
PreferredAuthentications publickey
User user2

# 测试 SSH 是否生效
ssh -T git@email1.github.com
ssh -T git@email2.github.com
提示：You've successfully authenticated 表示成功

# 使用远程仓库地址拉取代码
需要使用远程仓库地址，如果原先使用 HTTPS 通信，则需要修改远程仓库地址
每个仓储需要单独配置 name/email
```
