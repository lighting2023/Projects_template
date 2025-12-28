# 项目模板 (Projects Template)

这是一个多语言开发项目模板。

## Git Subtree 使用示例

### 1. 将模板添加到现有的 Git 仓库作为 subtree

假设你有一个主项目，想把这个模板添加进去：

```bash
# 在主项目中添加这个模板作为 subtree
git subtree add --prefix=templates/projects_template \
  https://github.com/yourusername/Projects_template.git main \
  --squash
```

### 2. 从远程仓库拉取更新

```bash
# 从远程拉取更新到 subtree
git subtree pull --prefix=templates/projects_template \
  https://github.com/yourusername/Projects_template.git main \
  --squash
```

### 3. 推送更改回远程仓库

```bash
# 如果对模板做了修改，推回到远程
git subtree push --prefix=templates/projects_template \
  https://github.com/yourusername/Projects_template.git main
```

### 4. 完整的示例工作流程

#### 步骤 1: 初始化模板仓库（如果是新仓库）

```bash
cd Projects_template
git init
git add .
git commit -m "Initial commit: 多语言项目模板"
git remote add origin https://github.com/yourusername/Projects_template.git
git push -u origin main
```

#### 步骤 2: 在其他项目中使用这个模板

```bash
# 进入你的主项目
cd /path/to/your/main-project

# 添加模板作为 subtree
git subtree add --prefix=templates/projects_template \
  https://github.com/yourusername/Projects_template.git main \
  --squash

# 之后如果需要更新模板
git subtree pull --prefix=templates/projects_template \
  https://github.com/yourusername/Projects_template.git main \
  --squash
```

#### 步骤 3: 如果你修改了模板并想推送回去

```bash
# 在主项目中修改 templates/projects_template/ 下的文件
# ... 进行修改 ...

# 提交更改
git add templates/projects_template/
git commit -m "Update project template"

# 推送到模板的远程仓库
git subtree push --prefix=templates/projects_template \
  https://github.com/yourusername/Projects_template.git main
```

### Git Subtree 命令说明

- `--prefix=templates/projects_template`: 指定在父仓库中的路径
- `--squash`: 将多个提交合并为一个，保持主项目历史清洁
- `main`: 分支名称（可能是 `master` 或 `main`）

### 优势

- ✅ 模板代码作为子目录存在于主项目中
- ✅ 可以独立更新模板
- ✅ 不依赖外部工具（Git 原生支持）
- ✅ 可以双向同步更改

### 注意事项

- 使用 `--squash` 时，Git 历史会比较简洁，但合并时可能需要手动解决冲突
- 确保 `--prefix` 路径不存在，否则 subtree add 会失败
- 推送更改时，确保有推送到模板仓库的权限

