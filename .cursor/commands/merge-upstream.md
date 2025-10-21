---
description: 从 upstream/main 合并最新代码到本地 main 分支，保持代码同步
---

用户输入（可选）：

$ARGUMENTS

执行以下步骤来合并 upstream/main 的最新代码到本地 main 分支：

## 1. 检查当前状态
- 确认当前分支状态
- 检查是否有未提交的更改
- 验证 upstream 远程仓库配置

## 2. 获取最新代码
- 从 upstream 获取最新的 main 分支代码
- 更新本地 main 分支到最新状态

## 3. 执行合并操作
- 切换到 main 分支
- 合并 upstream/main 的更改
- 处理可能的冲突

## 4. 验证合并结果
- 检查合并后的代码状态
- 确认没有破坏性更改
- 提供合并摘要

## 执行流程

1. **状态检查**：
   ```bash
   git status
   git branch -v
   git remote -v
   ```

2. **获取最新代码**：
   ```bash
   git fetch upstream
   git fetch origin
   ```

3. **合并操作**：
   ```bash
   git checkout main
   git merge upstream/main
   ```

4. **处理冲突**（如果出现）：
   ```bash
   # 检查冲突文件
   git status
   
   # 解决 pyproject.toml 冲突：保留本地项目名称，版本号 +1
   git add pyproject.toml
   git commit -m "Merge upstream/main: 保留本地项目身份，版本升级"
   ```

5. **推送更新**（如果需要）：
   ```bash
   git push origin main
   ```

## 冲突处理策略

**pyproject.toml 冲突**：
- 保留本地项目名称（如 `arc-cli`）
- 版本号 +1（如 `0.0.1` → `0.0.2`）
- 保留本地项目描述
- 采用 upstream 的依赖配置

**其他文件**：优先采用 upstream 的更新

## 安全措施

- 在合并前创建备份分支
- 检查合并的提交历史

注意：此命令假设 upstream 远程仓库已正确配置。如果遇到问题，请检查 `.git/config` 文件中的远程仓库设置。
