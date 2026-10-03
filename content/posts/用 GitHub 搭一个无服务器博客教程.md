---
title: "用 GitHub 搭一个无服务器博客教程"
date: 2026-10-02
draft: false
tags: ["教程"]
categories: ["折腾"]
---
<!DOCTYPE html>
<html lang="zh-CN" data-page-node-id="3mlFVxTwEvlCJdZ1GwsnWe">
<head data-page-node-id="VTcWiU0ySX56HpcpramASv">
<meta charset="UTF-8" data-page-node-id="AlVh1CtnK0QbuEN8DSIkCS">
<meta name="viewport" content="width=device-width, initial-scale=1.0" data-page-node-id="yq2cDnpARmqpfDuuGA8LOQ">
<title>Hugo + GitHub Pages 博客搭建教程</title>
<style>
  * { box-sizing: border-box; }
  body {
    margin: 0; padding: 40px 20px 80px;
    background: #ffffff;
    color: #1f1f1f;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "PingFang SC", "Microsoft YaHei", sans-serif;
    line-height: 1.75;
    font-size: 15px;
  }
  .wrap { max-width: 820px; margin: 0 auto; }
  h1 { font-size: 26px; font-weight: 600; margin: 0 0 8px; letter-spacing: -0.3px; }
  .sub { color: #6b6b6b; font-size: 14px; margin: 0 0 28px; }
  h2 {
    font-size: 18px; font-weight: 600; margin: 44px 0 14px;
    padding-bottom: 8px; border-bottom: 1px solid #e6e6e2;
  }
  h3 { font-size: 15px; font-weight: 600; margin: 26px 0 8px; }
  p { margin: 10px 0; }
  ol, ul { margin: 10px 0; padding-left: 22px; }
  li { margin: 6px 0; }
  code.inline {
    background: #f2f2ee; border: 1px solid #e3e3de; border-radius: 4px;
    padding: 1px 5px; font-size: 13px;
    font-family: "SFMono-Regular", Consolas, "Liberation Mono", monospace;
  }
  .note {
    background: #eef4fb; border: 1px solid #cfe0f3; border-left: 3px solid #378add;
    border-radius: 6px; padding: 12px 16px; margin: 16px 0; font-size: 14px;
  }
  .warn {
    background: #fdf3e7; border: 1px solid #f2ddbd; border-left: 3px solid #ba7517;
    border-radius: 6px; padding: 12px 16px; margin: 16px 0; font-size: 14px;
  }
  .danger {
    background: #fdeeee; border: 1px solid #f3cfcf; border-left: 3px solid #c0392b;
    border-radius: 6px; padding: 12px 16px; margin: 16px 0; font-size: 14px;
  }
  .step {
    border: 1px solid #e6e6e2; border-radius: 10px;
    padding: 20px 22px; margin: 18px 0; background: #fcfcfa;
  }
  .step-head { display: flex; align-items: center; gap: 10px; margin-bottom: 10px; }
  .badge {
    flex: none; width: 26px; height: 26px; border-radius: 50%;
    background: #1f1f1f; color: #fff; font-size: 13px; font-weight: 600;
    display: flex; align-items: center; justify-content: center;
  }
  .step-title { font-size: 16px; font-weight: 600; }
  .codebox { position: relative; margin: 14px 0; }
  .codebox pre {
    margin: 0; background: #f6f6f3; border: 1px solid #e3e3de; border-radius: 8px;
    padding: 14px 16px; overflow-x: auto; font-size: 13px; line-height: 1.65;
    font-family: "SFMono-Regular", Consolas, "Liberation Mono", monospace;
  }
  .copy {
    position: absolute; top: 8px; right: 8px;
    background: #ffffff; border: 1px solid #d8d8d3; border-radius: 6px;
    color: #4a4a4a; font-size: 12px; padding: 3px 10px; cursor: pointer;
    font-family: inherit;
  }
  .copy:hover { background: #eee; }
  .copy.done { color: #1d9e75; border-color: #9fe1cb; background: #e1f5ee; }
  table { border-collapse: collapse; width: 100%; margin: 16px 0; font-size: 14px; }
  th, td { border: 1px solid #e6e6e2; padding: 9px 12px; text-align: left; vertical-align: top; }
  th { background: #f6f6f3; font-weight: 600; }
  .kbd {
    display: inline-block; background: #f2f2ee; border: 1px solid #d8d8d3;
    border-bottom-width: 2px; border-radius: 4px; padding: 0 6px; font-size: 13px;
  }
  .toc { background: #f6f6f3; border-radius: 8px; padding: 14px 22px; margin-bottom: 30px; font-size: 14px; }
  .toc a { color: #185fa5; text-decoration: none; }
  .toc a:hover { text-decoration: underline; }
  .path {
    display: inline-block; background: #eef4fb; border: 1px solid #cfe0f3;
    border-radius: 4px; padding: 1px 6px; font-size: 13px;
    font-family: "SFMono-Regular", Consolas, monospace;
  }
  footer { margin-top: 50px; padding-top: 18px; border-top: 1px solid #e6e6e2; color: #8a8a8a; font-size: 13px; }
</style>
</head>
<body data-page-node-id="EZG9BItxcsodgC4orF8qPx">
<div class="wrap" data-page-node-id="T5Qp43170yDGZFle5hrJfC">

<h1 data-page-node-id="AsmObKemsekQpCUOajOqWt">用 GitHub 搭一个无服务器博客</h1>
<p class="sub" data-page-node-id="o7pYL3bkgzF66bposVVKjD">Hugo + PaperMod 主题 + GitHub Pages 自动部署 · 全程在网页上操作，不需要装任何软件</p>


<div class="toc" data-page-node-id="DdRSKVb3SAtXfnOjIHZspK">
  <strong data-page-node-id="iKgC69fCg79PEXTJNUe46x">目录</strong><br data-page-node-id="sISRFPk9qnVd4RqC2eezgC">
  <a href="#step1" data-page-node-id="n3dNe67wu4u8QH7V9JQXrm">第 1 步 · 新建仓库</a> &nbsp;·&nbsp;
  <a href="#step2" data-page-node-id="YCuXE69WMP7vBnhPEroBDc">第 2 步 · 上传文件</a> &nbsp;·&nbsp;
  <a href="#step3" data-page-node-id="TYuHL5ZH7pHMs3cSPooHgC">第 3 步 · 打开发布开关</a> &nbsp;·&nbsp;
  <a href="#step4" data-page-node-id="6mec7vnrHNYpuLttOSmHrl">第 4 步 · 等它自动生成</a><br data-page-node-id="1uOpHImHXJ0KgUFONoz4ya">
  <a href="#step5" data-page-node-id="c6mWaGt4wQPtOTqNJYJdiG">第 5 步 · 改成你自己的信息</a> &nbsp;·&nbsp;
  <a href="#write" data-page-node-id="oEBEWoKIWVcJmv3WOdTyUs">以后怎么写新文章</a> &nbsp;·&nbsp;
  <a href="#html" data-page-node-id="aXFychoBOh3rJnunJgqvM3">文章里写 HTML</a> &nbsp;·&nbsp;
  <a href="#style" data-page-node-id="LXjoAtgLAYSJRFJHe3bb15">改页面样式</a> &nbsp;·&nbsp;
  <a href="#info" data-page-node-id="xyzx0GCCa4zRWpFBTq7n9J">改博客信息</a> &nbsp;·&nbsp;
  <a href="#fix" data-page-node-id="KhhvYgcBvISnYd70SE8UEv">出问题了怎么办</a> &nbsp;·&nbsp;
  <a href="#domain" data-page-node-id="BOvjxwAKehGs63lUZLknhK">换成自己的域名</a>
</div>

<h2 data-page-node-id="TebcpTfEOqKFmFPoYDsnFk">开始之前</h2>
<p data-page-node-id="R1uLNdvLI6Xx4FBXtkxx8S">准备一个 GitHub 账号。没有的话先去 <span class="path" data-page-node-id="qZbN0aFdiLj6mlvsA1C7kO">github.com</span> 注册，邮箱验证完就能用。免费账号足够了。</p>
<p data-page-node-id="HdLPU0LHE7Y1GgmHmdEvFp">另外把你手上的文件夹 <span class="path" data-page-node-id="pC9ESVbU30qeaH6uJGDbGG">hugo-blog-tutorial</span> 找出来，第 2 步要用它里面的东西。<strong data-page-node-id="S0jxagmYcdFZUTMHF149G1">注意里面有个 <span class="path" data-page-node-id="kYFCRm4e1ojZ0XkxLQkUjs">.github</span> 文件夹，它是隐藏文件夹，别漏了</strong>（Windows 需要在资源管理器「查看」里勾上「隐藏的项目」才看得到）。</p>

<h2 id="step1" data-page-node-id="yd5JqhqfJdNLObzoRYwWPW">第 1 步 · 新建仓库</h2>
<div class="step" data-page-node-id="0ri4EcFT1iTzjzyZ1fnvW8">
  <div class="step-head" data-page-node-id="xGioNOHe21PwENqnYT8bax"><div class="badge" data-page-node-id="SjYU2oRTcax6w1SBWViWTj">1</div><div class="step-title" data-page-node-id="2zjeEsxLUYVCA7NTCkzuHq">建一个空仓库</div></div>
  <ol data-page-node-id="gswaqHrzcOjflS9NM2FvDK">
    <li data-page-node-id="R2CufGd0W2W7jFaLbtxFIf">登录 GitHub 后，点右上角头像左边的 <strong data-page-node-id="IaqCilDbpE1tIHCFN8TnMx">「+」</strong>，在菜单里选 <strong data-page-node-id="l6nfbkud25HyC1b03gnMHC">New repository</strong>（新建仓库）。</li>
    <li data-page-node-id="TGqEBWvHFHqBTpDGZGvQzI"><strong data-page-node-id="uIHcEujrvXWgCKJBKuRyuy">Repository name</strong> 这一栏，填 <span class="path" data-page-node-id="Tf5mAWuAO0W34xE4NiCenF">你的用户名.github.io</span>。<br data-page-node-id="VkIOe4G49K79DZBv1L3Gno">
        「你的用户名」= 页面右上角头像旁边那串英文，<strong data-page-node-id="A4NJr0ZhIljr4sSP13B75Q">一字不差地抄下来</strong>，大小写也要一致。</li>
    <li data-page-node-id="rFXCOLGFlunFCJfIxSifMo">下面三个选项：可见性选 <strong data-page-node-id="ilV6MP2DG2xKw3xuOJH1PM">Public</strong>（公开）。</li>
    <li data-page-node-id="S1kfEJ6vzTJHRHUUFz7zgP">勾上 <strong data-page-node-id="yjqx6RrL5snBZmGtHP3ti7">Add a README file</strong>（加一个说明文件）。</li>
    <li data-page-node-id="JAble2IcFa6BRzCvTDSUM3">点最下面绿色的 <strong data-page-node-id="pG4aIFvZy7iDtWaJViUmBM">Create repository</strong> 按钮。</li>
  </ol>
  <div class="note" data-page-node-id="4xBNJpSJgSbAmTB5Pkildn">
    为什么要叫 <span class="path" data-page-node-id="VtNxbfwF0B0C0jrZlN7g4l">用户名.github.io</span>？因为这样你的网址会是最短的 <span class="path" data-page-node-id="IOzx3G5NdnnZGT9E1LFAyK">https://用户名.github.io</span>。<br data-page-node-id="8LzsyvshrXQ2Kw1bgd8TVT">
    如果名字填错了也没关系，只是网址后面会多一段仓库名，比如 <span class="path" data-page-node-id="jP1T49RhEKOeVE4dyFt7Fc">https://用户名.github.io/blog/</span>，照样能用。
  </div>
</div>

<h2 id="step2" data-page-node-id="qcIM2D8h9GGSISvGA9GvIE">第 2 步 · 把文件传上去</h2>
<div class="step" data-page-node-id="jdZUD8CZwB9WoHYUpWKHEz">
  <div class="step-head" data-page-node-id="MVq7e5qK9sD5oNkwKGCDhO"><div class="badge" data-page-node-id="lBOZX3o0NvLEAIqdHlPaKk">2</div><div class="step-title" data-page-node-id="5VMs7WVYCoh3kD2B47E2iZ">一次拖拽上传</div></div>
  <ol data-page-node-id="GQCtcE7qqWHFSTo1Kl6gJQ">
    <li data-page-node-id="58eq86XoIPwj0qPieo9QpX">进入刚建好的仓库页面，点中间偏右的 <strong data-page-node-id="pofPb8Gcak0rKQBmWahnHn">Add file</strong> → <strong data-page-node-id="H0h4kr5Y7aFO3F1rVa3ePf">Upload files</strong>。</li>
    <li data-page-node-id="SScbBdou4GIUXoCPo8bEMU">打开 <span class="path" data-page-node-id="ABJ4iyIH5yqDsKXwJJQV5j">hugo-blog-tutorial</span> 文件夹，<strong data-page-node-id="qvQkZT5L0XZAzIAuWLR74d">把里面的内容全选，一起拖进浏览器窗口</strong>。</li>
  </ol>
  <div class="danger" data-page-node-id="pjPyAJyUL3PzF6H51yM6Ld">
    <strong data-page-node-id="M4xKtVlPK1bGKALeB63Ovf">这三个别搞错：</strong><br data-page-node-id="QmTK9lKkpYCnB8Jn3XJtSA">
    ① <span class="path" data-page-node-id="wGBnsgBqQRHqKUrTmUA9mG">教程.html</span> 不用上传 —— 那只是给你看的说明书。<br data-page-node-id="sS2Bs1M3qS78qADiFZZDys">
    ② <span class="path" data-page-node-id="Sbct01FlXf1E6TQyB1wEKY">.github</span> 文件夹<strong data-page-node-id="pFTE7DGMSFxDIr0Zv2ukjP">必须一起拖进去</strong>，它是那个「自动生成网页」的引擎，漏了就不会自动发布。<br data-page-node-id="lvJD8puG3SHEdejU4ML8Tw">
    ③ 拖进去的应该是<strong data-page-node-id="3q74PkAjA5bB8WdlVwVWXK">文件夹里面的东西</strong>，不是把 <span class="path" data-page-node-id="WGuflnpaXnEEZTGCCF8aQY">hugo-blog-tutorial</span> 这个外壳文件夹本身拖进去。
  </div>
  <ol start="3" data-page-node-id="9rV6ssxDaB6lRF9K77dJgH">
    <li data-page-node-id="z18gKrBe0NBuJCFACXpKmr">等页面上的文件列表都列出来（灰色的上传进度条走完）。</li>
    <li data-page-node-id="BF9XDwS5AiDEztO8OHsUiW">拉到页面最底部，<strong data-page-node-id="qee76vSnfn2uJOCgXNuwsa">Commit changes</strong> 那一栏随便写句话（比如「首次上传」），点绿色按钮 <strong data-page-node-id="qsGhwfxT9t8CorTGOo0rx8">Commit changes</strong>。</li>
  </ol>
  <p data-page-node-id="EPJX90lbTR31kPc13z1Zv0">传完后，仓库首页应该能看到这些：<span class="path" data-page-node-id="xZQe22PBffEeZG6XDUU6a9">.github</span>、<span class="path" data-page-node-id="P83OKiRgch6TKLgrm9xtdR">content</span>、<span class="path" data-page-node-id="AVUwTWFaMIo9EiVpwltd3T">hugo.toml</span>、<span class="path" data-page-node-id="H0SBdIpQIJJJmExcM6xocA">.gitignore</span>。</p>

  <h3 style="margin-top:32px;" data-page-node-id="BwDdEtQVlmxodBFH4b9qeJ">万一 <span class="path" data-page-node-id="EMYNnhIGtfcF9cpOUY0cAh">.github</span> 还是漏了（拖拽上传最常见的坑）</h3>
  <div class="danger" data-page-node-id="xUbEdr2tRBiWXZyInOccUB">
    <strong data-page-node-id="FN8TxZrr9GRafcZbotTSIA">为什么偏偏只缺了它：</strong>Windows 资源管理器<strong data-page-node-id="IE3WLaEvNQkvYzAa8jsXD7">默认不显示以「点」开头的文件</strong>。你全选文件夹里的内容时，<span class="path" data-page-node-id="pQQTITznaos3mZkWsUAu3I">.github</span> 和 <span class="path" data-page-node-id="F4jzcDYpB6uPSzA8XRkoA3">.gitignore</span> 根本没出现在列表里，压根没被选上。<br data-page-node-id="XSi83x8lS0V9BDxPIN0j6n">
    判断方法就一条：<strong data-page-node-id="gqM0TJ3UrXQMELWJILnSBN">看仓库首页有没有 <span class="path" data-page-node-id="BTr2WZkmg0m532QKjqUO6h">.github</span> 这个文件夹。</strong>没有，就照下面补。
  </div>
  <div class="warn" data-page-node-id="L4JqCWjLsAsE72VLa8gkoJ">
    <strong data-page-node-id="HuQhkomBdOPYqeRmmqrlyO">补的时候不能用「上传」。</strong>GitHub 网页的上传功能<strong data-page-node-id="oxfHrNtDCF0KDsEHpejZkk">会丢掉文件夹层级</strong> —— 把 <span class="path" data-page-node-id="JwFR89y2yFJTsylLvJi6wc">.github</span> 文件夹拖进去，里面的 <span class="path" data-page-node-id="gKYAYEz7kHHoe7H3HW3mbN">hugo.yml</span> 会被直接丢在仓库根目录，进不了 <span class="path" data-page-node-id="F5nDX7koh7oOTgxO9WPXeQ">.github/workflows/</span>，白传。<br data-page-node-id="IvUmAuRPqbdw8HylkL5s1p">
    正确做法只有一种：<strong data-page-node-id="mRF8GXZZcSF0qLbwWNCBM8">把带斜杠的完整路径直接敲进文件名框</strong>。
  </div>
  <p data-page-node-id="ROKwRL1AYhwqCMpMe7fsbP"><strong data-page-node-id="hI1WZR2Q8nACR4VUWuX3hh">正确做法 · 新建文件，路径直接敲进文件名框：</strong></p>
  <div class="step" data-page-node-id="AVSWNzc48QVIP7j89SknIM">
    <div class="step-head" data-page-node-id="vSx4VBE0mvBDwV2BJfmXXv"><div class="badge" data-page-node-id="mkHpgevGn5gIsZI0A7UoNI">1</div><div class="step-title" data-page-node-id="uBuWgfhZxiLObim0Yj8NlZ">新建文件</div></div>
    <p data-page-node-id="E8g00I7GsTbgH7Kusxjb3a">进仓库首页，点右侧的 <strong data-page-node-id="r5Jb4FflU8hyriKPsvxNpD">Add file</strong> → <strong data-page-node-id="FFWuPy99XO2v7MkSXpwQhk">Create new file</strong>。</p>
  </div>
  <div class="step" data-page-node-id="C9HnPGysx16rFe7chHZTDD">
    <div class="step-head" data-page-node-id="mvkCgh9IdY12ADl03F9bCi"><div class="badge" data-page-node-id="GGFNJQYZ8iIRuvF65gnXuG">2</div><div class="step-title" data-page-node-id="WKfJJ2zCA9WwKMbf8rPbyP">填文件名（斜杠会自动建文件夹）</div></div>
    <p data-page-node-id="t0NYrizUGYvSJ0VXv8Ry9w">在页面顶部的文件名输入框里，<strong data-page-node-id="hInoGDoZUpao9fKGX09KSF">完整输入下面这一串</strong>，一个字都不要少：</p>
    <div class="codebox" data-page-node-id="hl1700LCtAHCQ6gTBRYYnB">
      <button class="copy" onclick="copyCode(this)" data-page-node-id="7HekWx9Xk7j8AcyvOYBZbu">复制</button>
<pre data-page-node-id="SR2n69NZX4mI0Rd0gnXx73">.github/workflows/hugo.yml</pre>
    </div>
    <div class="warn" data-page-node-id="HYfL6iZktyHR9GREXq3hnu">输入框里只要看到斜杠，GitHub 就会自动帮你建成文件夹结构，你不需要手动「新建文件夹」。开头的那个点是英文句号，别漏。</div>
  </div>
</div>

<h2 id="step3" data-page-node-id="GigYo7rpvmPbaie5sO2WPL">第 3 步 · 打开发布开关</h2>
<div class="step" data-page-node-id="cHOzN6JQp0CFLdZk88rvA5">
  <div class="step-head" data-page-node-id="pQx2z9kGjh1FhIPE8htsXd"><div class="badge" data-page-node-id="HhsMf6cOmS77zXVIm0irBJ">3</div><div class="step-title" data-page-node-id="KF0NcSgDhN6DaQUTIwKxiz">告诉 GitHub「用自动流程发布」</div></div>
  <ol data-page-node-id="icDBQ8KAaqEdoLePWpyqxP">
    <li data-page-node-id="CXm5StyGNrD3v7mWNCUFZc">在仓库顶部的标签栏里点 <strong data-page-node-id="WAPsbjPSquzuJnCsaC4PVf">Settings</strong>（设置）。</li>
    <li data-page-node-id="zeVEOMdS8GQHaw6J3f2wg1">看左侧的竖排菜单，往下找到 <strong data-page-node-id="DfGhFBiGCi9okwOHT4S3Ka">Pages</strong>，点它。</li>
    <li data-page-node-id="nQEYLO3Iy9gnbKi1oE9Sop">页面上有一行 <strong data-page-node-id="7K9iX2oqpFxZ9DkUZRHib3">Source</strong>（来源），把右边的下拉框从 <em data-page-node-id="biNQtJKGL0uNdGpFvACZrx">Deploy from a branch</em> 改成 <strong data-page-node-id="EIMJwEXhvBGpNVxsasIVaC">GitHub Actions</strong>。</li>
  </ol>
  <div class="note" data-page-node-id="QSOsAlLbqH03rjRE41Hz6E">改完<strong data-page-node-id="994g4Ke4YZqBtCrjY5W70S">不用点保存</strong>，它立即生效。这行设置就是「网页由自动流程生成，而不是我手动上传」的意思。</div>
</div>

<h2 id="step4" data-page-node-id="OJe0V49o3Na1YNXieUztGI">第 4 步 · 等它自动生成</h2>
<div class="step" data-page-node-id="hu0LBR4pbM5kexVr34nCsh">
  <div class="step-head" data-page-node-id="Q3EE7bBNsqIHPjm1J53Z9H"><div class="badge" data-page-node-id="A6l3fB0iUtZKRXU9ohlL40">4</div><div class="step-title" data-page-node-id="tCHyvLLHSjY7fvJB3TVrDq">看绿勾就成功了</div></div>
  <ol data-page-node-id="s8sKFrX4hImbSXLDnNwgQ4">
    <li data-page-node-id="4ma65ECQFKuNmT8VuanyPM">点仓库顶部的 <strong data-page-node-id="VwTLUXlDMXTfqzBNPCbQrx">Actions</strong> 标签。你会看到一条任务正在跑，旁边是一个<strong data-page-node-id="lxmRC5JsV4UnmmfSb9G2I1">黄色转圈</strong>。</li>
    <li data-page-node-id="KFA96c0UK3HU0m4AkhWWrA">等 1～2 分钟，转圈变成<strong data-page-node-id="dbxDsRIjDySQ4RYBhL9x4b">绿色对勾</strong> = 发布成功。</li>
    <li data-page-node-id="qybKRRq8FuvoUYzsVhJCvT">点进这条任务，在左边列表里点 <strong data-page-node-id="JO1RHoATCyI9O4kxFsGsr3">deploy</strong>，右侧 <em data-page-node-id="UkbH4s50CAbYmA0NOFpSUe">Deploy to GitHub Pages</em> 下面会出现一个蓝色网址，点开就是你的博客。</li>
  </ol>
  <p data-page-node-id="FYlTKpNQu7aHQH4S5BSy0m">网址就是 <span class="path" data-page-node-id="rWkpUujMBILAZOZDH4je4b">https://你的用户名.github.io</span>，可以直接发给别人。</p>
  <div class="warn" data-page-node-id="U1YdM3JyrN6bPWKgiAqTy4">
    如果变成<strong data-page-node-id="001szkUni2vlEPD1oPejRR">红色叉号</strong>，说明自动流程哪一步出错了。别慌，第 5 步下面的「出问题了怎么办」有对照表。
  </div>
</div>

<h2 id="step5" data-page-node-id="27dEZs9BFpR9bEAOkYjRIJ">第 5 步 · 改成你自己的信息</h2>
<div class="step" data-page-node-id="WYnD4jAQjl8oIo96AnPDwU">
  <div class="step-head" data-page-node-id="pvEiQ63EKPeUugqhS2DZyX"><div class="badge" data-page-node-id="DP5nP5IYzi0ASMSJlNrEzz">5</div><div class="step-title" data-page-node-id="AWjToaAvaN5b51VNI3QOIo">改配置，改完自动重新发布</div></div>
  <ol data-page-node-id="EChwaCGj2jVFLwgCBP23zb">
    <li data-page-node-id="tHiwWvQlVIZkmfOzjzNklS">回仓库首页，点 <span class="path" data-page-node-id="w0HMmIRFXVMRKZXyKLbwcJ">hugo.toml</span> 这个文件。</li>
    <li data-page-node-id="0qHMmTS7wifI4xqhjN1rD3">点文件右上角的<strong data-page-node-id="tbAFCnUzrP9FvZ6YDIuEsk">铅笔图标</strong>（鼠标悬停会显示 Edit this file），进入编辑状态。</li>
    <li data-page-node-id="22TCH8ilxmtxoRlCqcSyeY">把下面这几行的内容换成你自己的：</li>
  </ol>
  <div class="codebox" data-page-node-id="NnwkoTbGsMd9QFNGUjIh3H">
    <button class="copy" onclick="copyCode(this)" data-page-node-id="vdz0yg9xECYR5Af4uFnuDn">复制</button>
<pre data-page-node-id="40XR4R5AEq0on7mTmI5Zld">baseURL = 'https://你的用户名.github.io/'
title = '我的博客'
  author = '你的名字'
  description = '这里写一句你的博客简介'
    Title = '你好，欢迎来我的博客'
    Content = '这里放一句欢迎语。'
    url = 'https://github.com/你的用户名'</pre>
  </div>
  <ol start="4" data-page-node-id="uWatK9gQunHWZ9U0lX1YBv">
    <li data-page-node-id="ZBZHIVjrJIIrEVSWFYhGZm">改完拉到最底部，点绿色按钮 <strong data-page-node-id="GBQQDN3iZFTM7SQvXlkG20">Commit changes</strong>。</li>
    <li data-page-node-id="m42lcQ9qnSRYp7u3HaxzSi">再回 Actions 看，它会自动重新跑一次，1～2 分钟后刷新你的网址就看到新内容了。</li>
  </ol>
  <div class="warn" data-page-node-id="8oF3TsyR5advyidjIlopUM">
    <strong data-page-node-id="Hb82oRQQPZq6aCgWr4gevo">改的时候只动单引号里面的字</strong>，别动单引号本身、别动等号、别动开头的空格。多一个少一个引号，自动流程就会报错。
  </div>
</div>

<h2 id="write" data-page-node-id="2Ma5oqBWWuo5AEB3LSCqHk">以后怎么写新文章</h2>
<p data-page-node-id="NSHy0LyZAVadh36y2D8Mpx">这是你日常唯一要会的操作，一共 4 下点击。</p>
<div class="step" data-page-node-id="fi2o9VBDHX5T1dkme9oTUd">
  <div class="step-head" data-page-node-id="qrr67Vt2lHqr4wcY93NWMc"><div class="badge" data-page-node-id="eVg9eGODSKLhzAT317HGCX">1</div><div class="step-title" data-page-node-id="9t73kkAkYlQ1RDMXauVWDj">进文章目录</div></div>
  <p data-page-node-id="FPlrSQ5pwvpBDP1VdR0oNk">仓库首页 → 点 <span class="path" data-page-node-id="YKOa2AUpE56X3kqr2OQHfi">content</span> 文件夹 → 再点 <span class="path" data-page-node-id="0Nx4k2WqxhZJnp6IGr1vgI">posts</span> 文件夹。你会看到示例文章 <span class="path" data-page-node-id="TYE5PX5SFqtAfJwpYn8uCj">我的第一篇文章.md</span>。</p>
</div>
<div class="step" data-page-node-id="jjfo9x6LxGkVolmRUBGJ91">
  <div class="step-head" data-page-node-id="LZbDeSItsJutpKKIfh2KNC"><div class="badge" data-page-node-id="Q7uzEfPPoJCzO7R80EP4mw">2</div><div class="step-title" data-page-node-id="RmNDG3FiqkovHwO76vNmek">新建一个文件</div></div>
  <p data-page-node-id="7bTzlI1owWi0F5FpvupHQa">点右上角 <strong data-page-node-id="tfos5ETJksohRPPPa3nr3l">Add file</strong> → <strong data-page-node-id="RiE8Ja1H9YiLUK3kC1MBmP">Create new file</strong>。文件名按这个格式写：</p>
  <div class="codebox" data-page-node-id="70CNobfgLxb3gbYXNFRYl4">
    <button class="copy" onclick="copyCode(this)" data-page-node-id="NlWlgmA2I68pQGs1uDDU7C">复制</button>
<pre data-page-node-id="vJQy3ZEpWgyfzEP3HtkGod">2026-10-03-我的第二篇文章.md</pre>
  </div>
  <p data-page-node-id="XYZ1ps7M3R8JhlQWi8DByf">也就是 <code class="inline" data-page-node-id="cbElmkRQC91L7bycWWSCCa">年-月-日-标题.md</code>，<strong data-page-node-id="Ci8n43CYnztW93gsccK0OU">结尾的 .md 必须保留</strong>。</p>
</div>
<div class="step" data-page-node-id="wNoeZuuOPli2SpnnHKU3oj">
  <div class="step-head" data-page-node-id="4tGzcu5ajAEhE3jx5ar3JZ"><div class="badge" data-page-node-id="HNiHkon1bRxZut4XIDh2YQ">3</div><div class="step-title" data-page-node-id="CsNPgGmK4zaGSZHAOjah1j">粘贴内容模板</div></div>
  <p data-page-node-id="5Yuqmd2p1Cw9tPk1Idt4NK">把下面整段复制进编辑框，然后只改引号里的东西，在三条横线下面写正文：</p>
  <div class="codebox" data-page-node-id="arGbNg3zN39fAWJoOHRONe">
    <button class="copy" onclick="copyCode(this)" data-page-node-id="oXDsKWMPgBSbWhMQchtJwU">复制</button>
<pre data-page-node-id="fxpwnILhKjvSwcJG7NJ7fQ">---
title: "我的第二篇文章"
date: 2026-10-03
draft: false
tags: ["教程"]
categories: ["随笔"]
summary: "一句话摘要，显示在文章列表里。"
---

正文从这里开始写。

## 这是一个小标题

- 列表第一项
- 列表第二项

**这是加粗**，*这是斜体*。
</pre>
  </div>
  <div class="danger" data-page-node-id="MXoojHrQnVEJv6u9yuKmZK">
    <strong data-page-node-id="QHT0CNp2uXDUAllijgvdFg">两个最容易踩的坑：</strong><br data-page-node-id="PX1QmCHxUVrNRZAIESDFkP">
    ① <span class="path" data-page-node-id="Tk5o4nLVckFtR2n6j2bzYA">draft: false</span> 一定要是 <strong data-page-node-id="JHzXmgEFWrurvgp9ViGnxu">false</strong>。写成 <span class="path" data-page-node-id="bw3OG0IWNjI3IFQ55MnqxO">true</span> 的文章属于「草稿」，<strong data-page-node-id="2hlYgmctOrqf8j70CayEUX">不会显示在网站上</strong>。<br data-page-node-id="2T3if1rMJskyflntvDRMI6">
    ② <span class="path" data-page-node-id="svC0K9HEpEGbLppYRVlsVw">date</span> <strong data-page-node-id="HJM9m3kvjAyYgLld3NKEld">填当天的日期</strong>，别往后写。写成未来的日期，文章同样不显示，而且<strong data-page-node-id="1aQeEERxcWOq8Y47bJEeJS">不报错</strong>，最容易被忽略。
  </div>
</div>
<div class="step" data-page-node-id="fdkONpFC4pJZZVpZ68vmjC">
  <div class="step-head" data-page-node-id="bQeoQwx2oKK7rEnCHAZdyZ"><div class="badge" data-page-node-id="qihDuEMXDwx4VOhmWhNqo4">4</div><div class="step-title" data-page-node-id="lQTtXxtwFiTPl43bjrhiOw">提交，等一分钟</div></div>
  <p data-page-node-id="yAHZkAKkjRwoofjXseogZm">拉到最底部点 <strong data-page-node-id="ZIEfgVoLRmc5hWDYYGR8zK">Commit changes</strong>。回 Actions 看绿勾，1～2 分钟后刷新网页，新文章就上线了。</p>
</div>

<h3 data-page-node-id="8gDW1Wg5SxEpZsCqjBXHVN">想在文章里插图片</h3>
<ol data-page-node-id="FPL3T5xxS0UEzxY011myUi">
  <li data-page-node-id="w24h8s4glBNEtvjfHeyNRO">先在仓库里建一个目录：<strong data-page-node-id="u90eEwZh5FiRh7x2fDY4aO">Add file</strong> → <strong data-page-node-id="uLtc6plGAHajwF5mz3W6bV">Create new file</strong>，文件名填 <span class="path" data-page-node-id="CTn5YhhNpOF9Ba0VjHZZv1">static/images/1.jpg</span>（斜杠会自动帮你建文件夹）。先随便存一下，然后再用 <strong data-page-node-id="HSVH7me2YsjcCKuMLrK6FD">Add file → Upload files</strong> 把图片传进 <span class="path" data-page-node-id="r8E0JnIj94BhOKnw3FJN5r">static/images/</span> 里。</li>
  <li data-page-node-id="Wg6h9bkhDcq7xWksyOopWN">在文章正文里这样写：</li>
</ol>
<div class="codebox" data-page-node-id="8Me43fl0ClFqOeAysry4Et">
  <button class="copy" onclick="copyCode(this)" data-page-node-id="sucv1EhGouklev13CbeLpF">复制</button>
<pre data-page-node-id="rLG15ZGdggPAWeVYP1gF0n">![图片说明](/images/1.jpg)</pre>
</div>

<h3 data-page-node-id="nmUSWh2BojyTAjowTmCqik">记住这一条就够了</h3>
<div class="note" data-page-node-id="pKlGEUUSWnOl4wvgGwIra5">
  <strong data-page-node-id="f5Y9x612FkUYmpFvaUQgdj">任何修改都是同一个套路：</strong>点开文件 → 点铅笔图标 → 改 → 底部 Commit changes → 等 1 分钟自动上线。没有别的操作，也没有「部署」这个步骤，GitHub 全都帮你做了。
</div>

<h2 id="info" data-page-node-id="UOqi1pKuioYrb9z347KYGB">补充 · 把博客的名字、作者和网址改成你自己的</h2>
<p data-page-node-id="yOPodvAb7STs8kMfzk5ImV">现在 <span class="path" data-page-node-id="XVYaxzpvggRo6ow73gFECD">hugo.toml</span> 里还是「你的用户名」「我的博客」这些占位文字，网站上线后会原样显示出来。点开 <span class="path" data-page-node-id="zXbWaOWOglcgBfteWKSApC">hugo.toml</span> → 点铅笔图标 → 按下表改 → 底部 Commit changes：</p>
<table data-page-node-id="SmROi3RvmvLDw82z3rN0bp">
  <tr data-page-node-id="n6WGC57wsMEojLBV8gTY4C"><th style="width:34%" data-page-node-id="pSsmDeRiZlVuHb7Oau0yBN">这一行</th><th data-page-node-id="4Z7zXUhQUBRchkVU1P2kug">改成什么</th></tr>
  <tr data-page-node-id="vse73DUhBtcKXHZYP8mXY2"><td data-page-node-id="4ikKfEyVMImTcTWGyuH3d2"><span class="path" data-page-node-id="sP7mSj1REsMFF6FXlfHKJT">baseURL = ...</span></td><td data-page-node-id="RXpQbDI8ky4YA3hOjApms4"><span class="path" data-page-node-id="DirFuUHr44jwLzbLwNECIA">'https://你的用户名.github.io/'</span><br data-page-node-id="ZWkkzwLcpCRZW1tgavypc6">如果仓库名不是 <span class="path" data-page-node-id="gJmunJBKmk7DY5O2PMCVPi">你的用户名.github.io</span>，就在末尾补上仓库名，比如 <span class="path" data-page-node-id="gFHmpY3GcDVWlZpaUFflaQ">'https://你的用户名.github.io/blog/'</span></td></tr>
  <tr data-page-node-id="3DOuXpJy836ALwBkJSLaNF"><td data-page-node-id="kbjddHRY04LPaojJHThs13"><span class="path" data-page-node-id="axioqfI8SUii2VaaupQD5G">title = ...</span></td><td data-page-node-id="KSyigGNiLDvzE8Jx348DBD">你的博客名字，比如 <span class="path" data-page-node-id="mAeimaOa9DeonIB11NNuTC">'我的笔记'</span></td></tr>
  <tr data-page-node-id="wa90GUlUiEZ8MLqdo1EPgU"><td data-page-node-id="8GYnU90VPY5CEUETdCKcIt"><span class="path" data-page-node-id="Mx9LpeYSSYOfw8ljrmDwqs">author = ...</span></td><td data-page-node-id="ljUYJi3YnKi8JiIGUJMTb5">你的名字</td></tr>
  <tr data-page-node-id="aHBJY6TxjCpdmiA8MeBjMa"><td data-page-node-id="zyLHH0yJZpOG2efysoJoyF"><span class="path" data-page-node-id="I584LqbRrLqiHRvrzDUx8B">description = ...</span></td><td data-page-node-id="1fFzNKfHF9kd3IhJNARaUH">一句话简介</td></tr>
  <tr data-page-node-id="D8X2aGZcbopFyEPZv7oO4N"><td data-page-node-id="i7sk1MpRbzmxFboKjWVSVo"><span class="path" data-page-node-id="1DdlgPL69UKHEIJ7suj8qA">url = 'https://github.com/...'</span></td><td data-page-node-id="EJAgY56cvcwp8E5Qo8azkJ"><span class="path" data-page-node-id="XcH5rhpnwuqChoRugUzheu">'https://github.com/你的用户名'</span></td></tr>
</table>
<div class="note" data-page-node-id="QOm65Z22wYvrCEWDRWtbU7">
  <strong data-page-node-id="fAd9d62bqkLcQJ2oeDl3nI">网址长什么样，取决于第 1 步仓库名怎么填的：</strong><br data-page-node-id="LWLRqG3DlFCHIgxR21Schx">
  仓库名叫 <span class="path" data-page-node-id="WQHMezDdOwrppTs361c96K">你的用户名.github.io</span> → 网址是 <span class="path" data-page-node-id="ry68PeinSXBmgArdpdgRLf">https://你的用户名.github.io</span>（最短）。<br data-page-node-id="gCMnfUp9aRaz2rut46APpo">
  仓库名是别的（比如 <span class="path" data-page-node-id="p3G2Rn9erXIrcNughZk0mm">blog</span>）→ 网址是 <span class="path" data-page-node-id="vkUv45eFZeegOsyKNuJott">https://你的用户名.github.io/blog/</span>，结尾那段就是仓库名，<strong data-page-node-id="0NqPTglfAh5jeXBBiXdXuk">正常的，不用管</strong>。<br data-page-node-id="7EDvoVf1Y0utDOv7Vte4Ly">
  两种都能用，功能完全一样。
</div>

<h2 id="html" data-page-node-id="dm5PmKih1fXg9BgipCdGmR">让文章能写 HTML（必须先开一个开关）</h2>
<div class="danger" data-page-node-id="5pdFKrhhewZi0d8ZIqp9KY">
  <strong data-page-node-id="HpMr2LsPwdDTzif1zY5shW">不做这一步，你写的 HTML 会被整段删掉。</strong>较新版本的 Hugo 出于安全考虑，
  默认<strong data-page-node-id="gpGBqSA217UXARRDbbA8FC">不允许</strong>文章里出现 HTML 标签。你写一个 <span class="path" data-page-node-id="BV9CK3NmWAO5XJSB8m4MVW">&lt;div&gt;...&lt;/div&gt;</span>，
  网页上那块直接变成空白——标签和里面的内容一起消失，而且<strong data-page-node-id="jnSRwzxIzcAfMX0GXScRnN">不报错</strong>，很难发现是这里的问题。
  打开下面这个开关就正常了。
</div>
<div class="step" data-page-node-id="Y9fPT2j4BMJ1idOEJFadpm">
  <div class="step-head" data-page-node-id="EtqTOxyYNzirxH4xXZzF38"><div class="badge" data-page-node-id="ZlMsYCpnvjsAYCxMJqA0Zz">1</div><div class="step-title" data-page-node-id="zaPF1Oyx7BCnl3KFBO3aGP">打开 hugo.toml</div></div>
  <p data-page-node-id="Euo7KJDnVMjhXfTZVzl5Oq">仓库首页 → 点 <span class="path" data-page-node-id="3nKqHhFBOU109Qbf8hhZbH">hugo.toml</span> → 点右上角<strong data-page-node-id="yR1d9Om2KFjVaqui6H3FuB">铅笔图标</strong>。</p>
</div>
<div class="step" data-page-node-id="KEtlvfLvk67oK4ckruJfkm">
  <div class="step-head" data-page-node-id="FaRazdCx775xJh1nD4TtME"><div class="badge" data-page-node-id="v8c88KvCGiWSePevCoqKou">2</div><div class="step-title" data-page-node-id="Gask2FQgTBmkxcPlBtPS5p">在 [markup] 下面插入两行</div></div>
  <p data-page-node-id="W0yCPAGrHVncIYzKkJg2np">往下找，有一行单独写着 <span class="path" data-page-node-id="wCElatMzq9rj9q0CFvkT0G">[markup]</span>。在它<strong data-page-node-id="bB2hsLgC8FNduofDXPINFc">正下方</strong>插入下面这两行：</p>
  <div class="codebox" data-page-node-id="6m4s0Xf4nE5tGKyCKEjVAw">
    <button class="copy" onclick="copyCode(this)" data-page-node-id="XnNf0VFfze13pSgAmK5IZw">复制</button>
<pre data-page-node-id="f0NK1HH8cIFA7Esup5YKz4">  [markup.goldmark.renderer]
    unsafe = true</pre>
  </div>
  <div class="warn" data-page-node-id="2nnnKhXvBZREp8q8RedySw">
    <strong data-page-node-id="kTDZgB9yFywGd7U9xrd6Kz">缩进是「两个空格」和「四个空格」，不要按 Tab 键。</strong>改完之后这一段应该长这样：<br data-page-node-id="BZiynQK2ymNbSasioNOYWu"><br data-page-node-id="pQGMZzpZgH6QqVgFgLrODF">
    <span class="path" data-page-node-id="7OhqmsMX0xi3hlc63NLfSm">[markup]</span><br data-page-node-id="gcvBlvVdAxCyBAHWVXEV0S">
    <span class="path" data-page-node-id="1YT0LSW5FxSSgQ8RWZHPMJ">&nbsp;&nbsp;[markup.goldmark.renderer]</span><br data-page-node-id="c7Dnexfc0rIZgQB01BOHFA">
    <span class="path" data-page-node-id="gOblI8eHOM1GHCusMBwAlY">&nbsp;&nbsp;&nbsp;&nbsp;unsafe = true</span><br data-page-node-id="N00SDHADLEoDB4g3roAFl7">
    <span class="path" data-page-node-id="GmTmqYycTtlr5CJAviQItP">&nbsp;&nbsp;[markup.highlight]</span><br data-page-node-id="Rqd9EEM98d2mFCqPT1usXH">
    <span class="path" data-page-node-id="tJtlQxcBsaF9G3oMdYgf53">&nbsp;&nbsp;&nbsp;&nbsp;noClasses = false</span>
  </div>
</div>
<div class="step" data-page-node-id="sEoygqj0Q6bshwnDTnIvxs">
  <div class="step-head" data-page-node-id="GpugMzbMDyCFCVSJ8cTtbB"><div class="badge" data-page-node-id="iHc1fx38oOlx1jOVyhBQdX">3</div><div class="step-title" data-page-node-id="F9oKDmZgvwsG7cYiCUUBA0">提交</div></div>
  <p data-page-node-id="qhz4CN8b1ndQcn79X4uJBm">拉到最底部点 <strong data-page-node-id="MkhNEPqSlkpxUEGCyTFELm">Commit changes</strong>。等 Actions 变绿，开关就生效了。</p>
</div>
<div class="step" data-page-node-id="ajmnBNb6S5RfNkS1oTPi4Z">
  <div class="step-head" data-page-node-id="sRftIVG9HpbRxIzNbM4amz"><div class="badge" data-page-node-id="M4J2TB412vRTGQJaiVJdw2">4</div><div class="step-title" data-page-node-id="0dacthsYVQcZAELRA1KJSF">写一篇含 HTML 的文章试试</div></div>
  <p data-page-node-id="MYkxHNBfP149Ke0zaN1Sht">按 <a href="#write" data-page-node-id="JxbYvPIJZFY9bgSt5WMLD7">《以后怎么写新文章》</a> 新建一个 <span class="path" data-page-node-id="yphHTd9Ggln5vzFz9xafQu">.md</span> 文件，
  正文里直接写 HTML 标签即可，样式用 <span class="path" data-page-node-id="to0YKqQcKNFTqr4l65ZFyH">style="..."</span> 写在标签上：</p>
  <div class="codebox" data-page-node-id="t9FVDUJo2KPdVwQmkDDFAD">
    <button class="copy" onclick="copyCode(this)" data-page-node-id="JzQ57YoEF4SmXqXhxKlbnM">复制</button>
<pre data-page-node-id="QobxEQFqUQL3yUzGUguroR">普通正文还是用 Markdown 写。

&lt;div style="padding:16px 20px;border-left:4px solid #378add;background:#eef4fb;border-radius:6px;"&gt;
  &lt;strong&gt;提示&lt;/strong&gt;&lt;br&gt;
  这一段是 HTML 写的，Markdown 做不到这种样式。
&lt;/div&gt;

&lt;div style="display:flex;gap:12px;"&gt;
  &lt;div style="flex:1;padding:14px;border:1px solid #dddddd;border-radius:8px;"&gt;
    左栏
  &lt;/div&gt;
  &lt;div style="flex:1;padding:14px;border:1px solid #dddddd;border-radius:8px;"&gt;
    右栏
  &lt;/div&gt;
&lt;/div&gt;</pre>
  </div>
  <div class="note" data-page-node-id="AOP9Y0LVf9VVRHbfRmawN4"><strong data-page-node-id="PFeeOoOE9REEng8toGhxFc">Markdown 和 HTML 可以混着写</strong>，一篇文章里两段 Markdown、一段 HTML 完全没问题。仓库里 <span class="path" data-page-node-id="OhVquZdRYsjuYkMXGQcAAS">content/posts/</span> 下有一篇《在文章里写 HTML 的示例》，上面这段的完整版本就在那儿，可以直接照抄。</div>
</div>

<h2 id="style" data-page-node-id="9jzvl9HVT58DJNDbjt8wh9">改页面样式（配色、宽度、字号）</h2>
<div class="note" data-page-node-id="Zkim71UFLIqziLMbMhS6nM">
  <strong data-page-node-id="Ei2ZTQKACTz0ZZgyDG4lgS">不用碰主题文件。</strong>PaperMod 留了一个口子：只要在仓库里建出
  <span class="path" data-page-node-id="gRctWiuDQFNLm1Pt2vMONU">assets/css/extended/</span> 这个目录，里面的<strong data-page-node-id="gxgK8NnmU1n7A2nJXAcdp9">所有 .css 文件都会被自动合并进网站</strong>。
  你只改自己的文件，主题以后自动更新也不会把你的改动冲掉。
</div>
<div class="step" data-page-node-id="xfAxcw6IXgNO2Kmmu8g4eE">
  <div class="step-head" data-page-node-id="40Uiml5Cu5n2ndHECMATGk"><div class="badge" data-page-node-id="IiK8rRjzUR6e35xRRiTquZ">1</div><div class="step-title" data-page-node-id="MTDRZkorFzkZkbPFOxIrRi">新建样式文件</div></div>
  <p data-page-node-id="ewvshAKCcgW2SzUFAhgfFK">仓库首页 → <strong data-page-node-id="vsJd7vSZsxD4KBKBeUj2hk">Add file</strong> → <strong data-page-node-id="NT19P06sNciEgDEJ38SBOQ">Create new file</strong> → 文件名框<strong data-page-node-id="I0QbNYPzWCCeXZXR7LwkFY">完整输入</strong>：</p>
  <div class="codebox" data-page-node-id="6FFqHJDnDfSO1UBdSjP0qh">
    <button class="copy" onclick="copyCode(this)" data-page-node-id="OpQvFHxlq2oSF397CHftqu">复制</button>
<pre data-page-node-id="4mWydzBcLsEqI8GyOkYh3i">assets/css/extended/custom.css</pre>
  </div>
  <p data-page-node-id="PZ0CjIMlCr63y2PFVoBY9Q">斜杠会自动建好两层文件夹。</p>
</div>
<div class="step" data-page-node-id="73pOSb9oxRstDhMpGiYcmR">
  <div class="step-head" data-page-node-id="ZpNFjrhYkq0rkHEZWzw3j5"><div class="badge" data-page-node-id="la1QTFzFGLleqbeKRXNyYC">2</div><div class="step-title" data-page-node-id="Wuh1zFUgvwVxsUFJU48SId">粘贴样式内容</div></div>
  <div class="codebox" data-page-node-id="T4Jk0dV5hZxsGrLEsfxm7g">
    <button class="copy" onclick="copyCode(this)" data-page-node-id="2ziMRidAPG9vkIpLnHYlhT">复制</button>
<pre data-page-node-id="5QGsMllowLmAgalerycXdK">/* ① 正在生效：正文宽度。默认 720px */
:root {
  --main-width: 860px;
}

/* ② 改字号和行距：去掉下面整段的注释符号就生效
.post-content {
  font-size: 17px;
  line-height: 1.9;
}
*/

/* ③ 改配色：去掉下面的注释符号
:root {
  --primary: rgb(20, 20, 20);
  --secondary: rgb(108, 108, 108);
  --theme: rgb(255, 255, 255);
  --border: rgb(238, 238, 238);
}
*/

/* ④ 深色模式要单独改，否则读者切深色时看不到你的配色
:root[data-theme="dark"] {
  --primary: rgb(230, 230, 230);
  --theme: rgb(24, 25, 27);
}
*/

/* ⑤ 隐藏页面元素：去掉下面的注释符号
.post-meta { display: none; }
.footer { display: none; }
.top-link { display: none; }
*/</pre>
  </div>
  <p data-page-node-id="NwuX0Ionae1Zvpgw9xK0a8">拉到最底部点 <strong data-page-node-id="1Hwlp0ruEEixZqsUYMt6Eh">Commit changes</strong>，约 1 分钟后刷新网页就能看到变化（正文变宽了）。</p>
</div>

<h3 data-page-node-id="KtztZISRFzWaoX2aQNp6IK">能改哪些东西</h3>
<table data-page-node-id="iG39FYFFqGqpIFyDIxYBLW">
  <tr data-page-node-id="Jj1ugb8DslKnZXmNqpp7Hi"><th style="width:30%" data-page-node-id="fW7vFlEx1Ppek85Xk4FOsF">变量名</th><th style="width:26%" data-page-node-id="DYhv9FQ1ax4MY3uJjZJkh1">默认值</th><th data-page-node-id="XuKvIIWmv8H9Zs5xtI1hBF">管什么</th></tr>
  <tr data-page-node-id="sKKkQ4rruQMbAXgrXH7Sg1"><td data-page-node-id="9FyHBdfrnNWBILluZjOyP7"><span class="path" data-page-node-id="gcCzGkDARFyUh1SDdyE66O">--main-width</span></td><td data-page-node-id="ftkp17wxlEmBaSaM7IcbYh"><span class="path" data-page-node-id="NbDAM0DFCAFLRLyvxg0ag6">720px</span></td><td data-page-node-id="dRNxstFLMf5PzXnfRvDC7B">正文区域宽度</td></tr>
  <tr data-page-node-id="W8LWSOVXWfANTt5uPDwDr4"><td data-page-node-id="y0WEx1NgWrQfPkxdT5wmWt"><span class="path" data-page-node-id="a33F55PVAgYHYBMqCPO8cY">--nav-width</span></td><td data-page-node-id="CtOcLbpP0XKTP7pBsVq5za"><span class="path" data-page-node-id="g6iJdduYgFcpxBzaQ4dO0s">1024px</span></td><td data-page-node-id="oAJPejmBEHtjQ2AsQG32c9">顶部导航栏宽度</td></tr>
  <tr data-page-node-id="qsGkSi1n3fApXpuFZeG7my"><td data-page-node-id="VGvoCtlZF3SVGPBmdfbV1T"><span class="path" data-page-node-id="rB12XVsvZOwBIIy3dCixIn">--radius</span></td><td data-page-node-id="2NCGQL2i1czurRusRtbuRe"><span class="path" data-page-node-id="isUcXdUUa4FlYuM68EIgUO">8px</span></td><td data-page-node-id="Now4z6fUc1ME0ATGiYeOOW">卡片、代码块的圆角</td></tr>
  <tr data-page-node-id="VN1L18kCpGdsNknLWAsnvi"><td data-page-node-id="FIKYNfBvQZPSEsNYHKRXqU"><span class="path" data-page-node-id="zGHxDkT2txBNSrHB5wqMCi">--gap</span></td><td data-page-node-id="A5R4TIcztHRuhU9pzQDm6P"><span class="path" data-page-node-id="shpzBt8GiX7KF9JN4uwH1E">24px</span></td><td data-page-node-id="N0D9BYbaT6wM0Z07mKuq6Z">元素之间的间距</td></tr>
  <tr data-page-node-id="XBlgqvZ4r1u5AJAAsqNVsV"><td data-page-node-id="d6gHTk1PA2xixzt0GPA7jO"><span class="path" data-page-node-id="x3MxERQJtCkdFtgmNyxPHE">--theme</span></td><td data-page-node-id="r6bW9DuN2rkIu7ubzCqtL6"><span class="path" data-page-node-id="KLNfqBHmnCUht0mTdEQrOC">rgb(255,255,255)</span></td><td data-page-node-id="TjaZ2CSCQYwhRmmMs1zo2W">页面背景色</td></tr>
  <tr data-page-node-id="gNN8DBJVdi8ub7bjIPeEzG"><td data-page-node-id="ZOziPAt8tw35YdsxIXkVwo"><span class="path" data-page-node-id="8mQ3c757RPmO4HTcuBpWTP">--primary</span></td><td data-page-node-id="2kdZvyuyKeXwyFWbC33wZ0"><span class="path" data-page-node-id="YwRqXIWtHwJ6fTnx1A2AlK">rgb(30,30,30)</span></td><td data-page-node-id="XUwGnRIIOYmyPDbiIWpt7n">主要文字颜色</td></tr>
  <tr data-page-node-id="QGWecumiSJ7guTiMUPR43V"><td data-page-node-id="5klVlOQgdo93iLqa478RXU"><span class="path" data-page-node-id="58hqOuMdXN90bz2H4HVDJs">--secondary</span></td><td data-page-node-id="1nBjH5SxoRTxYzZuBRNJAH"><span class="path" data-page-node-id="pPeHVdxhzRUEcxv0aEdrxN">rgb(108,108,108)</span></td><td data-page-node-id="FSGFMoyUaJIuTSjRmX9XYH">日期、摘要等次要文字</td></tr>
  <tr data-page-node-id="YwbTgHLsN4uUmnyqzK9Zxi"><td data-page-node-id="nnOlOpdgARWMvUsBGZJ3QD"><span class="path" data-page-node-id="lkJcuESXmL8YdnCMkoriUs">--border</span></td><td data-page-node-id="EZPYjKDZAOPyG6ven8Eswr"><span class="path" data-page-node-id="z7hU428PRuKdeozoNBgyDy">rgb(238,238,238)</span></td><td data-page-node-id="p2wpC2uLc5lWkiMs4Ls2ag">分割线颜色</td></tr>
</table>
<div class="warn" data-page-node-id="HsCB5BkxnUDaCYrTeRUj60">
  <strong data-page-node-id="euNVEnJ1osxoe98ZfPBABU">改颜色的两个坑：</strong><br data-page-node-id="IHB2evgJ1H4xDULEHArhGJ">
  ① 颜色要写成 <span class="path" data-page-node-id="KBdIdBO2SSBSEo5aMplmHK">rgb(30,30,30)</span> 或 <span class="path" data-page-node-id="daETCz3oAUR3m4kmbXlvz7">#1e1e1e</span> 这种格式，不要写「黑色」「深灰」；<br data-page-node-id="NzBQ8snHALy2UqAQOfzF2o">
  ② 页面有<strong data-page-node-id="2PNGtdq9Lx3aQwm9W2x1VT">浅色和深色两套</strong>配色。你只改浅色的那套，读者把系统切成深色模式时页面会变回默认色，可能看不清。所以第 ④ 段要一起改。
</div>
<div class="note" data-page-node-id="MGhVzaxzfRPcaup6yAUaVS">
  <strong data-page-node-id="nEFlw5bCi0ERPnBjIzsC7S">想大改（换布局、加侧边栏）怎么办：</strong>那需要改主题的模板文件，做法是在自己仓库里建一个同名的
  <span class="path" data-page-node-id="Saot10IKReAdgPtR6bQtvp">layouts/</span> 文件去覆盖主题的。这个复杂度就上来了，建议先用上面的 CSS 变量把能调的调完。
</div>

<h2 id="fix" data-page-node-id="h1Xvi2bH54W1LpmAu5osJF">出问题了怎么办</h2>
<table data-page-node-id="DioyMCSMJUZQclsFMpdEAF">
  <tr data-page-node-id="NTfUK1PZxVQkfUQFfa8Bp2"><th style="width:38%" data-page-node-id="XTkKxVcQG7LH8Ej3sBHT7o">现象</th><th data-page-node-id="UDls2fQV5N79H6Zmxuep5m">原因和解决办法</th></tr>
  <tr data-page-node-id="JqKdc3pqyIalFjCDaCsRrK">
    <td data-page-node-id="q8cUX0Hhaot0qLHXYxcfDs">Actions 页面是「Get started with GitHub Actions」欢迎页<br data-page-node-id="igZ8ksTZp1m7wrlsfQe5AJ">或仓库根目录有个孤零零的 <span class="path" data-page-node-id="h2h8dh2sSiQx840KC1dfai">hugo.yml</span></td>
    <td data-page-node-id="Sxq4R31sMnQoDijyByZQvs">缺 <span class="path" data-page-node-id="5mccASaUxaJuHIBj7utjez">.github</span> 文件夹（资源管理器默认不显示点开头的文件，全选时选不到）。照 <a href="#step2" data-page-node-id="vhgZIMvD5hTNJSd4Piae4N">第 2 步里「万一 .github 还是漏了」</a> 做一次即可。</td>
  </tr>
  <tr data-page-node-id="IgOvLP31jgVxNoEjpNZh57">
    <td data-page-node-id="aRBkDhYPy2Hd5FkoC83GLZ">打开网址显示 404</td>
    <td data-page-node-id="FQArlrKtmwb6JSP7AwNSKT">① 先等 2 分钟再刷新；② 还不行就去 <strong data-page-node-id="iKrYulQQp6zvxRfVFBIIiX">Settings → Pages</strong> 确认 Source 已经是 <em data-page-node-id="KNuFmuWTVEeJRP8simeREm">GitHub Actions</em>；③ 确认第 2 步上传的文件里确实有 <span class="path" data-page-node-id="g7n7tBXLU52dKcbO2ossCJ">.github</span> 文件夹。</td>
  </tr>
  <tr data-page-node-id="XfFtAE2zMCe6RuLierVdgH">
    <td data-page-node-id="A3qMvGjea4pRmWBYBoyeDo">Actions 里是红色叉号</td>
    <td data-page-node-id="McDF9Po0H56ESDFIpSywfN">点进那个红色任务，看哪一步是红的。<strong data-page-node-id="QSRTSosQ5l1fxOSVfGc5qZ">九成的情况是 <span class="path" data-page-node-id="U325yjWeUH8sFDhAcJJGvn">hugo.toml</span> 写错了</strong>：引号没配对、等号丢了、或者某一行开头的空格被删掉了。把文件改回原样试试。</td>
  </tr>
  <tr data-page-node-id="fnLyiu3C7c5cwjXrke5mc7">
    <td data-page-node-id="dP5tsGMvomqpAt8fJo1FHk">页面出来了，但点「归档 / 搜索 / 关于」是 404</td>
    <td data-page-node-id="27Sq9hDnRJl97j16K9BGLx"><span class="path" data-page-node-id="PLKZn96A1IeoxYGzn1KZUz">content</span> 目录里少了对应的文件。检查 <span class="path" data-page-node-id="eTJwqV6rHM9RzBv7b2lCae">archives.md</span>、<span class="path" data-page-node-id="LpAuJaxlo95HJ9vd9mre01">search.md</span>、<span class="path" data-page-node-id="x82Eh1dCXpIzluOqhTp1Ll">about.md</span> 是不是都在。</td>
  </tr>
  <tr data-page-node-id="yirRo5VxvgFZjL39wNFCtm">
    <td data-page-node-id="3T4CAeL3DAvEUenhfGlRFA"><strong data-page-node-id="5NqT3uTGUxpyGylImW37Ir">改完东西，网站上看不到变化（文章不出现、文字没改）</strong></td>
    <td data-page-node-id="PM0GvHXzWH935ACml48tLT"><strong data-page-node-id="tU0H0FrLxRnwrdZrkVWX3I">先做这一步，多数情况是浏览器缓存。</strong>浏览器会把页面存起来省流量，默认几小时内不重新下载。强制刷新一次：按 <span class="path" data-page-node-id="mqATVmfxqhEfdMZVlLapnz">Ctrl + F5</span>（笔记本有些要按 <span class="path" data-page-node-id="Gpw2RGhzwmHunRuyKjQKzd">Ctrl + Fn + F5</span>）。不行就换个方式验：<br data-page-node-id="4OfhfjiqgdYAYLXMpLSvsX">
      ① 用<strong data-page-node-id="WG1o99a0BDR5Ob9xFE55wn">无痕窗口</strong>（Chrome/Edge 按 <span class="path" data-page-node-id="Tztd3Jb464mK3Pb4EchY0J">Ctrl + Shift + N</span>）打开你的博客网址；<br data-page-node-id="1P488soCdeXp6MjO8kh8cA">
      ② 或者把网址后面加个问号再加几个字，比如在地址栏末尾补上 <span class="path" data-page-node-id="HGWFmHDMblEOAtStsx3Vf4">?v=2</span> 回车。<br data-page-node-id="04VdYqrXMaEHr20DHwnkK8">
      这两个办法都能绕过缓存。如果无痕窗口能看到、普通窗口看不到，那就是缓存，不用再改任何文件。</td>
  </tr>
  <tr data-page-node-id="ZeSSUfGZbEZQ2jelAoVcxk">
    <td data-page-node-id="AwFMNg7UBGnZuDUYdeiB5j"><strong data-page-node-id="LQiAmS6F7RKCZ9S3aaOUHb">确定不是缓存，文章文件也传上去了，Actions 还是绿的，但网站上就是没有这篇</strong></td>
    <td data-page-node-id="mkp0hPBXWoMNDRGVfeHRwu">按这个顺序查，三条几乎覆盖全部情况：<br data-page-node-id="pVAAV7skAbxQiKiGxXWPwd">
      ① <strong data-page-node-id="sAF9wQD2wmQsG3sZaTehAY">最常见：<span class="path" data-page-node-id="3pzUSSPNE5FrVFf3mUmBwH">date</span> 写成了未来的日期。</strong>Hugo 认为「未来的文章还没到发布时间」，直接不生成，而且<strong data-page-node-id="wpBGrtWBXaAHyDaaf6UMQj">不报错</strong>。今天的日期是几号就写几号，或者写更早的日期。判断方法：看你电脑右下角的日期，跟文章里的 <span class="path" data-page-node-id="qfFtk54rDJCpi4cBlJ8MdB">date</span> 比一下。<br data-page-node-id="KBXQD8kVYmDaHoCDrG4n7A">
      ② <span class="path" data-page-node-id="OOe9BSCja8ne3G3YBYuTVE">draft</span> 写成了 <span class="path" data-page-node-id="pfBIQb8uSJbtLoBBh76EnO">true</span>，必须是 <span class="path" data-page-node-id="2nqGqulOB4R2EDeR7kqpko">false</span>。<br data-page-node-id="zuu3nwW3OOpGESwrJfxLmY">
      ③ 文件名结尾不是 <span class="path" data-page-node-id="K4LmDgHCuEfcczEgoN4RnA">.md</span>（比如存成了 <span class="path" data-page-node-id="4AqGGJXEmBqW8lhEsDTPv8">.md.txt</span>，资源管理器默认藏扩展名，看不出来）。</td>
  </tr>
  <tr data-page-node-id="IqWQlJb7fr4xhBM0YGLMRw">
    <td data-page-node-id="8QaJOYdKE6mliidsoCxDyw">网址后面多了一串仓库名</td>
    <td data-page-node-id="G3rC4K3fYV3g4A1zxAf8ym">说明仓库名不是 <span class="path" data-page-node-id="e28sx0XhAxpsSpRkmAANQU">用户名.github.io</span>。不影响使用。真要改只能重建仓库。</td>
  </tr>
  <tr data-page-node-id="dGTZdE4KprnBMfaMDzYDmZ">
    <td data-page-node-id="JVWLxovNpI905mn6dvKBxQ">想换配色、换字号</td>
    <td data-page-node-id="hCaNJET3qzsev1wcA8z9B1">照 <a href="#style" data-page-node-id="DLgJJVs5BvKJbarjvoombK">《改页面样式》</a> 那节做，不用动主题文件。PaperMod 还自带浅色/深色自动切换，读者用深色系统时页面会自动变深。</td>
  </tr>
  <tr data-page-node-id="sVTAqB4NM3gC4rANXjFgIA">
    <td data-page-node-id="Bx4xVID0dosiDpcsxeYkUU">文章写错了想删掉</td>
    <td data-page-node-id="WxPcLvh3SA5HEmxe5sKAT8">点开那个 <span class="path" data-page-node-id="GS9dYlNtnxwD0XlzUrjEHe">.md</span> 文件 → 右上角 <strong data-page-node-id="9jNflPIpoHC9NnBfLhi7wa">⋯</strong> 下拉菜单（删除选项藏在里面）→ <strong data-page-node-id="pQQ3g65fHr9dGeXnYB378C">Delete file</strong> → 底部 <strong data-page-node-id="xTv1u786htIAUH8ecBBi8E">Commit changes</strong>。1 分钟后网站上的那篇也消失了。</td>
  </tr>
</table>

<h2 id="domain" data-page-node-id="ro5ISHU3S65dQEkdCXV4uB">可选 · 换成自己的域名</h2>
<p data-page-node-id="VFKEi5m1CXLQeWpeQM3c0F">不做这一步也完全能用，<span class="path" data-page-node-id="sPB5KOsk0T53IUlQOsKj20">用户名.github.io</span> 免费且带 HTTPS。</p>
<ol data-page-node-id="6CALKABoQDdGOgu05zUy6W">
  <li data-page-node-id="2dRBJGDFutasDsu9Bbr18C">去域名商（阿里云、腾讯云、Namesilo 等）买一个域名。</li>
  <li data-page-node-id="E9S5scQBEHiQt3xbp6DOWV">在域名商后台添加一条 <strong data-page-node-id="wmtjBypXIQs2TCVa2kMzKV">CNAME 记录</strong>：主机记录填 <span class="path" data-page-node-id="U2hRLWpYbfCXpB3IdOuctY">www</span> 或 <span class="path" data-page-node-id="d2qnnSrQoqESyTY78BvypM">@</span>，记录值填 <span class="path" data-page-node-id="speb9Yov1c9x4deJx1wrhq">你的用户名.github.io</span>。</li>
  <li data-page-node-id="MOACvZJ2CXAIRmG705PTCN">回仓库 <strong data-page-node-id="XhyYkGAO8V7CiEAVu4KZtL">Settings → Pages</strong>，在 <strong data-page-node-id="abLNebYwc0jOdOasQwviZP">Custom domain</strong> 框里填你的域名，点 <strong data-page-node-id="VGL3kQHhiIsxmL9h6TODo2">Save</strong>。</li>
  <li data-page-node-id="dtzLdG7FsXe8JoLTckbU8Z">等几分钟，勾上下面的 <strong data-page-node-id="xKomjazCtdb2SEjJNFiVk8">Enforce HTTPS</strong>（强制加密）。证书是 GitHub 免费签发的。</li>
</ol>
<p data-page-node-id="Tu6HaaxaABxqc1of6aBAYi"><strong data-page-node-id="PwbTJCK16GfSFtt9RLSVw6">注意</strong>：绑了自定义域名之后，记得把 <span class="path" data-page-node-id="4gNwsgACAuIqYLNvNrJbNr">hugo.toml</span> 里的 <span class="path" data-page-node-id="PYooEBcrJUeofSPQyRGDWx">baseURL</span> 也改成新域名，否则站内链接可能跳错。</p>

<h2 data-page-node-id="7zt1SNw4HEzy541sQoLiUg">关于费用和隐私</h2>
<ul data-page-node-id="s6XbWCP4pD8QSRQ2SA69Mm">
  <li data-page-node-id="RH36FrsOgudLKrA8dpxIEN"><strong data-page-node-id="ucSSBCX459VCaWl1RDibBT">费用</strong>：公开仓库 + GitHub Pages，完全免费，无广告，无流量限制条款上的坑。</li>
  <li data-page-node-id="es888KFnDZSlGbfRF1XqAX"><strong data-page-node-id="UGzS6LRUIp3WBu4WBygyK3">隐私</strong>：仓库是公开的，任何人点进你的 GitHub 主页都能看到文章源码，也能搜到。<strong data-page-node-id="S6AlhCQASmPs7svReLT5PP">「只有拿到链接才能看」做不到</strong>，除非你升级付费账户。所以别放敏感内容。</li>
  <li data-page-node-id="PkMXo8Ed7VXV403hHaEbCF"><strong data-page-node-id="sAwdwH65DTpzh7Jsu1YlNs">发现机制</strong>：没有点赞、没有评论、没有推荐流，不会主动推给别人。但搜索引擎依然可能收录，这是所有公开网页的共性。</li>
</ul>

<footer data-page-node-id="wBq14XpaPF8ABF9fRBSrtu">
  这份教程对应的是 Hugo 0.167.0 + PaperMod 主题。主题会在每次发布时自动下载最新版，你不需要手动更新。
</footer>

</div>

<script>
function copyCode(btn) {
  var pre = btn.parentNode.querySelector('pre');
  var text = pre.innerText;
  var done = function () {
    btn.textContent = '已复制';
    btn.classList.add('done');
    setTimeout(function () {
      btn.textContent = '复制';
      btn.classList.remove('done');
    }, 1500);
  };
  if (navigator.clipboard && navigator.clipboard.writeText) {
    navigator.clipboard.writeText(text).then(done, function () { fallback(text, done); });
  } else {
    fallback(text, done);
  }
}
function fallback(text, done) {
  var ta = document.createElement('textarea');
  ta.value = text;
  ta.style.position = 'fixed';
  ta.style.opacity = '0';
  document.body.appendChild(ta);
  ta.select();
  try { document.execCommand('copy'); done(); } catch (e) { alert('复制失败，请手动选中复制'); }
  document.body.removeChild(ta);
}
</script>
</body>
</html>
