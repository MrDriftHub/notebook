这份笔记涵盖了从安装 Git 到在 GitHub 上创建仓库的完整流程，以及如何使用 PyCharm 连接 GitHub 仓库。

---

# 使用 Git 和 PyCharm 管理代码并连接 GitHub

当然可以！以下是根据你的要求**重新整理的完整、结构清晰、页面明了的 Markdown 笔记**，按照 **“从安装 → 配置 → 使用”** 的逻辑顺序组织，风格简洁专业，适合长期保存和查阅。

---

## 1️⃣ 安装 Git

### 1.1 下载并安装 Git
- 访问官网：[https://git-scm.com](https://git-scm.com)
- 下载 Windows 版 Git 并安装（一路默认选项即可）

### 1.2 验证安装
打开命令提示符（CMD）或 PowerShell，运行：

```bash
git --version
```

✅ 正常输出示例如下：
```
git version 2.40.1.windows.1
```

---

## 2️⃣ 配置 Git 全局信息

首次使用 Git 需配置用户名和邮箱（与 GitHub 账号一致）：

```bash
git config --global user.name "XXX"
git config --global user.email "mr.drift.dev@outlook.com"
```

> 🔔 说明：
> - `user.name`：GitHub 显示的提交者名称
> - `user.email`：GitHub 绑定的邮箱，用于识别提交

---

## 3️⃣ 配置 SSH 密钥（免密码推送）

### 3.1 生成 SSH 密钥
运行命令生成密钥对：

```bash
ssh-keygen -t rsa -b 4096 -C "mr.drift.dev@outlook.com"
```

- 按回车使用默认保存路径：`C:\Users\WG_Z_\.ssh\id_rsa`
- 可设置密码（可选），或直接回车留空

### 3.2 查看并复制公钥
```bash
type C:\Users\WG_Z_\.ssh\id_rsa.pub
```

全选并复制输出内容（以 `ssh-rsa` 开头，以邮箱结尾）。

### 3.3 添加公钥到 GitHub
1. 登录 GitHub：[https://github.com](https://github.com)
2. 点击头像 → **Settings**
3. 左侧 → **SSH and GPG keys** → **New SSH key**
4. 填写：
   - **Title**: `My Windows PC`
   - **Key**: 粘贴复制的公钥内容
5. 点击 **Add SSH key**

### 3.4 测试连接
```bash
ssh -T git@github.com
```

✅ 成功提示：
```
Hi MrDrift! You've successfully authenticated...
```

---

## 4️⃣ 创建 GitHub 仓库

### 4.1 登录 GitHub
使用邮箱账号 `mr.drift.dev@outlook.com` 登录。

### 4.2 新建仓库
1. 点击右上角 `+` → **New repository**
2. 填写信息：
   - **Repository name**: `notebook`
   - **Description**: `My project templates and technical notes`
   - **Private**（可选）
   - ❌ 不勾选 “Initialize this repository with a README”
3. 点击 **Create repository**

---

## 5️⃣ 初始化本地仓库并推送

### 5.1 创建本地项目目录
```bash
cd D:\git\github
mkdir notebook
cd notebook
```

### 5.2 初始化 Git 仓库
```bash
git init
```

### 5.3 创建初始文件
```bash
echo "# 项目模板与笔记" > README.md
```

### 5.4 添加并提交文件
```bash
git add .
git commit -m "初始提交：添加 README"
```

### 5.5 关联远程仓库
```bash
git remote add origin git@github.com:XXX/notebook.git
```

> 🔔 替换 XXX 为你的 GitHub 用户名。

### 5.6 推送代码（首次）
```bash
git branch -M main
git push -u origin main
```

✅ 成功后，GitHub 仓库中将出现 `README.md` 文件。

---

## 6️⃣ 日常使用命令

每次添加或修改文件后，执行以下命令同步到 GitHub：
前缀可加：`添加：`、`更新：`、`修复：`、`删除：`

```bash
# 1. 添加所有更改的文件
git add .

# 2. 提交更改（请写明描述）
git commit -m "添加：Vue3 项目模板"

# 3. 推送到远程仓库
git push
```

### 🔄 示例
```bash
git add .
git commit -m "更新：优化笔记目录结构"
git push
```

```bash
git add .
git commit -m "添加：Python 脚本模板"
git push
```

---

## 7️⃣ 目录结构

建议在 `notebook/` 下组织内容：

```bash
notebook/
├── templates/              # 项目模板
│   ├── vue3-ts/
│   ├── react-vite/
│   └── python-script/
├── notes/                  # 学习笔记
│   ├── git-guide.md
│   ├── vscode-tips.md
│   └── linux-commands.md
└── README.md
```

---

## 8️⃣ 常用命令速查

| 命令 | 说明 |
|------|------|
| `git status` | 查看当前修改状态 |
| `git log --oneline` | 查看提交历史 |
| `git pull` | 拉取远程最新内容 |
| `git remote -v` | 查看远程仓库地址 |
| `git branch` | 查看当前分支 |

---

## ✅ 总结

- ✅ Git 安装与配置
- ✅ SSH 密钥设置
- ✅ GitHub 仓库创建
- ✅ 本地仓库初始化与推送
- ✅ 日常提交流程掌握

---

📅 最后更新：2025年9月3日