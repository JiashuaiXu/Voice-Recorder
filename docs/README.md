# Voice Recorder 项目文档

欢迎！这是Fossify Voice Recorder项目的完整文档，专为Kotlin开发新手设计。

## 文档导航

### 📚 文档列表

0. **[快速参考](./00-快速参考.md)** ⚡
   - 快速查找常用信息
   - 编译命令速查
   - 关键常量速查
   - 常见问题速查

1. **[项目概述](./01-项目概述.md)**
   - 项目简介和主要功能
   - 技术栈
   - 项目结构概览

2. **[项目架构](./02-项目架构.md)**
   - 架构模式说明
   - 核心组件层次
   - 数据流和通信机制
   - 设计模式应用

3. **[依赖关系](./03-依赖关系.md)**
   - 外部依赖库详解
   - 依赖版本管理
   - 依赖关系图
   - 依赖冲突处理

4. **[核心模块详解](./04-核心模块详解.md)**
   - 录制模块（Recorder）
   - 服务模块（Service）
   - UI模块（Fragment）
   - 适配器模块（Adapter）
   - 配置模块（Config）
   - 扩展函数模块（Extensions）
   - 辅助类模块（Helpers）
   - 事件模型（Events）

5. **[编译指南](./05-编译指南.md)**
   - 环境要求
   - 环境配置步骤
   - 编译步骤（Android Studio和命令行）
   - 签名配置
   - 常见问题解决

6. **[Git同步指南](./06-Git同步指南.md)**
   - 同步上游仓库的方法
   - 处理冲突
   - 最佳实践
   - 常见问题解决

## 快速开始

### 对于Kotlin新手

如果你是Kotlin开发新手，建议按以下顺序阅读：

1. **先读项目概述** - 了解项目是做什么的
2. **再看编译指南** - 先让项目跑起来
3. **然后看项目架构** - 理解整体设计
4. **最后看核心模块** - 深入理解实现细节

### 学习建议

1. **边看边实践**
   - 阅读文档时，打开对应的源代码文件
   - 尝试修改代码，观察效果
   - 使用Android Studio的调试功能

2. **理解设计模式**
   - 注意项目中使用的设计模式
   - 思考为什么这样设计
   - 尝试应用到自己的项目中

3. **关注通信机制**
   - EventBus的使用方式
   - Intent通信
   - 组件生命周期

4. **学习Kotlin特性**
   - 扩展函数（Extensions）
   - 数据类（Data Classes）
   - 协程（如果使用）
   - Lambda表达式

## 项目关键概念

### 1. Android组件

- **Activity**: 用户界面的单一屏幕
- **Fragment**: 可重用的UI组件
- **Service**: 后台服务，用于长时间运行的任务
- **BroadcastReceiver**: 接收系统广播

### 2. 架构模式

- **MVC**: Model-View-Controller
- **观察者模式**: EventBus实现
- **策略模式**: Recorder接口的不同实现

### 3. 通信方式

- **EventBus**: 组件间解耦通信
- **Intent**: Activity和Service之间的通信
- **接口回调**: Fragment和Activity之间的通信

## 代码阅读建议

### 推荐的阅读顺序

1. **从入口开始**
   - `SplashActivity.kt` - 应用启动
   - `MainActivity.kt` - 主界面

2. **理解数据模型**
   - `Recording.kt` - 录音数据模型
   - `Events.kt` - 事件模型
   - `Config.kt` - 配置管理

3. **学习核心功能**
   - `RecorderService.kt` - 录制服务
   - `Recorder.kt` 及其实现 - 录制逻辑
   - `RecorderFragment.kt` - 录制界面

4. **理解UI交互**
   - `PlayerFragment.kt` - 播放界面
   - `RecordingsAdapter.kt` - 列表适配器

## 常见问题

### Q: 如何开始修改代码？

A: 
1. 先确保项目能正常编译运行
2. 从小的修改开始，比如改变文字颜色
3. 理解修改的影响范围
4. 使用Git进行版本控制

### Q: 如何添加新功能？

A:
1. 确定功能属于哪个模块
2. 参考现有代码的实现方式
3. 遵循项目的代码风格
4. 测试新功能

### Q: 如何调试应用？

A:
1. 使用Android Studio的调试器
2. 添加日志输出（Log.d）
3. 使用断点
4. 查看Logcat输出

### Q: 如何理解EventBus？

A:
1. EventBus是一个事件总线
2. 组件可以发送事件（post）
3. 其他组件可以订阅事件（subscribe）
4. 实现组件间的解耦通信

### Q: 如何保持fork与上游同步？

A:
1. 添加上游仓库：`git remote add upstream https://github.com/FossifyOrg/Voice-Recorder.git`
2. 获取上游更改：`git fetch upstream`
3. 合并到本地：`git merge upstream/main`
4. 推送到你的fork：`git push origin main`
5. 详细说明请查看 [Git同步指南](./06-Git同步指南.md)

## 资源链接

- [Kotlin官方文档](https://kotlinlang.org/docs/home.html)
- [Android开发者指南](https://developer.android.com/guide)
- [EventBus文档](https://greenrobot.org/eventbus/)
- [Gradle用户指南](https://docs.gradle.org/current/userguide/userguide.html)

## 保持与上游同步

如果你fork了这个项目，需要定期同步上游仓库的更新：

### 快速同步步骤

```bash
# 1. 确保在main分支
git checkout main

# 2. 获取上游更改
git fetch upstream

# 3. 合并上游更改
git merge upstream/main

# 4. 推送到你的远程仓库
git push origin main
```

### 首次设置上游仓库

如果还没有配置上游仓库：

```bash
# 添加上游仓库
git remote add upstream https://github.com/FossifyOrg/Voice-Recorder.git

# 验证配置
git remote -v
```

### 注意事项

1. **定期同步**: 建议每周或每次开始工作前同步一次
2. **先同步再开发**: 在开始新功能前先同步上游
3. **保持main分支干净**: 在功能分支上开发，main分支只用于同步
4. **查看差异**: 合并前先查看上游有什么更改（`git log main..upstream/main`）
5. **测试合并**: 合并后测试确保一切正常

### 处理冲突

如果合并时出现冲突：
1. 查看冲突文件：`git status`
2. 手动解决冲突（查找 `<<<<<<<`, `=======`, `>>>>>>>` 标记）
3. 标记为已解决：`git add <冲突文件>`
4. 完成合并：`git commit`

**详细说明**: 查看 [Git同步指南](./06-Git同步指南.md)

## 贡献指南

如果你想为项目做贡献：

1. Fork项目
2. 同步上游仓库（见上方说明）
3. 创建功能分支：`git checkout -b feature/your-feature`
4. 编写代码并测试
5. 提交更改：`git commit -m "描述你的更改"`
6. 推送到你的fork：`git push origin feature/your-feature`
7. 在GitHub上创建Pull Request

## 许可证

本项目采用开源许可证，详情请查看项目根目录的LICENSE文件。

---

**祝你学习愉快！** 🎉

如有问题，可以：
- 查看项目Issues
- 阅读源代码注释
- 参考Android官方文档

