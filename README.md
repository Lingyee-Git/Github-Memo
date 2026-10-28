# Github-Memo
Github操作备忘

## 配置Git
右键→更多→Git Bash打开终端，在终端输入以下两条命令，用以实现本地代码与github云端仓库的同步
```bash
git config --global user.name "Lingyee-Git"
git config --global user.email "yuan.xinyi456@qq.com"
```
配置完成后可输入`git config --list`查看配置信息

## 配置SSH密钥
实现免密登录，提高操作效率
1. 终端输入命令生成SSH密钥
```bash
ssh-keygen -t rsa -b 4096 -C "yuan.xinyi456@qq.com"
```
2. 执行命令后按3次回车，生成密钥文件
3. 查看并复制公钥：终端输入`cat ~/.ssh/id_rsa.pub`，复制输出的全部内容（从ssh-rsa开始到邮箱结束）
4. 添加公钥到GitHub：Settings→SSH and GPG keys，点击New SSH key，粘贴复制的公钥，填写标题，点击Add SSH key
5. 验证配置：终端输入`ssh -T git@github.com`，若出现"Hi Lingyee-Git! You've successfully authenticated..."说明密钥配置成功

 ## 创建仓库
 1. Repository name：仓库名称
 2. Description：仓库描述
 3. Visibility：仓库类型（Public / Private）
 4. Add a README file：生成README.md文件，用于编写项目说明
 5. Add.gitignore：选择对应语言自动生成.gitignore文件，用于忽略不需要提交的文件
 6. Choose a license：选择项目的开源许可证，明确项目的使用权限

## 克隆仓库到本地
1. 仓库主页点击Code，复制仓库地址（SSH地址）
2. 打开终端，导航到要存放仓库的本地目录`cd 目:/录/地址`
3. 输入克隆命令：`git clone git@github.com:Lingyee-Git/仓库名称.git`，执行后本地目录下会出现与仓库同名的文件夹

## 本地修改并提交代码
1. 进入本地仓库目录：`cd 目:/录/地址`
2. 查看修改状态：`git status`
3. 将修改添加到暂存区：`git add .`，也可以指定添加某个特定文件，如`git add README.md`
4. 提交修改到本地仓库：`git commit -m "提交说明"`
5. 将本地提交推送到GitHub云端仓库：`git push origin main`，main是目标分支，若提交其他分支则修改为对应的名称

## 分支管理与合并
1. 创建并切换到新分支：`git checkout -b 分支名称`
2. 在新分支上修改、提交代码，步骤均同上
3. 应用新分支：进入仓库主页，Settings→Pages→Build and deployment→Branch，选择要应用的分支并Save
4. 合并分支（以合并到main为例）
   - 切换到main分支`git checkout main`
   - 拉取云端main分支最新代码`git pull origin main`
   - 合并新分支到main分支`git merge 分支名称`
   - 将合并后的main分支推送云端`git push origin main`
5. 删除分支：本地删除`git branch -d 分支名称`，云端删除`git push origin --delete 分支名称`
