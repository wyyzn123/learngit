# Git 2.23+ 常用命令指南

## 文件操作命令对比

### 1. git restore
用于恢复工作区文件，是 `git checkout` 的替代命令。

#### 常用场景：
- 恢复单个文件到最近一次提交的状态：
  ```bash
  git restore <file>
  ```
- 恢复所有文件到最近一次提交的状态：
  ```bash
  git restore .
  ```
- 从特定提交恢复文件：
  ```bash
  git restore --source=<commit> <file>
  ```

### 2. git reset
用于重置暂存区和工作区。

#### 常用场景：
- 重置暂存区（保留工作区修改）：
  ```bash
  git reset <file>
  ```
- 重置暂存区和工作区（丢弃所有修改）：
  ```bash
  git reset --hard
  ```
- 重置到特定提交：
  ```bash
  git reset --hard <commit>
  ```

### 3. git checkout
用于切换分支和恢复文件（在Git 2.23之前）。

#### 常用场景：
- 切换分支：
  ```bash
  git checkout <branch>
  ```
- 创建并切换到新分支：
  ```bash
  git checkout -b <new-branch>
  ```

### 4. git switch
用于切换分支，是 `git checkout` 的替代命令。

#### 常用场景：
- 切换到已存在的分支：
  ```bash
  git switch <branch>
  ```
- 创建并切换到新分支：
  ```bash
  git switch -c <new-branch>
  ```

## 命令对比总结

| 命令 | 主要用途 | 替代命令 |
|------|----------|----------|
| `git restore` | 恢复工作区文件 | 替代 `git checkout -- <file>` |
| `git reset` | 重置暂存区和工作区 | 无替代 |
| `git checkout` | 切换分支（旧版） | 被 `git switch` 替代 |
| `git switch` | 切换分支（新版） | 替代 `git checkout <branch>` |

## 使用建议

1. 对于文件恢复操作，优先使用 `git restore`
2. 对于分支切换操作，优先使用 `git switch`
3. 需要重置操作时，使用 `git reset`
4. 避免使用 `git checkout` 进行文件操作，使用 `git restore` 替代

## 注意事项

- 使用 `--hard` 选项时要特别小心，它会丢失所有未提交的更改
- 在执行重要操作前，建议先使用 `git status` 查看当前状态
- 如果不确定操作结果，可以先创建分支或提交进行备份 