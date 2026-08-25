## Step 1: Git 版本控制介绍

假设你和你的团队正在开发一个游戏项目，随着时间的推移，你很快发现整理备份变得困难。而且，由于大家更新项目的方式不同，协作起来非常混乱。

经过一番快速搜索，你了解到 [Git](https://git-scm.com/)。据说它能轻松跟踪变更并与他人协作。它消除了传统方式（如文件名命名规范、共享文件夹和通过邮件来回发送文件）带来的混乱。

> [!IMPORTANT]
> 为了降低学习门槛，本次练习使用云开发环境，已经预装了 Git。如果你想在自己的计算机上安装，请访问[Git 官网](https://git-scm.com/) 获取安装指南。

### 📖 理论知识: 什么是版本控制?

版本控制系统解决了开发者在随时间管理代码变更时面临的常见问题。例如:

- 数据备份和恢复
- 沙盒实验
- 并行开发
- 文件锁定
- 文件复制
- 冲突变更
- 团队协作

如果你经历过下面的场景，那你肯定会爱上 Git 的！😎

- `my-project-final-v2-really3.zip`
- “什么时候这个功能不工作的？我什么都没改啊！”（但你心里清楚你改过）
- “这个文件被锁定了。我先复制一份改着，等他周一回来再处理。”
- “v2 版本在哪封邮件里？好像是上周三的。”

### 什么是 "Git" 版本控制?

Git 是一种[分布式版本控制系统](https://en.wikipedia.org/wiki/Distributed_version_control)，与传统的集中式版本控制系统（如SVN）不同，每个开发者都拥有完整的项目历史副本。

这提供了以下优势:

- **无需联网即可操作** - 大多数操作都是在本地处理的。
- **更高的健壮性** - 分布式的副本相当于多个备份。
- **灵活的工作流程** - 开发者可以使用自己的流程和工具。

### 如何使用 Git?

Git 是开发者们为开发者自己打造的开源软件。因此，社区一直在不断完善各种功能来满足绝大多数需求。

例如，社区已将 Git 融入几乎所有的开发工作流程。以下是一些例子：

- **命令行界面（CLI）** - 原始官方工具。
- **代码编辑器** - 集成在你最喜欢的编辑器/工具里。例如：
  - Visual Studio Code
  - JetBrains IDEs
  - Xcode
  - Emacs/VIM
- **托管服务** - 集中式 Git 托管服务，支持通过 Web 浏览器在线编辑。例如：
  - GitHub
  - GitLab
  - Gitea
  - Azure DevOps
  - AWS CodeCommit
  - BitBucket
- **桌面应用程序** - 友好的图形用户界面。例如：
  - GitHub Desktop
  - Sourcetree
  - TortoiseGit
  - GitKraken
  - Git Butler
  - 还有更多: https://git-scm.com/tools/guis

### ⌨️ 实操环节: 打开示例项目

为了降低学习门槛，下面我们将通过一个预先配置好的云开发环境，来学习如何使用 Git。

1. 右键点击下面的按钮，在一个新标签页中打开 **Create Codespace** 页面。使用默认配置即可。

   [![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/{{full_repo_name}}?quickstart=1)

   > 🪧 **注意**: 通常情况下，[GitHub Codespace](https://github.com/features/codespaces) 会自动包含代码库和所有必需的设置。这是一个修改后的体验，以便您可以从头开始练习。

1. 确认 **Repository** 这一栏是你自己的练习副本，而不是原始仓库，然后单击绿色的 **Create Codespace** 按钮。

   - ✅ 你的副本: `/{{full_repo_name}}`
   - ❌ 原始仓库: `/skills/introduction-to-git`

1. 等待 Visual Studio Code 在浏览器中加载。

1. 在左侧文件浏览器中，右键单击 `src/index.html` 文件，然后选择 **Show Preview**，查看我们的示例游戏。

   > ⚠️ **注意**: 暂时不要做任何改动！我们还没有添加版本控制！ 😱

   <img width="350px" src="https://github.com/user-attachments/assets/c5f60f24-27fb-4670-ab0a-c00aa723672c"/><br/>

   <img width="500px" src="https://github.com/user-attachments/assets/a20529f3-8e42-464b-8d84-b0880dd14383"/>

> [!TIP]
> Feel free to leave the game open and give it more trial-runs as we make changes! 🧑‍🚀

### ⌨️ 实操练习 2: 使用命令行运行 Git

让我们从使用命令行界面（CLI）开始。这是使用 Git 最原始，也是最灵活的方式。

1. 如果尚未打开集成终端，请使用 `Ctrl+Shift+P` 打开终端，然后搜索并选择 `View: Toggle Terminal`

   <img width="500px" src="https://github.com/user-attachments/assets/4bbf918a-f87c-4875-b7fd-61d8b16a70e1"/>

1. 为了验证 Git 是否已成功安装，输入下面的命令，它会显示当前安装的 Git 版本。

   ```bash
   git --version
   ```

   <img width="500px" src="https://github.com/user-attachments/assets/0e09991b-829f-4028-b951-87bc5fa47bfc"/>

1. 下面的命令会显示 Git 的帮助文档。

   ```bash
   git --help
   ```

   <img width="500px" src="https://github.com/user-attachments/assets/c447adf3-9cc1-4106-9a49-f2bf705d396c"/>

### ⌨️ 实操练习 3: 设置 Git 身份

在对我们的游戏进行版本控制之前，得先告诉 Git 咱们是谁，这样以后就能区分每次提交的作者了。

> [!WARNING]
> Git 会在提交历史中存储作者的姓名和电子邮件，该信息对有权访问该存储库的任何人都是可见的。GitHub 提供了一个可选的[ noreply 电子邮件地址](https://docs.github.com/en/account-and-profile/reference/email-addresses-reference#your-noreply-email-address)，您可以在帐户[电子邮件设置](https://github.com/settings/emails)中启用它。

1. 设置你的显示名称。

   ⚠️ 别忘了把 `First` 和 `Last` 换成你自己的名字！

   ```bash
   git config --global user.name "First Last"
   ```

1. 设置你的电子邮件地址。为了保护隐私，你可以考虑在帐户[电子邮件设置](https://github.com/settings/emails)中启用你的 noreply 地址。

   ⚠️ 别忘了把 `me@example.com` 换成你自己的邮箱！

   ```bash
   git config --global user.email "me@example.com"
   ```

1. 确认一下刚才的设置有没有生效。

   ```bash
   git config --global --list
   ```

   <img width="500px" src="https://github.com/user-attachments/assets/62688039-3601-4a23-8f61-408210faff0a"/>

1. 好了，现在 Git 知道你是谁了，Mona 会开始自动检查你的作业。稍等片刻，她会在评论中回复进度与下一步任务。

> [!TIP]
> 如果你有多个账号，也可以为每个项目单独设置用户名和邮箱。在**已有**的项目仓库中，使用 `--local` 替换 `--global` 即可。

<details>
<summary>遇到问题？ 🤷</summary><br/>

- 确保你把 "First Last" 和 "me@example.com" 换成了自己的真实信息。

</details>
