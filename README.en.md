#### Instructions
# 测试分支

#### 介绍
核心流程图
初始化：建立仓库。
开发 v0.1：从 master 切出分支 -> 写代码 -> 合并回 master。
开发 v0.2：再次从 master 切出新分支 -> 写代码 -> 合并回 master。

#### 软件架构
具体操作步骤（复制即可用）
第一阶段：项目启动与 v0.1 开发
假设你刚建好文件夹，或者刚把代码放进去。

#### 安装教程

# 1. 初始化并保存第一版代码（作为基石）
git init
git add .
git commit -m "init: 项目初始化"
# 此时你在 master 分支上

# 2. 开始开发 v0.1 版本
# 【关键】基于当前的 master 创建一个新分支
git checkout -b feature-v0.1

# ... (在这里疯狂写代码，修改文件) ...

# 3. 阶段性保存（在分支里多提交几次没关系）
git add .
git commit -m "feat: 完成v0.1的登录功能"
git add .
git commit -m "fix: 修复v0.1的样式问题"

# 4. 开发完成，准备合并回主分支
git checkout master   # 先回到主分支
git pull origin master # (可选) 确保本地 master 是最新的
git merge feature-v0.1 # 将 v0.1 的改动合入 master

# 5. 推送 master 到远程（如果有远程仓库）
git push origin master




#### 使用说明
第二阶段：开发 v0.2 版本
当你要开发新功能时，千万不要直接在 master 上改，重复上面的步骤：

# 1. 确保你在 master 上，并且是最新的
git checkout master

# 2. 创建 v0.2 的开发分支
# 【关键】一定要从 master 切出来，这样才包含 v0.1 的代码
git checkout -b feature-v0.2

# ... (在这里开发 v0.2 的新功能) ...
git add .
git commit -m "feat: 开发v0.2的数据统计功能"

# 3. 开发完成，合并回主分支
git checkout master
git merge feature-v0.2

# 4. 推送
git push origin master

#### 参与贡献

几个让流程更顺畅的建议
分支命名规范：
不要只叫 0.1，建议加上前缀，比如 feature-0.1、dev-0.2 或者 release-0.1。这样一眼就能看出这是开发分支还是发布分支。
关于“保留版本”：
按照上面的操作，feature-v0.1 这个分支会一直存在于你的本地仓库中。
如果你以后想回头看 0.1 版本刚写完时的样子，可以直接 git checkout feature-v0.1 切换过去看。
如果你觉得分支太多看着乱，可以在合并后删除它（但这会丢失该分支特有的历史记录指针，通常建议保留或打上 Tag）：git branch -d feature-v0.1。
使用 Tag（标签）来标记版本（强烈推荐）：
分支是用来“干活”的，版本是用来“存档”的。当你把 v0.1 合并到 master 后，最好打一个标签，这样以后无论怎么改 master，都能一键回到 v0.1 的状态。

#### 特技

1.  使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2.  Gitee 官方博客 [blog.gitee.com](https://blog.gitee.com)
3.  你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解 Gitee 上的优秀开源项目
4.  [GVP](https://gitee.com/gvp) 全称是 Gitee 最有价值开源项目，是综合评定出的优秀开源项目
5.  Gitee 官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6.  Gitee 封面人物是一档用来展示 Gitee 会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)

