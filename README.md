# Hermel的附件表

这是一个新的导航网站，记录每期视频中需要用到的软件和网页资源。

> 你可以在浏览器中使用`Ctrl + F`通过视频编号快速查询。

[回到主页](./)

> ⚠️ 本网站资源仅供分享，如遇网页问题请及时联系我。

---

## 001. Docsify附件表搭建+Hugo博客搭建+GitHub托管，还0成本？！
## 准备工作：
1. [Node.js 官网](https://nodejs.org/zh-cn)
2. [docsify 官网](https://docsify.js.org/#/)
3. [Typora 官方中文站](https://typoraio.cn/)
4. [Git 官网](https://git-scm.com/)
5. [Hugo 官网](https://gohugo.io/)
6. [Hugo 主题](https://themes.gohugo.io/)
7. [GitHub 官网](https://github.com/)
8. [Watt Toolkit 官网](https://steampp.net/)

---

# docisfy建站流程（代码部分）

> [!IMPORTANT]  
> 一切以视频步骤为准，下方只展示所需代码！

---

## docisfy的安装

### 1. 检查node安装情况
```bash
node -v
```

### 2. 检查npm安装情况
```bash
npm -v
```

### 3. 安装docisfy工具
```bash
npm i docsify-cli -g
```

### 4. 初始化docsify文档
```bash
docsify init ./docs
```

### 5. 本地预览您的网站
```bash
docsify serve docs
```

---

# hugo建站流程（代码部分）

## hugo的安装

### 1. 检查hugo安装情况
```bash
hugo version
```

### 2. 创建项目结构  
*注：quicklystart可自定义更改名字*
```bash
hugo new site quickstart
```

### 3. 更改项目根目录  
*注：名字前后一致！*
```bash
cd quickstart
```

### 4. 初始化git库
```bash
git init
```

### 5. 主题更换后或前启动hugo服务
```bash
hugo server
```
*注：Ctrl + C 停止本地预览*

---

## 添加文章

### 1. 添加文章  
*注：my-first-post.md名字自定，注意后缀不要漏掉*
```bash
hugo new content/posts/my-first-post.md
```

### 2. 添加文章（stack主题）
```bash
hugo new content content/posts/my-first-post.md
```

### 3. 添加文章后预览
```bash
hugo server -D
```

---

## 手动部署

### 1. 在GitHub上新加新项目和更改`hugo.yaml`文件后远程部署GitHub  
*注：先使用“…or create a new repository on the command line”前三行指令*
```bash
echo "# demohugo" >> README.md
git init
git add README.md
```

### 2. 将文件移至缓存层
```bash
git add .
```

### 3. 配置个人信息  
*注：视频中没有这一步，如果出现与视频中不同的结果或报错，必须输入以下命令*
```bash
git config --global user.email "your-real-email@example.com"
git config --global user.name "Your Name"
```

### 4. 将剩余指令填入  
*注：代码仅做示例，以自己的为准*
```bash
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/example/demohugo.git
git push -u origin main
```


---

## GitHub 推送身份验证问题（macOS 下）

在执行最后一个指令：
```bash
git push -u origin main
```

在 **macOS 系统**下不会自动弹出登录框，所以你需要先输入你的 **GitHub 用户名**。接下来会提示你输入 **GitHub 密码**。  

⚠️ 注意：GitHub 自 **2021 年 8 月**起已经停止了对密码的直接支持，改用更安全的 **个人访问令牌（Personal Access Token，简称 PAT）** 来代替。这也是你在推送（`git push`）到 GitHub 时常见的身份验证问题。  
错误信息通常会提示：  
> Password authentication is not supported for Git operations  

---

## 解决方案：使用 Personal Access Token (PAT)

你需要 **创建一个个人访问令牌（PAT）**，并用它来代替你的 GitHub 密码。

### 1. 在 GitHub 上创建 PAT
1. 登录 GitHub。
2. 点击右上角头像 → **Settings（设置）**。
3. 在左侧菜单底部找到 **Developer settings（开发者设置）**。
4. 点击 **Personal access tokens（个人访问令牌）** → **Tokens (classic)**。
5. 点击 **Generate new token (classic)**。
6. 给令牌起一个名字（例如 `Hugo Blog`），方便辨认。
7. 设置有效期（建议 30 天 / 90 天，或更长，但要注意安全性）。
8. 在 **Select scopes（选择权限）** 部分，勾选 **repo**（进行仓库操作必需）。
9. 点击页面底部的 **Generate token**。
10. **非常重要！** 生成后会显示一串很长的字符，请立即复制。这串字符只会显示一次，如果丢失需重新生成。

---

### 2. 使用 PAT 进行 Git 操作
1. 回到终端，再次执行：
   ```bash
   git push -u origin main
   ```
2. 当提示输入密码时：  
   - **用户名** 输入 GitHub 用户名  
   - **密码** 粘贴刚才生成的 **PAT**  

按下回车即可完成推送。
