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

- **📖 关于我**：[了解更多我的故事](/about.html)
- **💻 代码仓库**：[GitHub @ylj-dev](https://github.com/ylj-dev)
- **🧠 算法练习**：[LeetCode 主页](https://leetcode.cn/u/ylj-v/)

> **“Talk is cheap. Show me the code.”** — Linus Torvalds