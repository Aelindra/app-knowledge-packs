---
name: ditto
description: Ditto（Windows 剪贴板历史管理，开源）结构综述：存储/检索/组织/网络同步。自动化读写剪贴板或配置 Ditto 前加载。
---

# Ditto 综述

**定位**：Windows 剪贴板扩展（开源，github.com/sabrogden/Ditto，~7k stars）。
把每次复制存入本地 SQLite 数据库（Ditto.db），提供无限历史、检索、组织与多机同步。

## 核心流程

1. **记录**：后台静默捕获所有复制（文本/图片/文件）
2. **检索**：快捷键呼出弹出列表 → 全文搜索 → 回车粘贴；支持批量粘贴多条
3. **组织**：置顶（sticky）、分组（groups）、标签（tags）、命名描述
4. **同步**：多台电脑间剪贴板网络同步（可加密）
5. **扩展**：ChaiScript 脚本、XML 主题

## 词表

Ditto.db（SQLite 存储）｜sticky（置顶）｜groups（分组）｜tags（标签）｜剪贴板同步

细节以官方站点与 GitHub 为准（见 sources.md）。
