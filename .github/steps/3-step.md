## 步骤 3：探索 Git 历史记录

现在我们的游戏已经由 Git 跟踪，让我们学习如何探索都做了哪些更改、何时做的以及由谁做的。

### 📖 理论: 理解 Git 历史记录

Git 会通过提交(commit)来维护项目的完整历史记录。每次提交都包含以下内容：

- **唯一哈希 ID**: 一个唯一的标识符，方便在历史记录中引用。
- **父提交**: 对前一个提交的引用，形成链条。
- **作者信息**: 谁做的修改。
- **时间戳**: 更改应用的时间。
- **提交消息**: 包含在该提交中所做更改的描述。

此外，`HEAD` 指针是一个特殊的标签，指示你在项目历史中的当前位置。你的项目结构大概如下图所示。

```mermaid
---
config:
  theme: 'forest'
---
gitGraph
   commit id: "9c6ef8a Initial commit"
   commit id: "16ac970 Start game documentation"
   commit id: "762ac02 Start developer docs" tag: "HEAD"
```

### 重要的 Git 命令

每个人查看历史记录的方式不同，社区也创建了许多可选项。
这里列出了一些你将来经常会用到的常用命令和选项。

- `git log` - 显示项目的详细历史记录。
  - `git log --oneline` - 每行一条提交，信息更精简。
  - `git log --graph` - 以可视化的图表形式显示提交历史，这对于分支较多的情况很有帮助。
- `git checkout` - 切换到历史记录中的不同时间点（会修改工作目录中的文件）。

### ⌨️ 实操练习 1: 探索历史记录（使用命令行）

1. 显示详细的提交历史记录。

   ```bash
   git log
   ```

   <img width="500px" src="https://github.com/user-attachments/assets/87e2aa43-7270-4163-a9e6-5ed5f4f1ed63"/>

1. 以单行形式显示每个提交。

   ```bash
   git log --oneline
   ```

   <img width="500px" src="https://github.com/user-attachments/assets/b49a6352-4233-4903-9254-18eaec569895"/>

1. 以可视化的图表形式显示完整的提交历史记录。

   ```bash
   git log --graph --oneline
   ```

   > 🪧 **Note**: This will look more interesting in a future step when the history is longer.

1. 复制 `Initial commit` 条目的 **Commit ID**。长短格式均可用。

1. 使用它切换到早期的版本。

   ```bash
   git checkout <commit id>
   ```

   <img width="500px" src="https://github.com/user-attachments/assets/4d0f6660-e689-47a2-874e-c3d71b32975b"/><br/>

   🪧 注意：`README.md` 文件已被移除。
   
   <img width="350px" src="https://github.com/user-attachments/assets/65091c64-3bef-47ad-a4ff-82f3260aa903"/>

1. 切换回 `main` 上的最新提交。注意 `README.md` 文件又回来了。 🧐

   ```bash
   git checkout main
   ```

   <img width="350px" src="https://github.com/user-attachments/assets/5814f14b-fbf5-4090-90f6-32f815f8b773"/><br/>

   <img width="350px" src="https://github.com/user-attachments/assets/fd673876-ca3b-4184-9f7f-c4bf3ae388a6"/>

### ⌨️ 实操练习 2: 探索历史记录（使用 VS Code）

1. 在左侧导航栏中，打开 **Source Control**（源代码管理）选项卡。

1. 右键单击 **Changes**（变更）标题并选择 **Graph**（图表）选项。

   <img width="350px" src="https://github.com/user-attachments/assets/c5bfb32d-198a-4baa-9ae5-156ee283256c"/>

1. 检查 **Graph**（图表）面板。注意最近提交的时间线列表。

   <img width="350px" src="https://github.com/user-attachments/assets/860f780f-98ca-4c0e-bb0f-e7d65fb84a67"/><br/>

1. 点击提交名称，展开该提交修改过的文件列表。

   <img width="350px" src="https://github.com/user-attachments/assets/42310a18-84a4-4dca-8f45-18d589e187c0"/>

1. 探索完 Git 历史记录后，Mona 应该已经在检查你的作业了。给她一点时间，继续关注评论。你将看到她回复进度信息和后续步骤。

<details>
<summary>遇到问题了？🤷</summary><br/>

- 使用 `git log --help` 查看所有可用的历史记录查看选项。

</details>
