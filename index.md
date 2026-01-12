---
layout: default
title: "首页"
---

# 欢迎来到我的学习博客！

我是ylj，一名游戏服务器开发工程师，正在系统学习：

## 📚 学习计划

1. **C++基础知识复习**（目标：炉火纯青）
   - 基础语法 -> 面向对象 -> 模板 -> 现代C++
   - 每章写总结笔记

2. **LeetCode刷题**（目标：熟练算法）
   - 跟随代码随想录
   - 参加周赛锻炼
   - 每题写题解

3. **计算机科学概论学习**
   - 系统阅读经典书籍
   - 记录核心概念

4. **开源项目实践**
   - 将所学应用于实际项目

## 📝 最新文章

{% for post in site.posts limit:5 %}
- [{{ post.title }}]({{ post.url }}) ({{ post.date | date: "%Y-%m-%d" }})
{% endfor %}

[查看所有文章](archive.html)

## 🔗 快速链接

- [GitHub主页](https://github.com/ylj-dev)
- [LeetCode主页](https://leetcode.cn/u/ylj-v/)  # 如果有的话
- [关于我](about.md)

---

**名言警句：**  
"学习如逆水行舟，不进则退"
