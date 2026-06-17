# Git版本管理操作指南

## 目录

- 创建新版本分支
- 合并到主分支
- 完整工作流总结

---

## 创建新版本分支

### 第一步：创建并切换到新分支

**确保当前在master分支上：**

```bash
git checkout master
```

**创建并切换到v0.4分支：**

```bash
git checkout -b v0.4
```

**说明：** `git checkout -b v0.4` 是 `git branch v0.4`（创建分支）和 `git checkout v0.4`（切换分支）的合并简写。执行后终端提示符会显示 `(v0.4)`。

### 第二步：修改代码

在编辑器中打开项目文件（如`index.html`），进行以下修改：

- 更新版本号：`<h3>我是 v0.4 版本</h3>`
- 添加新的CSS样式或内容
- 保存文件

### 第三步：提交更改到本地仓库

**将修改添加到暂存区：**

```bash
git add .
```

**提交更改并添加备注：**

```bash
git commit -m "更新到 v0.4 版本"
```

### 第四步：推送到GitHub

**推送新分支到GitHub远程仓库：**

```bash
git push --set-upstream github v0.4
```

**或使用简写形式（仅限第一次推送）：**

```bash
git push -u github v0.4
```

**注意：** 这里的 `github` 是远程仓库别名，如果配置的是 `origin`，请替换为 `origin`。

### 第五步：验证与后续操作

**验证推送结果：**

1. 刷新GitHub网页
2. 在分支下拉菜单中确认出现 `v0.4` 选项
3. 检查代码是否为最新版本

**合并准备：**
当v0.4开发完成并测试无误后，可以随时合并到master分支：

```bash
git checkout master
git merge v0.4
git push github master
```

---

## 合并到主分支

### 第一步：切回主分支

**切换回master分支：**

```bash
git checkout master
```

**重要：** Git规定只能在主分支上接收合并操作。

### 第二步：执行合并

**将v0.4分支合并到master：**

```bash
git merge v0.4
```

**成功提示：** 如果一切顺利，会显示 `Fast-forward`（快进合并）或 `Merge made by the 'recursive' strategy.'`。

### 第三步：推送到GitHub

**将合并后的master推送到远程仓库：**

```bash
git push github master
```

### 第四步：清理本地分支（可选但推荐）

**删除已合并的v0.4分支：**

```bash
git branch -d v0.4
```

---

## 完整工作流总结

### 标准开发流程

以后每次开发新版本，都按照以下标准操作流程：

1. **创建新版本分支**
2. **修改代码**
    - 在编辑器中进行代码修改
    - 保存所有更改
3. **提交本地更改**
4. **推送到GitHub**
5. **合并到主分支**

### 最佳实践建议

- **保持分支命名规范**：使用 `v版本号` 的格式（如v0.4、v1.0）
- **及时推送**：每次提交后及时推送到远程仓库
- **定期清理**：合并后的分支及时删除，保持仓库整洁
- **测试验证**：在合并前确保新版本功能正常

### 常见问题处理

**分支不存在错误：**
如果遇到 `merge: test-branch - not something we can merge` 错误，说明本地没有该分支，需要先通过 `git fetch` 获取远程分支信息。

**推送权限问题：**
确保远程仓库别名配置正确（`github`或`origin`），并具有推送权限。

---

**文档版本：v1.0**
**最后更新：2024年**

