---
layout: post
title: "我的C++学习之旅开始啦！"
date: 2026-01-06
categories: [cpp, open-source]
excerpt: "记录我作为游戏服务器开发者开始C++学习计划的过程"
render_with_liquid: false
---



## 为什么要开始这个计划？

作为一名游戏服务器开发者，我主要使用C++，最近需要临时转到Go。为了不荒废C++技能，我决定：

1. 建立个人博客，记录学习过程
2. 开发一个开源项目，实践C++
3. 每天进步一点点



## 2026-01-06 进展

今天成功搭建了GitHub Pages博客！

### **账号与环境准备**

**具体操作步骤：**

1. **注册GitHub账号**

   - 打开 [https://github.com](https://github.com/)
   - 点击右上角"Sign up"
   - 按提示注册，用户名建议：姓名拼音或技术相关名
   - 验证邮箱

2. **安装Git**

   ```reStructuredText
   # Windows：下载 https://git-scm.com/download/win
   # Mac：打开终端，输入 git（会自动提示安装）
   # Linux：sudo apt install git 或 sudo yum install git
   ```

3. **配置Git**

   ```bash
   # 打开终端或Git Bash
   git config --global user.name "你的名字"
   git config --global user.email "你的邮箱"
   git config --global core.editor "code --wait"  # 如果用VSCode
   ```

   

**完成标志**：能在终端运行`git --version`看到版本信息

### **创建博客（最简单方法）**

**使用最简方法：GitHub Pages + Markdown**

1. **创建博客仓库**

   - 登录GitHub
   - 点击右上角"+" → "New repository"
   - 仓库名格式：`用户名.github.io`（必须！）
   - 选择"Public"，勾选"Add a README file"
   - 点击"Create repository"

2. **克隆到本地**

   ```bash
   cd ~/Desktop  # 或你喜欢的目录
   git clone https://github.com/你的用户名/你的用户名.github.io.git
   cd 你的用户名.github.io
   ```

3. **创建第一篇文章**

   ```bash
   # 创建_posts文件夹
   mkdir _posts
   
   # 创建第一篇博客
   echo "# 我的C++学习之旅" > _posts/2026-01-06-beginning.md
   ```

5. **推送到GitHub**

   ```bash
   git add .
   git commit -m "添加第一篇博客"
   git push origin main
   ```

6. **创建个人访问令牌（首次执行git push时密码验证失败时需要）**

   报错信息：

   ```bash
   remote: Invalid username or token. Password authentication is not supported for Git operations.
   fatal: Authentication failed for 'https://github.com/ylj-dev/ylj_dev.github.io.git/'
   ```

   解决步骤：

   - 在 GitHub 网站的 “Settings” 中，找到并进入 **“Developer settings”**。
   - 点击 **“Personal access tokens”** -> **“Tokens (classic)”**。
   - 点击 **“Generate new token”** -> **“Generate new token (classic)”**。
   - 填写一个便于记忆的 **Note**（例如 “My MacBook”），选择 **Expiration**（过期时间，如 90 天），然后勾选 **`repo`** 权限（这是推送代码所需的最小权限）。
   - 滚动到页面底部，点击 **“Generate token”**。
   - **最关键的一步**：生成后，**立即复制**屏幕上显示的令牌字符串。它像这样：`ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`。关闭页面后将无法再次查看。
   - 回到你的终端，再次运行 `git push origin main`。
   - 当提示输入用户名时，**粘贴你第一步找到的真实用户名**。
   - 当提示输入密码时，**不要输入你的GitHub账户密码，而是粘贴你第二步生成的令牌**。
   - 成功后，系统通常会询问你是否将凭证保存到钥匙串，选择“是”以便未来无需重复输入。

7. **连接协议切换到 SSH 协议（推荐）**

   优点：

   ​	SSH将完全绕过HTTP/HTTPS的所有代理、过滤和连接问题，解决可能出现的`git push`卡住的问题。

   操作步骤：

   - **生成SSH密钥**（如果从未生成过）：

     ```bash
     ssh-keygen -t ed25519 -C "你的邮箱地址"
     ```

     按提示连续回车，使用默认设置（建议不设密码）。

   - **将公钥添加到GitHub**：

     - 复制公钥内容：`cat ~/.ssh/id_ed25519.pub`
     - 登录 [GitHub](https://github.com/)，点击右上角头像 → **Settings** → **SSH and GPG keys** → **New SSH key**。
     - 粘贴公钥，取个标题（如`My Mac`），点击 **Add SSH key**。

   - **修改你本地仓库的远程地址为SSH格式**（这是最关键的一步）：

     ```bash
     git remote set-url origin git@github.com:ylj-dev/ylj_dev.github.io.git
     ```

   - **测试并推送**：

     ```bash
     # 测试SSH连接
     ssh -T git@github.com
     # 第一次通过SSH连接需要验证指纹, 输入yes即可, 示例如下。
     # 看到 “Hi ylj-dev! You've successfully authenticated...” 即表示成功。
     # 这是SSH协议的标准安全机制。因为是第一次通过SSH连接 github.com, 电脑本地没有记录过它的身份指纹, 系统把这个指纹（SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU）显示给你，让你核对。
     # 输入yes之后：你的电脑会将这个指纹保存到 ~/.ssh/known_hosts 文件中。下次再连接时，就不会有此提示了。
     The authenticity of host 'github.com (20.205.243.166)' can't be established.
     ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU.
     This key is not known by any other names.
     Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
     Warning: Permanently added 'github.com' (ED25519) to the list of known hosts.
     Hi ylj-dev! You've successfully authenticated, but GitHub does not provide shell access.
     # 执行推送
     git push origin main
     ```

   现在就可以使用SSH协议进行所有Git操作了，可能出现的`git push`卡住的问题将不复存在。

8. **永久忽略`.DS_Store文件`（macOS系统文件，`git status`时看到了再进行处理即可）**

   - 详细解释

   |    项目    | 说明                                                   |
   | :--------: | :----------------------------------------------------- |
   | **文件名** | `.DS_Store`                                            |
   |  **作用**  | 保存其**所在文件夹的自定义视图设置**（非文件夹内容）。 |
   | **生成者** | macOS 系统的 **Finder**（访达）应用。                  |
   |  **位置**  | 出现在你打开过的**几乎所有文件夹**中。                 |

   - `git status`显示`.DS_Store文件`的原因

     可能通过 **Finder** 浏览过包含你博客项目的父文件夹，系统因此自动生成了这个文件。因为 `.DS_Store` 文件**通常与项目代码无关**，并且包含个人系统偏好，所以**强烈建议不要将其提交到 Git 仓库**。

   - 处理方式 --> **永久全局忽略**

     在你的电脑上全局配置 Git，忽略所有 `.DS_Store` 文件，一劳永逸：

     ```bash
     # 创建全局忽略配置文件
     echo ".DS_Store" >> ~/.gitignore_global
     # 让 Git 使用这个全局配置文件
     git config --global core.excludesfile ~/.gitignore_global
     ```

   此时，再次执行`git status`时就不会再看到`.DS_Store文件`了。

   

**完成标志**：打开 `https://你的用户名.github.io` 能看到页面

### **美化博客**

**做最简化的美化，只做必要的几步，使用GitHub默认主题：jekyll-theme-cayman**

1. **创建 `_config.yml`**

   ```bash
   cd ~/my_github/ylj-dev.github.io/
   # 创建 _config.yml
   cat > _config.yml << 'EOF'
   title: "ylj的C++学习笔记"
   description: "记录C++学习、LeetCode刷题、计算机科学概论阅读笔记、开源项目开发"
   url: "https://ylj-dev.github.io"
   baseurl: ""
   theme: jekyll-theme-cayman  # 使用GitHub默认主题
   
   # 作者信息
   author: "ylj"
   github_username: "ylj-dev"
   
   # 构建设置
   markdown: kramdown
   highlighter: rouge
   permalink: /:year/:month/:day/:title/
   
   # 插件
   plugins:
     - jekyll-feed
     - jekyll-seo-tag
   
   # 排除文件
   exclude:
     - README.md
     - Gemfile
     - Gemfile.lock
   
   # 自定义设置
   show_excerpts: true
   EOF
   ```

2. **创建分类目录页面**

   ```bash
   cat > categories.md << "EOF"
   ---
   layout: page
   title: "所有分类"
   permalink: /categories/
   ---
   
   # 📚 所有分类
   
   {% for category in site.categories %}
   ## {{ category[0] }}
   {% for post in category[1] %}
   - [{{ post.title }}]({{ post.url }}) - {{ post.date | date: "%Y-%m-%d" }}
   {% endfor %}
   {% endfor %}
   
   ---
   
   [返回首页](/)
   EOF
   ```

3. **创建分类文件夹和页面**

   ```bash
   mkdir -p categories
   
   # C++分类页面
   cat > categories/cpp.md << "EOF"
   ---
   layout: page
   title: "C++学习笔记"
   permalink: /categories/cpp/
   ---
   
   # C++学习笔记
   
   ## 学习路线图
   1. **基础阶段** - 语法、数据类型、控制流
   2. **核心阶段** - 面向对象、模板、STL
   3. **进阶阶段** - 现代C++、多线程、网络编程
   
   ## 文章列表
   {% for post in site.categories.cpp %}
   - [{{ post.title }}]({{ post.url }}) - {{ post.date | date: "%Y-%m-%d" }}
   {% endfor %}
   
   ---
   
   [查看所有分类](/categories/) | [返回首页](/)
   EOF
   
   # 算法分类页面
   cat > categories/algorithm.md << "EOF"
   ---
   layout: page
   title: "算法刷题"
   permalink: /categories/algorithm/
   ---
   
   # 算法刷题
   
   ## 刷题计划
   跟随《代码随想录》顺序，每天1-2题。
   
   ## 文章列表
   {% for post in site.categories.algorithm %}
   - [{{ post.title }}]({{ post.url }}) - {{ post.date | date: "%Y-%m-%d" }}
   {% endfor %}
   
   ---
   
   [查看所有分类](/categories/) | [返回首页](/)
   EOF
   
   # 计算机科学分类页面
   cat > categories/cs.md << "EOF"
   ---
   layout: page
   title: "计算机科学"
   permalink: /categories/cs/
   ---
   
   # 计算机科学
   
   ## 学习内容
   - 计算机组成原理
   - 操作系统
   - 计算机网络
   - 数据结构与算法
   
   ## 文章列表
   {% for post in site.categories.cs %}
   - [{{ post.title }}]({{ post.url }}) - {{ post.date | date: "%Y-%m-%d" }}
   {% endfor %}
   
   ---
   
   [查看所有分类](/categories/) | [返回首页](/)
   EOF
   
   # 开源项目分类页面
   cat > categories/open-source.md << 'EOF'
   ---
   layout: page
   title: "开源项目"
   permalink: /categories/open-source/
   ---
   
   # 开源项目
   
   ## 项目计划
   1. **MiniGameServer** - 轻量级C++游戏服务器框架
   2. **其他实践项目** - 将所学应用于实际开发
   
   ## 学习目标
   - 实践现代C++编程
   - 学习项目架构设计
   - 掌握Git协作流程
   - 参与开源社区
   
   ## 相关文章
   {% for post in site.categories.open-source %}
   - [{{ post.title }}]({{ post.url }}) - {{ post.date | date: "%Y-%m-%d" }}
   {% endfor %}
   
   ---
   
   [查看所有分类](/categories/) | [返回首页](/)
   EOF
   ```

4. **创建首页（添加分类链接）**

   ```bash
   # 创建 index.md
   cat > index.md << 'EOF'
   ---
   layout: default
   title: "首页"
   ---
   
   # 欢迎来到我的学习博客！👨‍💻
   
   我是 **ylj**，一名专注于 **C++ 游戏服务器后端开发** 的工程师。这里是我系统学习、沉淀知识的地方。
   
   ## 📝 最新文章
   
   {% for post in site.posts limit:5 %}
   - **【{{ post.categories | first }}】** [{{ post.title }}]({{ post.url }}) - <small>{{ post.date | date: "%Y-%m-%d" }}</small>
   {% if post.excerpt %}  *{{ post.excerpt | strip_html | truncate: 100 }}* {% endif %}
   {% endfor %}
   
   [查看所有文章归档...](/archive.html)
   
   ---
   
   ## 🎯 我的核心学习路径
   
   | 目标 | 关键行动 | 产出 |
   | :--- | :--- | :--- |
   | **C++ 精通** | 基础→面向对象→STL→现代C++→项目实践 | 系列笔记、开源项目 |
   | **算法提升** | 跟随《代码随想录》，每日刷题，参加周赛 | LeetCode 题解、竞赛总结 |
   | **CS 基础巩固** | 精读《计算机科学概论》等经典 | 核心概念笔记、体系理解 |
   | **工程能力** | 设计并实现一个 C++ 游戏服务器框架 | 开源项目、架构文档 |
   
   ---
   
   ## 📚 按主题探索
   
   <div class="category-grid">
   <a href="/categories/cpp/" class="category-card">
   <h3>C++ 学习笔记</h3>
   <p>从语法到工程实践的系统复习</p>
   </a>
   <a href="/categories/algorithm/" class="category-card">
   <h3>算法刷题</h3>
   <p>LeetCode 题解与竞赛心得</p>
   </a>
   <a href="/categories/cs/" class="category-card">
   <h3>计算机科学</h3>
   <p>操作系统、网络等理论基础</p>
   </a>
   <a href="/categories/open-source/" class="project-card"> <!-- 特殊样式突出项目 -->
   <h3>开源项目</h3>
   <p>MiniGameServer 及更多实践</p>
   </a>
   </div>
   
   ---
   
   ## 🔗 关于 & 联系
   
   - **关于我**：[了解更多我的故事](/about.html)
   - **代码仓库**：[GitHub @ylj-dev](https://github.com/ylj-dev)
   - **算法练习**：[LeetCode 主页](https://leetcode.cn/u/ylj-v/)
   
   > **“Talk is cheap. Show me the code.”** — Linus Torvalds
   EOF
   ```

5. **创建归档页面**

   ```bash
   cat > archive.md << 'EOF'
   ---
   layout: page
   title: "文章归档"
   permalink: /archive.html
   ---
   
   # 所有文章
   
   按时间倒序排列：
   
   {% for post in site.posts %}
   ## {{ post.date | date: "%Y年%m月" }}
   - [{{ post.title }}]({{ post.url }}) - {{ post.date | date: "%m-%d" }}
   {% endfor %}
   EOF
   ```

6. **创建关于页面**

   ```bash
   cat > about.md << 'EOF'
   ---
   layout: page
   title: "关于我"
   permalink: /about.html
   ---
   
   ## 👋 我是谁？
   
   我是ylj，一名游戏服务器开发工程师，主要使用C++进行后端开发。
   
   ## 🎯 当前目标
   
   2026年学习计划：
   1. **C++基础巩固**：从基础到高级，系统复习
   2. **算法能力提升**：LeetCode每日一题，参加周赛
   3. **计算机科学基础**：阅读经典书籍，打好理论基础
   4. **项目实践**：开发开源项目，锻炼工程能力
   
   ## 📊 技术栈
   
   - **主要语言**: C++, Go
   - **开发方向**: 游戏服务器后端
   - **熟悉框架**: 网络编程、多线程、数据库
   - **工具链**: Git, CMake, VSCode, Docker
   
   ## 🎓 学习方式
   
   1. **系统学习**：按知识体系逐步推进
   2. **刻意练习**：每个知识点都动手编码
   3. **输出驱动**：通过写博客巩固理解
   4. **社群互动**：在社区中学习和分享
   
   ## 💌 联系我
   
   - GitHub: [ylj-dev](https://github.com/ylj-dev)
   - 博客: [ylj-dev.github.io](https://ylj-dev.github.io)
   
   ---
   
   *路虽远，行则将至；事虽难，做则必成*
   EOF
   ```

7. **更新现有文章的分类标签**

   修改 `_posts/2026-01-06-beginning.md` 的Front Matter，因为Jekyll对Front Matter（文章头部信息）有严格要求

   ```bash
   ---
   layout: post
   title: "我的C++学习之旅开始啦！"
   date: 2026-01-06
   categories: [cpp, open-source]
   excerpt: "记录我作为游戏服务器开发者开始C++学习计划的过程"
   ---
   ```

8. **创建.gitignore文件（避免上传不必要文件）**

   ```bash
   cat > .gitignore << 'EOF'
   .DS_Store
   .sass-cache
   .jekyll-cache
   .jekyll-metadata
   .bundle
   vendor
   _site
   .env
   EOF
   ```

9. **提交所有更改**

   ```bash
   # 查看当前状态
   git status
   
   # 添加所有文件
   git add .
   
   # 提交
   git commit -m "完成博客美化，添加基本页面和分类系统"
   
   # 推送到GitHub
   git push origin main
   ```

10. **验证效果**

   等待1-2分钟，访问：

   ```reStructuredText
   https://ylj-dev.github.io
   ```

   你应该看到：

   - 一个美观的主题页面

   - 导航菜单

   - 你的第一篇文章

   - 归档页面

   - 关于页面



**博客美化前后的对比**

|     特性     |       美化前       |          美化后          |
| :----------: | :----------------: | :----------------------: |
|   **外观**   | 纯Markdown，无样式 |      专业主题，美观      |
|   **导航**   |     无导航菜单     | 有首页、归档、关于等导航 |
|   **分类**   |       无分类       |       支持文章分类       |
|   **搜索**   |         无         |      可能有基础搜索      |
| **代码高亮** |        基础        |         语法高亮         |
|  **响应式**  |         无         |      适配手机和电脑      |
| **作者信息** |         无         |      显示作者和版权      |

**当前文件分析**

```reStructuredText
ylj-dev.github.io/
├── _config.yml        # 必须 - Jekyll配置文件
├── _posts/						 # 所有博客文章
│   └── 2026-01-06-beginning.md  # 博客文章
├── about.md           # 可选 - 关于页面 - 建立个人品牌
├── archive.md         # 可选 - 归档页面 - 方便查看文章历史
├── categories/
│   ├── algorithm.md   # 必须 - 算法分类页面
│   ├── cpp.md         # 必须 - C++分类页面
│   ├── cs.md          # 可选 - 计算机科学分类页面
│   └── open-source.md # 必须 - 开源项目分类
├── categories.md      # 可选 - 分类汇总页面
├── index.md           # 必须 - 首页
└── README.md          # 可选 - GitHub仓库说明文件 - 不影响博客，但建议保留作为仓库说明
```

**后续写文章的建议**

未来写文章时，根据内容选择合适的分类：

```reStructuredText
# C++复习文章
categories: [cpp]

# 算法题解  
categories: [algorithm]

# 开源项目进展
categories: [open-source]

# 计算机理论学习
categories: [cs]
```



**这样博客就能很好地组织和展示自己的学习进展了！**

### **启用预制的工作流**

- **问题：**

  ​	https://github.com/ylj-dev/ylj-dev.github.io/actions

  ​	本地提交已经推送到GitHub，但自动构建流程就是没有启动（workflow runs列表没有更新），博客页面状态没有更新。

- **原因：**

  ​	https://github.com/ylj-dev/ylj-dev.github.io/settings/pages

  ​	GitHub Pages 当前可能没有启用一个明确的、自动化的构建工作流。页面上“**Use a suggested workflow...**”（使用推荐的工作流...）这句话是一个重要	提示。它意味着你的仓库目前可能处于一种“待配置”状态，依赖GitHub的后台服务进行构建，而这个服务的触发有时不灵敏。

- **解决方案：启用预制的工作流**

  ​	https://github.com/ylj-dev/ylj-dev.github.io/settings/pages

  1. **找到预制工作流：**
     在你截图页面中部的 “**Build and deployment**” 部分，找到名为 **“GitHub Pages Jekyll”** 的卡片。
  2. **点击配置按钮：**
     点击该卡片右下角的 **“Configure”**（配置）按钮。
  3. **提交工作流文件：**
     点击后，GitHub 会自动跳转到创建 `.github/workflows/jekyll.yml` 文件的页面。你无需修改代码，**直接滑动到页面底部**，点击绿色的 **“Commit changes...”** 按钮，然后选择 **“Commit directly to the main branch”**，最后确认提交。

  **这个操作的作用是**：它会为你的仓库创建一个标准的、由 GitHub Actions 驱动的 Jekyll 构建流程。之后，每次向 `main` 分支的推送都会可靠地触发一次完整的构建，并在 Actions 页面留下清晰记录。



**完成标志**：前往 Actions 页面(`https://github.com/ylj-dev/ylj-dev.github.io/actions`)。会看到一个新的工作流（可能是 `jekyll` 或 `pages-build-deployment`）立刻开始运行，构建成功后访问博客网站查看所有更新是否已生效。

### 禁用整篇文章的Liquid渲染

- **问题：**

  ​	markdown文档在浏览器部分渲染失败。

- **原因：**

  ​	文章内容中包含了大量Jekyll模板引擎（Liquid）的保留字符和语法，导致解析器在处理中途“宕机”了。比如：`{`、`}`、`%`、`|`、`:` 等符号，这些正是Liquid 模板语言的标记，Jekyll 会尝试将它们当作指令来执行，结果当然是失败并中断了渲染。

- **解决方案：**

  - 方法一：使用 `{% raw %}` 标签

    ​	将这些“高危”代码块用 **`{% raw %}` 和 `{% endraw %}`** 标签包裹起来，告诉Jekyll：“这里面的内容都是纯文本，不要解析”。

  - 方法二：禁用整篇文章的Liquid渲染（推荐）

    ​	在文章的 **Front Matter**（就是开头 `---` 之间的部分）中，加入一行配置即可。		

    ```markdown
    ---
    layout: post
    title: "我的C++学习之旅开始啦！"
    date: 2026-01-06
    categories: [cpp, open-source]
    excerpt: "记录我作为游戏服务器开发者开始C++学习计划的过程"
    render_with_liquid: false  # <--- 加入这一行关键配置
    ---
    ```

    ​	**这行配置的作用是**：告诉Jekyll，“**在渲染这篇文章时，不要处理里面的任何 `{ }` `%` 等Liquid标签，把它们全部当成纯文本**”。



---
*每天进步一点点，就是最大的成功*