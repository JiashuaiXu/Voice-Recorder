# Git Commit 提交规范

本项目采用 **Gitmoji + Conventional Commits** 组合规范。

## 格式

```
<emoji> <type>(<scope>): <description>

[可选的正文]

[可选的脚注]
```

## 常用 Gitmoji 与 Type 对应表

| Emoji | Code | Type | 说明 |
|-------|------|------|------|
| ✨ | `:sparkles:` | `feat` | 新增功能 |
| 🐛 | `:bug:` | `fix` | 修复 Bug |
| 📝 | `:memo:` | `docs` | 文档更新 |
| 💄 | `:lipstick:` | `style` | UI/样式更新 |
| ♻️ | `:recycle:` | `refactor` | 代码重构 |
| ⚡️ | `:zap:` | `perf` | 性能优化 |
| ✅ | `:white_check_mark:` | `test` | 测试相关 |
| 🔧 | `:wrench:` | `chore` | 配置文件修改 |
| 🔨 | `:hammer:` | `build` | 构建系统或依赖更新 |
| 👷 | `:construction_worker:` | `ci` | CI 配置修改 |
| 🎨 | `:art:` | `style` | 代码格式/结构改进 |
| 🔥 | `:fire:` | `refactor` | 删除代码或文件 |
| 🚑️ | `:ambulance:` | `fix` | 紧急修复 |
| 🌐 | `:globe_with_meridians:` | `feat` | 国际化与本地化 |
| 🔒️ | `:lock:` | `fix` | 安全问题修复 |
| ⬆️ | `:arrow_up:` | `chore` | 升级依赖 |
| ⬇️ | `:arrow_down:` | `chore` | 降级依赖 |
| 📌 | `:pushpin:` | `chore` | 固定依赖版本 |

## 示例

### 新功能
```bash
git commit -m "✨ feat: 添加录音暂停功能"
git commit -m "✨ feat(ui): 添加录音波形可视化"
```

### 修复 Bug
```bash
git commit -m "🐛 fix: 修复录音文件保存失败问题"
git commit -m "🚑️ fix: 紧急修复应用崩溃问题"
```

### 文档更新
```bash
git commit -m "📝 docs: 更新 README 安装说明"
git commit -m "📝 docs(api): 添加 API 文档"
```

### 代码重构
```bash
git commit -m "♻️ refactor: 重构录音引擎代码"
git commit -m "🎨 style: 统一代码格式"
```

### 依赖更新
```bash
git commit -m "⬆️ chore(deps): bump kotlin from 2.0.0 to 2.1.0"
git commit -m "📌 chore: 固定 Gradle 版本"
```

### 性能优化
```bash
git commit -m "⚡️ perf: 优化音频编码性能"
```

### 测试
```bash
git commit -m "✅ test: 添加录音功能单元测试"
```

## 工具推荐

### 1. gitmoji-cli（命令行工具）
```bash
# 安装
npm install -g gitmoji-cli

# 使用
gitmoji -c  # 交互式选择 emoji 并提交
```

### 2. Git 别名（快捷方式）
在 `~/.gitconfig` 中添加：

```ini
[alias]
    cm = !git commit -m
    feat = !git commit -m \"✨ feat:
    fix = !git commit -m \"🐛 fix:
    docs = !git commit -m \"📝 docs:
    style = !git commit -m \"💄 style:
    refactor = !git commit -m \"♻️ refactor:
    perf = !git commit -m \"⚡️ perf:
    test = !git commit -m \"✅ test:
    chore = !git commit -m \"🔧 chore:
```

使用示例：
```bash
git feat "添加新功能"
git fix "修复 bug"
git docs "更新文档"
```

### 3. VS Code 插件
- **Gitmoji** - 提供 emoji 选择器
- **Conventional Commits** - 提供 commit 格式辅助

### 4. 提交模板
创建 `~/.gitmessage` 文件：

```
# <emoji> <type>(<scope>): <subject>
# |<----  建议最多 50 字符  ---->|

# 解释为什么做这个改动
# |<----   每行最多 72 字符   ---->|

# 提供相关 issue 或其他链接
# 例如: Closes #123

# --- COMMIT END ---
# Type 可以是:
#   feat     : 新功能
#   fix      : Bug 修复
#   docs     : 文档更新
#   style    : 格式调整
#   refactor : 重构
#   perf     : 性能优化
#   test     : 测试
#   chore    : 构建/工具变动
# --------------------
```

配置使用模板：
```bash
git config --global commit.template ~/.gitmessage
```

## 最佳实践

1. **使用现在时态**：使用 "添加功能" 而非 "添加了功能"
2. **首行简短**：限制在 50 字符内
3. **必要时添加正文**：详细解释改动原因
4. **关联 Issue**：使用 `Closes #123` 等关键词
5. **原子提交**：每次提交只做一件事

## 参考资料

- [Gitmoji 官方文档](https://gitmoji.dev/)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [Angular Commit Guidelines](https://github.com/angular/angular/blob/master/CONTRIBUTING.md#commit)
