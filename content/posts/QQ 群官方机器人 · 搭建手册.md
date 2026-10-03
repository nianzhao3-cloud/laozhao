
---
title: "QQ 群官方机器人 · 搭建手册（含接入 AI）"
date: 2026-10-03
draft: false
tags: ["教学"]
categories: ["教学"]
summary: "搭建qq开放平台官方机器人"
---


<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>QQ 群机器人 · 搭建手册（含接入 AI）</title>
<style>
  * { box-sizing: border-box; }
  body {
    margin: 0; padding: 0 16px 80px;
    background: #f4f6fa; color: #1f2430;
    font-family: -apple-system, BlinkMacSystemFont, "PingFang SC", "Microsoft YaHei", "Segoe UI", sans-serif;
    line-height: 1.7; font-size: 15px;
  }
  .wrap { max-width: 880px; margin: 0 auto; }
  header {
    margin: 32px 0 26px; padding: 28px 30px; border-radius: 16px;
    background: linear-gradient(135deg, #eaf3ff 0%, #f0f7ff 55%, #f7fbff 100%);
    border: 1px solid #d8e6f8;
  }
  header h1 { margin: 0 0 8px; font-size: 25px; letter-spacing: .5px; }
  header p { margin: 0; color: #52606f; font-size: 14.5px; }
  .pill {
    display: inline-block; margin-top: 14px; padding: 4px 12px; border-radius: 999px;
    background: #fff; border: 1px solid #cfe1f7; color: #1a6fd4; font-size: 13px; font-weight: 600;
  }
  .alert {
    margin-top: 18px; padding: 16px 19px; border-radius: 12px;
    background: #fff8ec; border: 1px solid #f2d9a6; border-left: 4px solid #f0a63a;
    color: #6e5218; font-size: 13.5px;
  }
  .alert .alert-t { font-size: 15.5px; font-weight: 700; color: #8a5a10; margin-bottom: 7px; }
  .alert p { margin: 0 0 9px; color: #6e5218; }
  .alert ul { margin: 8px 0 0; padding-left: 20px; }
  .alert li { margin-bottom: 7px; }
  .alert li:last-child { margin-bottom: 0; }
  h2 { margin: 40px 0 6px; font-size: 19px; display: flex; align-items: center; gap: 10px; }
  h2 .num {
    width: 28px; height: 28px; flex: 0 0 28px; border-radius: 9px;
    background: #1a6fd4; color: #fff; font-size: 14px;
    display: flex; align-items: center; justify-content: center; font-weight: 700;
  }
  h2 .num.gray { background: #8895a4; }
  h2 .num.adv { background: #2f9e6e; }
  .sub { margin: 0 0 16px 38px; color: #63707f; font-size: 13.5px; }
  .sech {
    margin: 24px 0 11px; padding-left: 11px; font-size: 15.5px; font-weight: 700; color: #12161d;
    border-left: 4px solid #d9e6f5; line-height: 1.4;
  }
  .card {
    background: #fff; border: 1px solid #e3e8f0; border-radius: 14px;
    padding: 20px 22px; margin-bottom: 16px;
  }
  .card h3 { margin: 0 0 10px; font-size: 15.5px; }
  .card ol, .card ul { margin: 8px 0 0; padding-left: 20px; }
  .card li { margin-bottom: 7px; }
  code.k {
    background: #eef3f9; border: 1px solid #dbe5f0; border-radius: 5px;
    padding: 1px 6px; font-size: 13px; font-family: ui-monospace, Consolas, monospace;
    color: #1a518f;
  }
  b { color: #12161d; }
  .flow { display: flex; align-items: stretch; gap: 10px; flex-wrap: wrap; margin-top: 6px; }
  .fbox {
    flex: 1 1 170px; background: #f7fafd; border: 1px solid #e0eaf5;
    border-radius: 11px; padding: 12px 14px; font-size: 13px; color: #46525f;
  }
  .fbox strong { display: block; color: #1a6fd4; font-size: 13.5px; margin-bottom: 3px; }
  .arrow { align-self: center; color: #9db4cb; font-size: 20px; }
  .note {
    border-left: 3px solid #f0a63a; background: #fff8ec; border-radius: 0 10px 10px 0;
    padding: 11px 15px; margin: 14px 0 0; font-size: 13.5px; color: #7a5a1c;
  }
  .note.blue { border-left-color: #3b8ee0; background: #eef6ff; color: #22537f; }
  .note.red { border-left-color: #e0574a; background: #fdf1f0; color: #8a332a; }
  .note.green { border-left-color: #38a169; background: #eefaf1; color: #22663c; }
  .cmd {
    background: #fff; border: 1px solid #e3e8f0; border-radius: 12px;
    margin-bottom: 13px; overflow: hidden;
  }
  .cmd .bar {
    display: flex; align-items: center; gap: 9px;
    padding: 8px 12px; background: #f8fafd; border-bottom: 1px solid #edf1f7;
  }
  .tag {
    font-family: ui-monospace, Consolas, monospace; font-size: 11.5px; font-weight: 700;
    background: #e7f0fd; color: #1a6fd4; border-radius: 6px; padding: 2px 7px;
  }
  .tag.green { background: #e6f7ee; color: #2f9e6e; }
  .ttl { font-size: 13px; color: #4a5665; flex: 1; }
  .cp {
    border: 1px solid #cfe1f7; background: #fff; color: #1a6fd4;
    border-radius: 8px; padding: 4px 13px; font-size: 12.5px; cursor: pointer;
    font-family: inherit; transition: .15s;
  }
  .cp:hover { background: #eef6ff; }
  .cp.ok { background: #1a6fd4; border-color: #1a6fd4; color: #fff; }
  .cmd pre {
    margin: 0; padding: 12px 14px; font-size: 12.5px; line-height: 1.6;
    font-family: ui-monospace, Consolas, "Courier New", monospace;
    white-space: pre-wrap; word-break: break-all; color: #1b3b5f;
    background: #fbfcfe;
  }
  .hint { padding: 8px 14px 11px; font-size: 12.5px; color: #64707e; border-top: 1px dashed #eef1f6; }
  table { width: 100%; border-collapse: collapse; font-size: 13.5px; }
  th, td { text-align: left; padding: 9px 11px; border-bottom: 1px solid #eef1f6; vertical-align: top; }
  th { background: #f8fafd; font-weight: 600; color: #46525f; font-size: 13px; }
  .tbl-run td:first-child { color: #8a332a; width: 32%; }
  .cmp td:first-child { color: #52606f; width: 22%; }
  .badge-y { color: #22663c; font-weight: 700; }
  .badge-n { color: #8a332a; font-weight: 700; }
  footer { margin-top: 46px; text-align: center; color: #98a4b3; font-size: 12.5px; }
</style>
</head>
<body>
<div class="wrap">

  <header>
   
    <p>从零到「机器人在群里聊天」，照着往下做即可。全程不用写代码，命令都能直接复制粘贴。</p>
    <span class="pill">Linux 服务器　·　被 @ 回复　·　最后更新 2026-10-03</span>

    <div class="alert">
      <div class="alert-t">⚠️ 先看这条：机器人刚拉进一个新群，当天可能不理你</div>
      <p>把机器人拉进一个新群之后（比如今天新加的那个群），<b>当天 @ 它很可能一点反应都没有，后台（q.qq.com）里也还看不到这个群</b>。
      这不是机器人坏了，更不是你哪里配错了 —— <b>通常要等到第二天才会好</b>。</p>
      <ul>
        <li><b>别急着重装、也别反复改配置</b>。先等一天，第二天再去群里 @ 它一次。</li>
        <li>后台那个群列表是<b>统计数据</b>，天生有延迟（几小时到一天）。它显示什么，跟机器人能不能用<b>一点关系都没有</b>。</li>
        <li>想确认到底通没通，<b>别看后台，看机器人自己的日志</b>：在服务器上跑
          <code class="k">tail -n 20 ~/qqbot/bot.log</code>，只要看到「<b>收到来自群 xxx 的消息</b>」这一行，就是通了，后台爱显示不显示都别管。</li>
        <li>如果第二天还是没反应，再去后台的 <b>沙箱配置</b> 里把这个群加进去（见第 1.5 步）。</li>
      </ul>
    </div>
  </header>

  <h2><span class="num">图</span>整体是怎么回事</h2>
  <p class="sub">搞清楚这三段，后面就只是照做。</p>
  <div class="card">
    <div class="flow">
      <div class="fbox"><strong>① QQ 开放平台</strong>机器人在这里注册。你要从这里抄下两串密码（AppID / AppSecret），并开好群聊权限。</div>
      <div class="arrow">→</div>
      <div class="fbox"><strong>② 你的服务器</strong>我们装一个小程序，它拿着那两串密码去连 QQ 的服务器，24 小时守在那里。</div>
      <div class="arrow">→</div>
      <div class="fbox"><strong>③ 你的群</strong>机器人被拉进群以后，有人 @ 它，它就会回话。</div>
    </div>
    <div class="note blue">第 1 章在网页/手机上点，第 2 章在服务器终端里粘命令，第 3 章是以后怎么改，
      <b>第 4 章是选做的</b>：做了它就会真的跟你聊天，不做它就是背稿子的复读机。</div>
  </div>

  <h2><span class="num">1</span>在 QQ 开放平台确认 5 件事</h2>
  <p class="sub">官方后台改版比较勤，菜单名字可能略有出入，原理不变。</p>
  <div class="card">
    <h3>1.1　拿到两串密码</h3>
    <ol>
      <li>电脑浏览器打开 <code class="k">https://q.qq.com/</code>，用手机 QQ 扫码登录。</li>
      <li>进入你创建好的机器人，左侧找到 <b>开发设置</b>。</li>
      <li>抄下 <b>AppID</b>（一串纯数字）。</li>
      <li>点 <b>AppSecret</b> 旁边的「生成 / 重置」，把出现的密钥复制下来存好。</li>
    </ol>
    <div class="note red">AppSecret <b>只显示一次</b>，关掉页面就再也看不到了（只能重置）。务必先粘到记事本存好。</div>
  </div>

  <div class="card">
    <h3>1.2　确认机器人「能看到群消息」</h3>
    <p style="margin:8px 0 0">在 <b>开发设置 / 功能配置 / 权限配置</b> 里，找到和「<b>群</b>」有关的开关，全部打开（例如「群聊」「群消息」这类）。</p>
    <div class="note">这一步不做，机器人连上了也收不到群里的 @，表现为「怎么 @ 都没反应」。</div>
  </div>

  <div class="card">
    <h3>1.3　把服务器 IP 加进白名单</h3>
    <p style="margin:8px 0 0">新机器人默认开启 IP 白名单。在后台找到 <b>IP 白名单</b>，填上你服务器的<b>公网 IP</b>。</p>
    <div class="note">不知道公网 IP？在服务器终端粘下面这条，它会打印出来：</div>
<div class="cmd"><div class="bar"><span class="tag">1-3</span><span class="ttl">查服务器公网 IP</span><button class="cp" onclick="cp(this)">复制</button></div><pre>curl -s https://ipinfo.io/ip; echo</pre><div class="hint">打印出来的那串数字就是，填进后台白名单即可。</div></div>
  </div>

  <div class="card">
    <h3>1.4　把机器人拉进目标群</h3>
    <ol>
      <li>手机 QQ 打开你要用的群 → 右上角 <b>设置</b> → 找到 <b>群机器人 / 添加机器人</b>。</li>
      <li>搜索你的机器人名字，添加进群。</li>
      <li>拉进去以后，<b>当天没反应是正常的</b>，第二天再 @ 它一次（原因见顶部那条提示）。</li>
    </ol>
    <div class="note">拉机器人进群需要你是该群<b>群主或管理员</b>。<br>
      机器人<b>不挑群</b>：不需要把群号写进任何配置，拉进去、有人 @ 它就能用；想加到第二个群，重复上面三步即可。</div>
  </div>

  <div class="card">
    <h3>1.5　确认机器人是「已上线」状态</h3>
    <p style="margin:8px 0 0">后台如果你的机器人还显示「开发中 / 未上线」，先按提示提交上线。尚未上线的机器人通常只能在自己的 <b>沙箱群</b> 里被测试。</p>
    <div class="note">如果你就是想在「开发中」状态先用：把要用的群<b>群号</b>填进后台的 <b>沙箱配置</b>，然后继续第 2 步。
      注意沙箱配置生效也可能要等一阵，当天不灵别急着改。</div>
  </div>

  <h2><span class="num">2</span>在服务器上装机器人</h2>
  <p class="sub">登录你的服务器（网页终端 / 宝塔终端都行），按顺序复制粘贴。<b>每一段粘完，等屏幕上出现「ok / 就位」字样，再粘下一段。</b></p>

  <div class="card" style="padding:16px 20px">
    <div class="note blue" style="margin:0">
      下面命令里的 <code class="k">~/qqbot</code> 是机器人文件夹，会自动建在你的用户目录下，不需要改。<br>
      如果粘贴后提示 <code class="k">No such file or directory</code>，说明当前不在正确目录，先粘 <b>2-1</b> 那一段即可。
    </div>
  </div>
<div class="cmd"><div class="bar"><span class="tag">2-1</span><span class="ttl">建好机器人目录</span><button class="cp" onclick="cp(this)">复制</button></div><pre>mkdir -p ~/qqbot &amp;&amp; cd ~/qqbot &amp;&amp; echo &quot;===== 目录已就绪 =====&quot;</pre><div class="hint">粘完屏幕上出现 <b>===== 目录已就绪 =====</b> 就说明成功。</div></div>
<div class="cmd"><div class="bar"><span class="tag">2-2-1</span><span class="ttl">主程序 bot.py　第 1/4 段</span><button class="cp" onclick="cp(this)">复制</button></div><pre>printf &#x27;%s&#x27; &#x27;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&#x27; &gt;&gt; ~/qqbot/.b_bot_py.txt &amp;&amp; echo &quot;===== bot.py : 1/4 ok =====&quot;</pre><div class="hint">等出现 <b>===== bot.py : 1/4 ok =====</b> 再粘下一段。</div></div>
<div class="cmd"><div class="bar"><span class="tag">2-2-2</span><span class="ttl">主程序 bot.py　第 2/4 段</span><button class="cp" onclick="cp(this)">复制</button></div><pre>printf &#x27;%s&#x27; &#x27;+/MRubOjs/PIcdSMY/kcuIxIKqMYBulSwU10f6emTKmdIRUEe2gIvSiE2okR9LsQ6wdWqxsD1UcrwAWLvCwkoSukq9JqD5FlLaeZsiwaaqYnSvYYpq4qWYPDxR98EePDQAh/8iCc1TVT5cv963ryOkwmWi4AwXuPP6beFxygCM0YhymFvevJFI1eMfhKPZdSCybpoB9gpI1ACyA3j2YGA+n6PyL49xAVQYrAYooFGdydyCkKYOpBF1lQcyK6S/S3YGdqjiWvcYEmrzDSXezpUXUc2u9RAuEKWEnniybAQMXBAVlmQ7IcJT0Nc1Vdr58LQ765zTnjHO0iLXU/hKVLDeOM+0xeScsYwhzutR43JKjnNMM0RIx9vs1q2IizmtnLZIQz0R+FyEiC4E96GjcCUo2inqOhP4a0iD6h7LyNBZC3KQqJ2tJ9a3IoSXxxGHzLBst+7duYwVqXB+yRQXCoTBTW/KXqxBWBIeIEgM1zdVD+oTKBpML0oYHZs+/ILOUwXcwWxBTsJq4xiroqK0ZK0+KfKxlDjYIBpNWcGW8L32sEqvo2vI7/ytZta2k6IAYnhZ9BGiXOINhWWjbVcybNbkTcaW/rc3mzfvt9E3zyEoSdZINr3kMROMyeGNImSugAtIL4axrvUeJjjOVDouedQRWs8eu+7J7WDfiShYvq0+na8+eY2xMsOeZGoMarrPVjaTc4un37nrV2H0K+l760CwTS2+riKLyubpYwwry6a60tQ2Dl1dzYhj02iFg4BUzNlLNg2XWyZ5md5Bc+zGsm6x5NN9CVwJSYUchosPnfQsqZaE0GBMYB0dnNQGUpLbGsYqZ6RV34u5g41PLfSss/k/yzteXPcvL7/dH9B85L3xp72uGf+G3nXunfYEMpYBdVlii5NMnGTmGCLe6XwIjPqroooTMXXaFhcpI28H/YBPyAXA+fGvXKgdQWsE6K07/NPJV19plPqxOvkw5LBOJLXUbkB0aTbdfcYcdYmcWqq8rmNLgPTDjcnJx6lBdQCOGo396wUKSzaJlYguIJZmxvTNeW563SpqsKocSycoCSmoqdUmFzKSQhQDydxEnnDsTvuwFDXZ3Hikdrc8pa2QRa7IGXzQo+h7oUqIYvKLCxXiV3Sk3DG+qo/GoGmidyepVCQUvj5gqSa8I7hI1Ugq9IAlwtVygCiNrKS26PlD6atK9A6g1JJcsDwY3D5tTK99GpBR2F31kc/5y2NUIDBusCMLeAvRqOaWS7VIKAgdlgMJnASAyu0BR9od0TSJdebCYPg8n1fQTClzSTiFua//+IwQX/+0XBR325rC+sNoSw418midW/ZI8uWy+fsjiGJPlMiybyw6DWENZBj60ro6DHHoHcpFLcNHJ5PStjZ0EMpunk4/bWA6D0rfzzYxAfH4jB5/bFcnXjLprPwASbQ2PBqDUxAJVKbesayJyWA46toDcWTTRQwduFGNqtklJFgQVeoV3wjcUaRpALNhbumr9NgyNuOy+1u0/ohc2As882+FFateB3iMNZjeqTKXpuWooGBtokF1wvOUjaPkSeYNlBcuDPzUE7MWV3a1u6Hf8TyG4iUoSBZCNrnDLEtGoqWoZlOg3R2d8aoY1MKuqEePhw+9GjUcI8MdAci8WSvJSg0FDlsEHGKi+2DOqv7Ws3oVqt3XtkbZWrUwtY486NADj4HypKgDd2FwoyDs/ZTJanJxj8biXtfQnPi7DT0xi/RAATxeUSLmNkEhV4Rvg7pUwI7j1SpoyWU7EoZDkT/Sb+prQxZAfq88b3ZhHrOS1KacQ8QM0Vs6quQF1J6YyS/T650Ulx+tHgx7jg6RQAyecoummg3ERhlz+BoM4onzO1HHdDrCqCyS54mjSh+iIJfiwZmrPCVIn8hbQFYQKjMQhUai4tipwpSdoZKyqS54MoYMjSAhih2jWoJf1uZCB0dwnsC8O2380JpYCH3HnvQsvHQ0dCSkfayaUFPYQ62QDlAU1zotupTL5byRCnh+LY&#x27; &gt;&gt; ~/qqbot/.b_bot_py.txt &amp;&amp; echo &quot;===== bot.py : 2/4 ok =====&quot;</pre><div class="hint">等出现 <b>===== bot.py : 2/4 ok =====</b> 再粘下一段。</div></div>
<div class="cmd"><div class="bar"><span class="tag">2-2-3</span><span class="ttl">主程序 bot.py　第 3/4 段</span><button class="cp" onclick="cp(this)">复制</button></div><pre>printf &#x27;%s&#x27; &#x27;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&#x27; &gt;&gt; ~/qqbot/.b_bot_py.txt &amp;&amp; echo &quot;===== bot.py : 3/4 ok =====&quot;</pre><div class="hint">等出现 <b>===== bot.py : 3/4 ok =====</b> 再粘下一段。</div></div>
<div class="cmd"><div class="bar"><span class="tag">2-2-4</span><span class="ttl">主程序 bot.py　第 4/4 段</span><button class="cp" onclick="cp(this)">复制</button></div><pre>printf &#x27;%s&#x27; &#x27;tO2nfnAF9HLkdeCmOnsXHRO4T3q1xV10hjWMjWK3qAt/+eSDf0/8/WByz0F67uB6nBivAep61X7UHwLqK8/wViF1MpWNUuXVwDtmu1i2uBUYSyBgIjtX4xREyZmdQguHEDiP81P3R6BufBJLEJqMNc8NGA0O2zJeKsNSkztmPi427LXfaOJhbirasARyDlZetoa/8wFqttxQz8T3N77imxVHoQTfhtsk27EkAc3wwt2ZRPsfW5O4cWdYZ0YQq7+sS4K0Mwx6y5nDQPyJ9o9ak95pxbc5VCwSaDW9R4bFDlZpezlJ/KlUXST11CcQOFGJAulm7X9WsUFJb8Rij8afNnKnfya0ZBbwWuvMpbflO3glmOq6ffEZCBAjLr0YAFbvlQ0RP9Qz/kNu322+ICJ+nwy0r8Bz6l60HM6JFCXBrkSANnpXHC1/YMYGT3phCN3rwCQEcWtrmlVL8LWy8dh/L9CaWAySCugck3LMtiEiquEdBZ8d+qK5FKlvmp+RyEGyv7W+vYE+CfQPXyS9Nb0avb/gCAYjcKhgEr5WuZNiYiD+XtDzGdotM/oMyHEFdvuW9jba6+4FnE82gIiBNmP4RTISLe5N0vYQbE6k9jAWDVUP4jtz3ieORjeUM1yH6NRZ+EWGLFcMb0NCEs572t6d0gYrc2DxRnfz890EmEXtxWVMlYVwLWM1KIsmoE2g/tb8w8qry0y/8KLo6D02AfJgPHFdmYLft5t3hd9i+ngdNsTuf4vuMdmK+FEXzuq0G2aEGz8aD2S4UJxefMYuimF/d47+kQBlGkM+ZRq5Z5MfzwVY5wYAKNAE+EXiUB3IGYl2/j5J9hLhX6X78Ouz097T2GhvtAR3Qk49K3PjoR97SSKAaGc1jTaZqxiGhi18M7gA6PUt8cyIm22i9zTmlA5JAUOqPykEUIzLT7CVqaWyqtmbT3vdhAC3nuyKtFbYqQFQDFQTCu26x7JqtlvVebhmmvGODc8GhM5pWVgiwCBHcVFj2PLaJnWtEQOTL9xl06emZ3u1jErvTbzDXVfIltl5Df2biZj7AONi43VdM59W+mgddRato4eeRAq7/9ayO9uyOy00LujNNs4+3L77aMhUVsv5bHPHOq2+R6GyJoXXtpEaefWiF+NjL6Yc8L8ZOpMep34QRxYAB66jN4lzZjjg0FPUQH2EXTIlnUb/LDXDiP4FBNEcRUNXiTVHhrfwdjhte2KDlvYo2B9uBdIu6beRHqo5wdSYOpp3TYubpsi0ivNlwIGctSkY6R2lBRUl7ROzv0TzctreLFMgKRzQO4Sj5jj9f/XWPEbV2fJpqtanHYVDxTjtv6JA1Vfa+XZ6EyqD1FU2NrCPvfmDtbbWnLpgvmFkVLUg7j/gXMbJKpp7Ru+79e5e+wvcKGRn1nRPMYqxA5kj7LtYKHZntJSjNoav5ZqiPWZY4B7lcBhx/hklmiEbSi7dnT8X787nM+51OTYGnpXdEeKsOe30pZ8hY69t3cG/ijtxAm/uYGMRU5iSvbRgja9Atc3+SsTq/6m6+KPXW2QkxfQiRGu8cBj3bh5GCbtxF/fdvUNp4W0FGY97ZJnEITLIMspOlgUmPCbIyP8Co/bqJsk6AAA=&#x27; &gt;&gt; ~/qqbot/.b_bot_py.txt &amp;&amp; echo &quot;===== bot.py : 4/4 ok =====&quot;</pre><div class="hint">等出现 <b>===== bot.py : 4/4 ok =====</b> 再粘下一段。</div></div>
<div class="cmd"><div class="bar"><span class="tag">2-3-1</span><span class="ttl">安装脚本 install.sh　第 1/1 段</span><button class="cp" onclick="cp(this)">复制</button></div><pre>printf &#x27;%s&#x27; &#x27;H4sIAK0BwWoC/61WW1MTSRR+n1/RjJZA7c6E4MuWGKpU3C1qH0RZtawUD8NMA1NMZoaZjpotH1h3uRMTt+QmsC5CkHWXxAurEBP4MZvuhCf/wp6eSSBELmKZqmSS9Ok+3znn+87pM3WBbt0MdCtun3AGXb+O2EKWzq0VstnC5uDukzRNj5WWhz7mnpZGXtLxNfhOU3nUESN9lokK24ulf6fRN4i9XaPDkzQ3CLu5YTLDFuJ0fAmOLD5ZY2+n4ADuAummSxTDkMGbiwmSooLQ1n4jJJ5tUDUEn5rumEoEw9cmsVFE584h+57WKAreKliK6MEDhO/rBAUFAat9FhJDn/USy9boQIzID6+4NkGziX2T4nya5jlmz+UX+REr8FpbW1E4GDjfhdjyIHuWKudOFDrueGFbkYhiaki6i2xv4Txqbg1o+G7AjBoGj5Y4UQwZ0HtQGEk/Qxo67oioqwWRPmwKCFUwI8TeLLGxbTr6qnLSx9wkW1+mC2t+7SqlHKUrL4rZVRSUmhEdHd79/dnH3JgsyyKcBl6qECk2kXqhTFWAmlvPBfd8oz2LqK0pBCMpVmtbieCAdZkF3LwSdPkp2bp9zBHYOAhQM3uOAcdXv5qrWDRyjCu++sWuenT4OCUdYM/JjAjTldeljVQXp0bp1/whEv5v8GEp856Nj5d25mgiVcosstGXdH6bJh4XP8wV8n8Wn/5Gx/9iYxNgyQlS1h6433dTyO+AyrlcAIjgw5FuCXtKqBJCMxeCT8T9RuN3kYEBqdsidgwI6rFzn5uglfaOzhtXQmIfIbZ7IRCwY7Yuk6ipyMTVzd6+qCJjLSqrZsDVI7aBRcHqDzXxDJXRRBAvwV6Fbno/JZ0ve0eLqNXrLwEZFmTD6hWrKowutCA/30edVsFec+QxZ0IqAWJQwIaLD6o4/hw6b/FFnE1v0VxidyReykztq/N0CCSp28FKv+TGXIIjkq2o/Uovdk9CVsbmMbNCNPGs1S+iuhASg4eTjQ7HATtNzwJwlk2eGvhxmDw8LaeCs8d9n15cActDhc1x4DGbSdGdGbYwSJOPUHMTKi1N0tWHhc0JoDBHSxQdoMHCp4D2pHjAly8hOHx38TkdHqLprS9QUfjajxWwvkBoepKNJsXDdOSPEn9ssemRwod3bDZDk6uwBbRdHhZ1SOophwAZlu3YyU2iPD98cxgfEBgdGmWTYwAdBjwE6XsrvpkFV58EA27rKoVWkQhStByCFJe0wFu2FcfFDZaNzYb6KlT132JTtTSQcag+Snqk7+obZSCt1tAIF4Dj8PrbkZ/wwmac52tqw0cN7GPTrwAmv8X8Ev9MpB4RT3TKfWZydCgFPgvZYd/hV6p/uZgwtTc3D618+Lx3lTjivsV756NXMPGhajwjyQw0fK+DqgqMcRTARA34zUArPwMDAzyRLnbu6ipGFy923rpy9dr3QvimqZMuoQ27qqPbRLfMENycfnCsqI0uW0S41EOwEzIxuWc5/ZJlGrqJZaI4MN+F24pJ3CPWhHCn76pL+Clm45DfsIXbYAkUaNMdrBLLiYU4Q4Sr97HaCRtJCEqFqkgj3MCu979i3FNibuVnJ1ZDwSbw0e43mC4PCtYux0KRqEF0KQpxVpCUAxX8PKjEQJqCI5YpOdiwFO3IgV1bMi/zfuHo+zd0eM6TYE3tTntLrW4BnGE7s/R92m9ZQGm2noJeRZf+piPrLJ4Wa5x5Ham0k4TGBl0NSAnTnS0u0cf5wocVYA19MbE7FC/m017Dq93LXzXp/tSIJZLFlSzsB42VNjbQJdtub0MB/oQiOHDJYzPv6OsE3ZriMsk9ZbPbsIGuzxT/WYWADroDwIBwNuMTH9QCFn6PKc5vsEcp6EB0/o9SfpXG39JExlPR6fL6P/r4q4voDAAA&#x27; &gt;&gt; ~/qqbot/.b_install_sh.txt &amp;&amp; echo &quot;===== install.sh : 1/1 ok =====&quot;</pre><div class="hint">等出现 <b>===== install.sh : 1/1 ok =====</b> 再粘下一段。</div></div>
<div class="cmd"><div class="bar"><span class="tag">2-4-1</span><span class="ttl">定时发言清单 messages.txt　第 1/1 段</span><button class="cp" onclick="cp(this)">复制</button></div><pre>printf &#x27;%s&#x27; &#x27;H4sIAK0BwWoC/02RW27aQBSG31nFSGyApH2osjoXijG+YEIhgFsEicCBtNiuQKltHNhLO2c8fmIL+cfOTZoXz/yX7xzXGQWeGD+Sey3Xmojb5Ixq9VqdidDlsSZv7dz7JhYZZa6YhOfMYwzqYrxnpLcpSKB8vcmHa3b5mVHkqjzj8ZzZ/GiR32SNL1efGh+UNLArN0+syogqHj/kmxRVhTekTCvl/LBidYYvWu7BARpAyHAvJj2VHjs88+TdL8BTJ6XeoSIfJhTY/DSj7YSiPzBBK36mNF3zNOWxhTIy9GIwl50HMtf5cC5GRpUHlKLjUD/8rzXLsH/69+owGIvZHY+XFUW+TDEdZKK1k8GGghY//H6LEqYJWeHfgFpNYCxEr0vOjtzwPbIswG4aDexlw2OTVk90rSn7TQSj4lxu1PT3Fo18iC9KMUhyd/uySiNS5AcTSp7M5fGHtPxSDDnpDpkLxIjZrdrEaSoWf0mfnjODx0fgw0p9G5fS/0pto8L8AH7OuvjlqvhSFaOsWG3zZsJTHVYZRHQcK2icfgtPtWdNpVIWTwIAAA==&#x27; &gt;&gt; ~/qqbot/.b_messages_txt.txt &amp;&amp; echo &quot;===== messages.txt : 1/1 ok =====&quot;</pre><div class="hint">等出现 <b>===== messages.txt : 1/1 ok =====</b> 再粘下一段。</div></div>
<div class="cmd"><div class="bar"><span class="tag">2-5</span><span class="ttl">把分段拼回真正的文件（会自动备份旧程序）</span><button class="cp" onclick="cp(this)">复制</button></div><pre>cd ~/qqbot &amp;&amp; [ -f bot.py ] &amp;&amp; cp -f bot.py &quot;bot.py.bak.$(date +%m%d-%H%M%S)&quot; ; base64 -d .b_bot_py.txt | gunzip &gt; bot.py &amp;&amp; rm -f .b_bot_py.txt &amp;&amp; base64 -d .b_install_sh.txt | gunzip &gt; install.sh &amp;&amp; rm -f .b_install_sh.txt &amp;&amp; base64 -d .b_messages_txt.txt | gunzip &gt; messages.txt &amp;&amp; rm -f .b_messages_txt.txt &amp;&amp; python3 -c &quot;import ast;ast.parse(open(&#x27;bot.py&#x27;,encoding=&#x27;utf-8&#x27;).read());print(&#x27;===== 程序检查通过 =====&#x27;)&quot; &amp;&amp; ls -l bot.py install.sh messages.txt &amp;&amp; echo &quot;===== 3 个文件已就位 =====&quot;</pre><div class="hint">看到 3 个文件名、<b>===== 程序检查通过 =====</b> 和 <b>===== 3 个文件已就位 =====</b> 才算好。<br>这条会顺手把机器上的旧程序另存成 <code class="k">bot.py.bak.日期时间</code>，出问题能退回去。</div></div>
<div class="cmd"><div class="bar"><span class="tag">2-6</span><span class="ttl">自动安装依赖（约 1 分钟）</span><button class="cp" onclick="cp(this)">复制</button></div><pre>cd ~/qqbot &amp;&amp; bash install.sh</pre><div class="hint">最后一行出现 <b>安装完成，还差最后一步</b> 就对了。如果看到 <b>[失败]</b>，把屏幕内容截图发给你的助手。</div></div>
<div class="cmd"><div class="bar"><span class="tag">2-7</span><span class="ttl">第一次运行，填凭据</span><button class="cp" onclick="cp(this)">复制</button></div><pre>cd ~/qqbot &amp;&amp; python3 bot.py</pre><div class="hint">1. 提示 <b>请粘贴 AppID</b> 时，粘贴后按回车；<br>2. 提示 <b>请粘贴 AppSecret</b> 时同理。<br><i>注意：粘贴时屏幕上看不到任何字符，这是正常的，不要以为没粘上。</i><br>3. 出现 <b>[OK] 机器人已连上 QQ</b> 后，<b>去 QQ 群里 @ 一下机器人</b>；<br>4. 看到 <b>[配置完成]</b> 就按 <b>Ctrl + C</b> 退出。</div></div>
<div class="cmd"><div class="bar"><span class="tag">2-8</span><span class="ttl">让机器人后台常驻 + 开机自启</span><button class="cp" onclick="cp(this)">复制</button></div><pre>cd ~/qqbot &amp;&amp; systemctl daemon-reload &amp;&amp; systemctl enable --now qqbot &amp;&amp; sleep 4 &amp;&amp; systemctl is-active qqbot</pre><div class="hint">最后一行显示 <b>active</b> 就表示机器人已经在后台跑着了。</div></div>
<div class="cmd"><div class="bar"><span class="tag">2-9</span><span class="ttl">查看运行日志</span><button class="cp" onclick="cp(this)">复制</button></div><pre>tail -n 25 ~/qqbot/bot.log</pre><div class="hint">能看到 <b>机器人已连上 QQ</b> 就是一切正常。这里也是判断「新群通没通」最靠谱的地方。</div></div>

  <h2><span class="num">3</span>以后怎么用 / 怎么改</h2>
  <p class="sub">改内容都不用重启，机器人每次收到消息都会重新读一遍文件。</p>

  <div class="note red">
    ⚠️ <b>关于「到点自动发言」，先把话说清楚</b>：QQ 官方<b>基本关闭了群聊的主动消息权限</b>，
    也就是「没人理它、它自己开口」这件事，现在<b>多半发不出去</b>，日志里会写
    <code class="k">主动消息发送失败，无权限</code>。<br>
    这<b>不是</b>你哪里配错了，也<b>不是</b>脚本的问题，是平台限制。下面这条命令本身是对的，
    留着不影响任何事，哪天官方放开了就会自动生效。<br>
    真的需要「定时推送」，目前唯一合规的路子是把机器人改成 <b>QQ 频道</b>机器人（那是频道，不是群）。
  </div>
<div class="cmd"><div class="bar"><span class="tag">3-1</span><span class="ttl">加一条定时发言</span><button class="cp" onclick="cp(this)">复制</button></div><pre>echo &quot;08:00 早上好呀&quot; &gt;&gt; ~/qqbot/messages.txt &amp;&amp; echo 已添加</pre><div class="hint">把 <b>08:00</b> 和后面的文字换成你想要的即可，格式就是「时间 空格 内容」。加完不用重启。</div></div>
<div class="cmd"><div class="bar"><span class="tag">3-2</span><span class="ttl">改「没接 AI 时被 @ 的回复」</span><button class="cp" onclick="cp(this)">复制</button></div><pre>echo &quot;你好，我是群里的助手&quot; &gt; ~/qqbot/reply.txt &amp;&amp; echo 已改好</pre><div class="hint">引号里的字换成你想让机器人说的话。改完不用重启。<br>（<b>接了 AI 之后这条就不起作用了</b>——只有在没配 Key、或者调 AI 失败时才会退回这句。）</div></div>
<div class="cmd"><div class="bar"><span class="tag">3-3</span><span class="ttl">重启机器人</span><button class="cp" onclick="cp(this)">复制</button></div><pre>systemctl restart qqbot &amp;&amp; sleep 4 &amp;&amp; systemctl is-active qqbot</pre><div class="hint">显示 <b>active</b> 即正常。<br>唯一需要重启的情况：改了程序本身（<code class="k">bot.py</code>）。<br>重启会清空它记住的对话（记忆只存在内存里）。</div></div>
<div class="cmd"><div class="bar"><span class="tag">3-4</span><span class="ttl">临时停止</span><button class="cp" onclick="cp(this)">复制</button></div><pre>systemctl stop qqbot &amp;&amp; echo 已停止</pre><div class="hint">开机仍会自动启动。想再开：<code class="k">systemctl start qqbot</code></div></div>
<div class="cmd"><div class="bar"><span class="tag">3-5</span><span class="ttl">（建议先做）把服务器时区改成北京时间</span><button class="cp" onclick="cp(this)">复制</button></div><pre>timedatectl set-timezone Asia/Shanghai &amp;&amp; date &amp;&amp; echo 时区已改为北京时间</pre><div class="hint">定时发言是按服务器时间算的。如果这里显示的不是 <b>CST +0800</b>，定时就会对不上。粘这一条即可修好。</div></div>

  <h2><span class="num adv">4</span>进阶：让它真的会聊天（接入 AI）</h2>
  <p class="sub">选做章节。不做，机器人被 @ 时只会回一句写死的话；做了，它就能读懂你的问题、自己组织语言回答。</p>

  <div class="card" style="padding:6px 0">
    <table class="cmp">
      <tr><th></th><th>不做本章（复读机）</th><th>做完本章（接 AI）</th></tr>
      <tr>
        <td>群里 @ 它</td>
        <td><span class="badge-n">回一句写死的话</span><br>不管问什么都一样</td>
        <td><span class="badge-y">真的读懂你的问题</span><br>自己组织语言回答</td>
      </tr>
      <tr>
        <td>能不能接着聊</td>
        <td>不能，每次都当第一次</td>
        <td>记得你最近 3 轮对话（不同人的记忆互相独立）</td>
      </tr>
      <tr>
        <td>花钱吗</td>
        <td>不花</td>
        <td>按用量付费，群里日常问答一般<b>一个月几毛到几块钱</b></td>
      </tr>
    </table>
    <div class="note green" style="margin:16px 22px 18px">
      重要：<b>没填 Key 之前，机器人现在的行为跟平时完全一样</b>（自动退回那句固定话）。
      所以配 AI 这一步<b>没有任何风险</b>，你随时可以把 Key 摘掉变回复读机。
    </div>
  </div>

  <div class="card">
    <h3>4.0　先花 5 秒确认你的程序是哪个版本</h3>
    <p style="margin:8px 0 0">粘下面这条，它会直接告诉你答案（只是读一下文件，不改任何东西）：</p>
  </div>
<div class="cmd"><div class="bar"><span class="tag">4-0</span><span class="ttl">看看机器人程序支不支持 AI</span><button class="cp" onclick="cp(this)">复制</button></div><pre>cd ~/qqbot &amp;&amp; if grep -qE &quot;enable_search|dashscope&quot; bot.py; then echo &quot;当前状态：联网搜索版（请回第 2 章把 2-2 ~ 2-5 再做一遍换成最新版）&quot;; elif grep -q &quot;api.deepseek.com&quot; bot.py; then echo &quot;当前状态：最新版，支持 AI 聊天（直接往下做 4.2）&quot;; else echo &quot;当前状态：老版本，不支持 AI（请回第 2 章把 2-2 ~ 2-5 再做一遍）&quot;; fi</pre><div class="hint">只要不是显示「<b>最新版，支持 AI 聊天</b>」，就回到第 2 章，从 <b>2-2</b> 开始把 2-2 ~ 2-5 重做一遍（会覆盖成最新版，并自动把旧的另存备份），然后继续 4.2。<br><b>刚按第 2 章装完的，一定是最新版</b>，直接往下走。</div></div>

  <div class="card">
    <h3>4.1　申请一个 DeepSeek 的 Key</h3>
    <ol>
      <li>电脑浏览器打开 <code class="k">https://platform.deepseek.com</code>，登录（就是你在网页上跟 DeepSeek 聊天那个账号，不用另外注册）。</li>
      <li>左侧找到 <b>充值</b>（或「账户余额」），充 <b>10 元</b>先试试——够聊很久了。</li>
      <li>左侧点 <b>API keys</b> → <b>创建 API key</b>，随便起个名字，比如 <code class="k">qqbot</code>。</li>
      <li>把生成的那串密钥（<b>sk-</b> 开头）复制下来，下一步要粘。</li>
    </ol>
    <div class="note red">这串 Key <b>只在创建时完整显示一次</b>，关掉窗口就看不到了（只能重新创建）。先粘到记事本存好。</div>
  </div>

  <p class="sech">4.2　把 Key 交给机器人</p>
<div class="cmd"><div class="bar"><span class="tag">4-2-1</span><span class="ttl">把 Key 交给机器人</span><button class="cp" onclick="cp(this)">复制</button></div><pre>read -p &quot;把 Key 粘进来再按回车：&quot; K &amp;&amp; echo &quot;$K&quot; &gt; ~/qqbot/ai_key.txt &amp;&amp; echo &quot;===== 已保存 =====&quot; &amp;&amp; echo &quot;开头几位是：&quot; &amp;&amp; cut -c1-8 ~/qqbot/ai_key.txt</pre><div class="hint">粘这条以后，终端会停下等你。这时把复制好的 Key <b>粘贴进去按回车</b>。<br>最后会打印 Key 的开头 8 位，确认是 <b>sk-</b> 开头就对了。<br><b>不用重启</b>，机器人收到下一条消息时就会自动读到。<br>以后想换一个新 Key，把这条重跑一遍就行。</div></div>
<div class="cmd"><div class="bar"><span class="tag">4-2-2</span><span class="ttl">想再确认一遍 Key 存对没有</span><button class="cp" onclick="cp(this)">复制</button></div><pre>cut -c1-10 ~/qqbot/ai_key.txt; echo</pre><div class="hint">只显示前 10 位，够确认就行，不会把整串 Key 暴露在屏幕上。</div></div>

  <div class="card">
    <h3>4.3　测试一下</h3>
    <p style="margin:0 0 6px">去 QQ 群里 @ 机器人，问它一个真正的问题，比如：</p>
    <p style="margin:0 0 0; padding:12px 16px; background:#f7fafd; border:1px solid #e0eaf5; border-radius:10px; color:#1a518d">
      @我的机器人 用一句话解释什么是量子纠缠
    </p>
    <div class="note blue">第一次回答可能要等 5～10 秒（它真的在想）。等太久的容忍上限是 60 秒，超了它会说「想太久了」。</div>
    <div class="note">如果它回的<b>还是那句固定话</b>，说明 Key 没读到 —— 检查 4-2-2 打印出来的是不是以 <code class="k">sk-</code> 开头，再往下看排错表。</div>
  </div>

  <p class="sech">4.4　平时还能怎么调</p>
<div class="cmd"><div class="bar"><span class="tag">4-4-1</span><span class="ttl">改机器人的性格 / 说话风格</span><button class="cp" onclick="cp(this)">复制</button></div><pre>read -p &quot;输入想让机器人扮演的角色，回车确认：&quot; P &amp;&amp; echo &quot;$P&quot; &gt; ~/qqbot/persona.txt &amp;&amp; echo &quot;===== 人设已更新 =====&quot;</pre><div class="hint">比如你输入 <b>你是群里的大管家，说话幽默，喜欢用成语</b>，它以后就按这个人设回答。<br>也可以用来限制长度，比如加一句 <b>回答不超过 80 字</b>。不用重启，下一条消息即生效。</div></div>
<div class="cmd"><div class="bar"><span class="tag">4-4-2</span><span class="ttl">让机器人「忘掉刚才聊的」（在 QQ 里发，不是在服务器上跑）</span><button class="cp" onclick="cp(this)">复制</button></div><pre>@我的机器人 重置</pre><div class="hint">在群里 @ 机器人 并说 <b>重置</b>，它就会清空和你这段对话的记忆，重新开始。<br>机器人会记住<b>每个人的最近 3 轮对话</b>，不同人的记忆互相独立，不会串味。</div></div>

  <div class="card">
    <h3>4.5　关于花钱，说个大实话</h3>
    <p style="margin:8px 0 0">
      DeepSeek 是<b>按实际用量计费</b>的，用多少扣多少，不用不扣。群里偶尔问几句，
      一个月通常也就几毛到几块钱。真正会烧钱的情况只有一种：<b>群里有人不停刷它</b>。
      真遇到了，告诉你的助手，可以加一条「每人每分钟最多问一次」的限制。
    </p>
  </div>

  <h2><span class="num gray">?</span>出问题看这里</h2>
  <p class="sub">先对照现象找原因，找不到就把屏幕截图发给你的助手，不要自己乱试。</p>

  <div class="card" style="padding:6px 0">
    <table class="tbl-run">
      <tr><th style="width:32%">你看到的现象</th><th style="width:34%">多半是</th><th>怎么办</th></tr>
      <tr>
        <td>刚拉进一个新群，@ 它没反应，后台也看不到这个群</td>
        <td><b>正常现象</b>：新群当天多半还没生效</td>
        <td><b>等一天</b>再 @ 一次（见手册最上面那条）。第二天还不行，去后台 <b>沙箱配置</b> 加上群号</td>
      </tr>
      <tr>
        <td>跑 2-7 时一直卡着，不出现「机器人已连上 QQ」</td>
        <td>AppID 或 AppSecret 不对／多了空格</td>
        <td>删掉配置重来：<code class="k">rm -f ~/qqbot/config.json</code>，再跑一次 2-7</td>
      </tr>
      <tr>
        <td>说「已连上 QQ」，但在老群里 @ 它也没反应</td>
        <td>第 1.2 步的群权限没开；或机器人还没上线，只有沙箱群收得到</td>
        <td>回后台确认群权限（1.2）；再确认这个群是不是沙箱群里配过的那个（1.5）</td>
      </tr>
      <tr>
        <td>日志里出现 <code class="k">[定时发送失败]</code> 或 <code class="k">主动消息发送失败，无权限</code></td>
        <td><b>平台限制</b>：QQ 官方基本关闭了群聊主动消息权限</td>
        <td>不是你的问题，脚本也没错（见第 3 章开头的说明）。要定时推送只能改用 QQ 频道</td>
      </tr>
      <tr>
        <td>到点了，但时间对不上（早/晚几小时）</td>
        <td>服务器用的是 UTC 时间，不是北京时间</td>
        <td>粘第 <b>3-5</b> 条命令改成北京时间</td>
      </tr>
      <tr>
        <td>2-6 提示 <code class="k">[失败]</code></td>
        <td>依赖没装上（网络／Python 版本问题）</td>
        <td>把屏幕上最后 20 行截图发给助手</td>
      </tr>
      <tr>
        <td>程序被改坏了／想退回旧程序</td>
        <td>2-5 每次都会自动备份旧程序</td>
        <td>看目录里 <code class="k">bot.py.bak.日期时间</code>，用最新那个换回来：<br>
          <code class="k">cd ~/qqbot && cp -f "$(ls -t bot.py.bak.* | head -1)" bot.py && systemctl restart qqbot && systemctl is-active qqbot</code></td>
      </tr>
    </table>
  </div>

  <div class="card" style="padding:6px 0">
    <table class="tbl-run">
      <tr><th style="width:32%">现象（接了 AI 之后）</th><th style="width:34%">多半是</th><th>怎么办</th></tr>
      <tr>
        <td>它还是回那句固定话</td>
        <td>Key 没读到，或文件里混进了空格/换行</td>
        <td>跑 <code class="k">cut -c1-8 ~/qqbot/ai_key.txt; echo</code>，看到的应该以 <b>sk-</b> 开头</td>
      </tr>
      <tr>
        <td>群里显示「收到，我在呢～」而不是回答</td>
        <td>调 AI 失败了，程序自动回退（这是保护机制）</td>
        <td>跑 <code class="k">tail -n 30 ~/qqbot/bot.log</code> 看 <b>[AI 失败]</b> 后面写了什么</td>
      </tr>
      <tr>
        <td>日志里写 <code class="k">HTTP 401</code></td>
        <td>Key 填错了 / 已被删除</td>
        <td>重新去 platform.deepseek.com 建一个 Key，重跑 4-2-1</td>
      </tr>
      <tr>
        <td>日志里写 <code class="k">HTTP 402</code> 或提到 balance</td>
        <td>账户没余额了</td>
        <td>去 platform.deepseek.com 充值</td>
      </tr>
      <tr>
        <td>日志里写 <code class="k">HTTP 429</code></td>
        <td>请求太频繁</td>
        <td>等一分钟再试，不用改任何东西</td>
      </tr>
      <tr>
        <td>回答太长被切掉</td>
        <td>群里单条消息有长度上限，程序自动截断在 500 字</td>
        <td>正常现象。想让它更短，用 4-4-1 改人设，加一句「回答不超过 80 字」</td>
      </tr>
      <tr>
        <td>重启后它把刚才聊的忘了</td>
        <td>对话记忆只存在内存里</td>
        <td>正常现象。群里发「重置」也能手动清</td>
      </tr>
      <tr>
        <td>它说「这个问题我想太久了」</td>
        <td>等 AI 回答超过 60 秒，程序主动放弃</td>
        <td>再问一次，或者把问题问短一点</td>
      </tr>
    </table>
  </div>

  <h2><span class="num gray">×</span>不想要了 / 想改回去</h2>
<div class="cmd"><div class="bar"><span class="tag">X1</span><span class="ttl">暂时关掉 AI（Key 留着，随时能开回来）</span><button class="cp" onclick="cp(this)">复制</button></div><pre>mv ~/qqbot/ai_key.txt ~/qqbot/ai_key.txt.off &amp;&amp; echo &quot;===== AI 已关闭，机器人变回复读机 =====&quot;</pre><div class="hint">不用重启，下一条消息立刻生效。<br>想再打开：<code class="k">mv ~/qqbot/ai_key.txt.off ~/qqbot/ai_key.txt</code>（Key 不用重新申请）</div></div>
<div class="cmd"><div class="bar"><span class="tag">X2</span><span class="ttl">一键卸载（机器人不想用了再执行）</span><button class="cp" onclick="cp(this)">复制</button></div><pre>systemctl disable --now qqbot; rm -f /etc/systemd/system/qqbot.service; systemctl daemon-reload; rm -rf ~/qqbot; echo &quot;===== 已彻底删除 =====&quot;</pre><div class="hint">会停止服务、删掉开机自启、删掉整个 <b>~/qqbot</b> 文件夹（Key、人设、聊天记录全在里面）。</div></div>

  <footer>命令都可以直接复制粘贴，不需要理解它们。<br>中途任何地方报错，把屏幕截图发给你的助手就行。</footer>
</div>

<script>
function cp(btn) {
  var pre = btn.closest('.cmd').querySelector('pre');
  var txt = pre.innerText;
  function done() {
    btn.textContent = '已复制';
    btn.classList.add('ok');
    setTimeout(function () { btn.textContent = '复制'; btn.classList.remove('ok'); }, 1500);
  }
  function fallback() {
    var ta = document.createElement('textarea');
    ta.value = txt;
    ta.style.position = 'fixed';
    ta.style.left = '-9999px';
    document.body.appendChild(ta);
    ta.select();
    try { document.execCommand('copy'); done(); }
    catch (e) { alert('复制失败，请手动选中命令后按 Ctrl+C'); }
    document.body.removeChild(ta);
  }
  if (navigator.clipboard && navigator.clipboard.writeText) {
    navigator.clipboard.writeText(txt).then(done, fallback);
  } else { fallback(); }
}
</script>
</body>
</html>
