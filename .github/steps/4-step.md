## 步骤 4：比较变更

现在我们已经学会了如何“撤销”，接下来我们对游戏做一些真正的改动！更重要的是，学习如何在提交到仓库历史**之前**使用 Git 查看到底改了什么。

理解文件差异对于审查你的工作和发现错误至关重要！

### 📖 理论: 差异对比（diffs）

Git 使用不同的符号和颜色来标记文件更改：

- 绿色 `+` 表示添加的行
- 红色 `-` 表示删除的行

示例:

```diff
+ This is a line that was added
- This is a line that was removed
```

> [!TIP]
> 你可以使用以下命令更改 Git 的默认比较颜色。
>
> ```bash
> git config --global color.diff.old yellow
> git config --global color.diff.new blue
> ```

### 重要的 Git 命令

`git diff` 命令用于显示不同开发状态之间的差异。

- `git diff` - 显示工作目录和暂存区之间的差异。
- `git diff --staged` - 显示暂存区和上一次提交之间的差异。
- `git diff HEAD~1` - 显示当前提交和上一次提交之间的差异。

### ⌨️ 实操练习 1: 差异对比（使用 CLI）

让我们对游戏做一些改动，然后使用命令行来显示差异。

1. 打开 `src/index.html`。

2. 在 `line 20` 处，用下面的例子替换 `info-section` 部分。

   ```txt
   <div class="info-section">
      <h3>Current Score</h3>
      <div class="score" id="score">0</div>
      <h3>High Score</h3>
      <div class="high-score" id="high-score">0</div>
   </div>
   ```

   这演示了 3 处修改：

   - 将 `Score` 标签修改为 `Current Score`
   - 添加 `High Score` 信息。
   - 移除 `status` 信息。

3. 查看当前工作目录和上一次提交之间的差异。

   ```bash
   git diff src/index.html
   ```

   <img width="500px" src="https://github.com/user-attachments/assets/f41d6917-1651-4549-bb7b-5441a1832e38"/>

1. 将更改添加到到暂存区。

   ```bash
   git add src/index.html
   ```

5. 再次运行 `git diff`。注意，现在没有显示任何更改，因为工作目录已经和暂存区保持一致。

   ```bash
   git diff src/index.html
   ```

1. 查看暂存区和上一次提交之间的差异。

   ```bash
   git diff --staged src/index.html
   ```

   <img width="500px" src="https://github.com/user-attachments/assets/f6aad38c-56fa-49ed-8209-9fe249c209ff"/>

1. 现在提交暂存区的更改，提交消息如下。

   ```md
   git commit -m "Add element for showing high score"
   ```

   <img width="500px" src="https://github.com/user-attachments/assets/8381b943-ca22-4b22-97b5-4520e174fc4c"/>

### ⌨️ 实操练习 2: 差异对比（使用 VS Code）

让我们对游戏做一些改动，然后使用 VS Code 来显示差异。

1. 打开 `src/patterns.js`。

1. 在 `line 3` 处，用下面的例子替换 `Null Pointer` 的 `pattern`。

   ```txt
   {
     name: "Null Pointer",
     pattern: [
       [0, 1, 1, 1, 0],
       [0, 1, 0, 1, 0],
       [0, 1, 1, 1, 0],
       [0, 0, 1, 0, 0],
       [0, 0, 1, 0, 0],
     ],
   },
   ```

1. 在 `文件资源管理器` 中，注意 `patterns.js` 文件名颜色改变了，并且旁边显示了 `M`，表示它已被修改。

   <img width="350px" src="https://github.com/user-attachments/assets/93a8f34c-9b16-4783-bc46-81532cdeffdf"/>

1. 打开 `源代码管理` 选项卡。在 `变更` 列表中，双击 `patterns.js` 文件以打开差异（比较）视图。

   <img width="350px" src="https://github.com/user-attachments/assets/4dce9e42-caca-4c6e-a6fe-8d83d58cd06d"/><br/>

   <img width="500px" src="https://github.com/user-attachments/assets/4c410689-2a53-462f-9200-79d21bddbf2c"/>

   > 💡 **Tip**: 你可以在对比视图中直接修改内容，改动会实时反馈！

1. 将文件添加到 **暂存区**。 ⚠️ 注意：不要现在提交！

   可以看到，对比视图不再显示差异了，因为当前文件已经和暂存区一致。

   <img width="500px" src="https://github.com/user-attachments/assets/b1274ece-2b03-42d2-88e8-9f3aaaa8f2c5"/>

1. 在 **暂存变更** 列表中，双击 `patterns.js` 文件以打开差异（比较）视图。

   此时无法再对暂存区的内容进行修改，已锁定，因为它已经准备好提交了。

   <img width="350px" src="https://github.com/user-attachments/assets/da306727-49f1-4f73-9f38-3a0e5d406cef"/><br/>

   <img width="500px" src="https://github.com/user-attachments/assets/de1448eb-d0dd-4ec5-89a2-74fb4aa1cf5f"/>

1. 使用以下提交消息提交更改。

   ```txt
   Make null pointer pattern easier to complete
   ```

1. 提交后，Mona 将自动检查您的作业。请稍等片刻，并关注评论区，她会回复进度信息和下一步操作。

<details>
<summary>遇到问题？ 🤷</summary><br/>

- 如果变更列表超出一屏，可以按 `q` 退出文件查看。

</details>
