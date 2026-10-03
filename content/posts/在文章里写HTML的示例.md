---
title: "在文章里写 HTML 的示例"
date: 2026-10-02
draft: false
tags: ["教程"]
categories: ["折腾"]
summary: "演示在 Markdown 文章里直接插入 HTML 标签，Hugo 会原样输出。"
---

普通的正文用 Markdown 写就够了，比如**加粗**、*斜体*、[链接](https://example.com)。

## 下面是 HTML 写的内容

<div style="padding:16px 20px;border-left:4px solid #378add;background:#eef4fb;border-radius:6px;margin:20px 0;">
  <strong>这是一个提示框</strong><br>
  这段是用 HTML 的 div 写出来的，Markdown 做不到这种样式。
</div>

<div style="display:flex;gap:12px;margin:20px 0;">
  <div style="flex:1;padding:14px;border:1px solid #dddddd;border-radius:8px;">
    <strong>左栏</strong><br>用 flex 做左右分栏。
  </div>
  <div style="flex:1;padding:14px;border:1px solid #dddddd;border-radius:8px;">
    <strong>右栏</strong><br>手机上看会自动变成上下堆叠。
  </div>
</div>

<p style="color:#d85a30;font-weight:600;">这一行是用 HTML 的 p 标签写的，颜色和字重都由 style 直接指定。</p>

## 三个必须注意的点

1. 文章文件名结尾必须是 `.md`
2. HTML 的样式要直接写在标签上，用 `style="..."` 这种写法
3. 如果 HTML 没生效、被当成一串文字原样显示出来了，说明 `hugo.toml` 里少了
   `[markup.goldmark.renderer]` 下面的 `unsafe = true` 这一行
