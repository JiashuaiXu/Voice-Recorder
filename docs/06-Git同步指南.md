# Git同步指南

## 问题说明

当你fork了一个GitHub仓库后，上游仓库（原始仓库）会持续更新。为了保持你的fork与上游同步，需要定期同步上游的更改。

## 解决方案

### 第一步：添加上游仓库（首次设置）

如果你还没有配置上游仓库，需要先添加：

```bash
# 添加上游仓库
git remote add upstream https://github.com/FossifyOrg/Voice-Recorder.git

# 验证配置
git remote -v
```

你应该看到：
- `origin`: 你的fork仓库（JiashuaiXu/Voice-Recorder）
- `upstream`: 上游仓库（FossifyOrg/Voice-Recorder）

### 第二步：获取上游更改

```bash
# 获取上游仓库的最新更改
git fetch upstream
```

### 第三步：合并上游更改

#### 方法一：合并（Merge）- 推荐

```bash
# 切换到main分支
git checkout main

# 合并上游的main分支
git merge upstream/main
```

#### 方法二：变基（Rebase）- 保持线性历史

```bash
# 切换到main分支
git checkout main

# 变基到上游的main分支
git rebase upstream/main
```

**注意**: 如果已经推送过，使用rebase后需要强制推送（`git push --force`），请谨慎使用。

### 第四步：推送更改到你的远程仓库

```bash
# 推送合并后的更改
git push origin main
```

## 完整同步流程

```bash
# 1. 确保在main分支
git checkout main

# 2. 获取上游更改
git fetch upstream

# 3. 查看差异（可选）
git log main..upstream/main

# 4. 合并上游更改
git merge upstream/main

# 5. 推送到你的远程仓库
git push origin main
```

## 检查同步状态

### 查看本地和上游的差异

```bash
# 查看上游有你没有的提交
git log main..upstream/main

# 查看你有上游没有的提交
git log upstream/main..main

# 查看所有差异
git log --left-right --oneline main...upstream/main
```

### 查看当前状态

```bash
# 查看当前分支状态
git status

# 查看所有远程分支
git branch -a
```

## 处理冲突

如果合并时出现冲突：

1. **查看冲突文件**:
   ```bash
   git status
   ```

2. **手动解决冲突**:
   - 打开冲突文件
   - 查找 `<<<<<<<`, `=======`, `>>>>>>>` 标记
   - 选择保留的代码或合并两者
   - 删除冲突标记

3. **标记为已解决**:
   ```bash
   git add <冲突文件>
   ```

4. **完成合并**:
   ```bash
   git commit
   ```

## 常见场景

### 场景1：上游更新了，你想同步

```bash
git fetch upstream
git merge upstream/main
git push origin main
```

### 场景2：你在本地有未提交的更改

```bash
# 先保存你的更改
git stash

# 同步上游
git fetch upstream
git merge upstream/main

# 恢复你的更改
git stash pop

# 解决可能的冲突，然后提交
```

### 场景3：你想在上游更新前先提交你的更改

```bash
# 先提交你的更改
git add .
git commit -m "你的提交信息"
git push origin main

# 然后同步上游
git fetch upstream
git merge upstream/main
git push origin main
```

## 自动化脚本（可选）

你可以创建一个脚本来自动化同步过程：

**Windows (sync-upstream.bat)**:
```batch
@echo off
git checkout main
git fetch upstream
git merge upstream/main
git push origin main
```

**Linux/Mac (sync-upstream.sh)**:
```bash
#!/bin/bash
git checkout main
git fetch upstream
git merge upstream/main
git push origin main
```

使用：
```bash
# Windows
sync-upstream.bat

# Linux/Mac
chmod +x sync-upstream.sh
./sync-upstream.sh
```

## 最佳实践

1. **定期同步**: 建议每周或每次开始工作前同步一次
2. **先同步再开发**: 在开始新功能前先同步上游
3. **保持main分支干净**: 在功能分支上开发，main分支只用于同步
4. **查看差异**: 合并前先查看上游有什么更改
5. **测试合并**: 合并后测试确保一切正常

## 工作流程建议

```
1. 开始工作前
   ↓
2. git fetch upstream  (获取上游更新)
   ↓
3. git merge upstream/main  (合并到本地)
   ↓
4. git push origin main  (推送到你的fork)
   ↓
5. 创建功能分支开发
   git checkout -b feature/your-feature
   ↓
6. 开发完成后
   git push origin feature/your-feature
   ↓
7. 在GitHub上创建Pull Request
```

## 故障排除

### 问题1：找不到upstream

```bash
# 检查远程仓库配置
git remote -v

# 如果没有upstream，添加它
git remote add upstream https://github.com/FossifyOrg/Voice-Recorder.git
```

### 问题2：合并后历史混乱

```bash
# 查看提交历史
git log --oneline --graph

# 如果需要，可以重置（谨慎使用）
git reset --hard upstream/main
```

### 问题3：推送被拒绝

```bash
# 先拉取远程更改
git pull origin main

# 解决冲突后再推送
git push origin main
```

## 相关命令速查

| 命令 | 说明 |
|------|------|
| `git remote -v` | 查看远程仓库 |
| `git fetch upstream` | 获取上游更改 |
| `git merge upstream/main` | 合并上游到本地 |
| `git rebase upstream/main` | 变基到上游 |
| `git push origin main` | 推送到你的fork |
| `git log main..upstream/main` | 查看上游新提交 |
| `git status` | 查看当前状态 |

---

**提示**: 定期同步上游仓库可以确保你的fork包含最新的功能和修复。

