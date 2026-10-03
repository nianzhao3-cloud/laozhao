---
title: "QQ 群机器人 · 小号方案操作手册"
date: 2026-10-03
draft: false
tags: ["教学"]
categories: ["教学"]
summary: "用自己的小号链接机器人"
---


<meta charset="utf-8">
<title>QQ 群机器人 · 小号方案操作手册</title>
<style>
  :root{
    --bg:#f7f8fa; --panel:#fff; --line:#e5e7eb; --line2:#eef0f4;
    --text:#1f2328; --text2:#5b6472; --text3:#8a94a6;
    --blue:#2f6feb; --blue-soft:#eaf1ff;
    --green:#1a7f4b; --green-soft:#e8f7ee;
    --amber:#9a6400; --amber-soft:#fff6e0;
    --red:#c0392b; --red-soft:#fdecea;
    --code:#f6f8fa;
  }
  *{box-sizing:border-box}
  body{margin:0;background:var(--bg);color:var(--text);
    font-family:-apple-system,BlinkMacSystemFont,"Segoe UI","PingFang SC","Microsoft YaHei",sans-serif;
    font-size:15px;line-height:1.75}
  .wrap{max-width:820px;margin:0 auto;padding:36px 22px 90px}
  h1{font-size:24px;margin:0 0 8px;font-weight:700;letter-spacing:-.01em}
  .lead{color:var(--text2);margin:0 0 22px}

  .flow{display:flex;flex-wrap:wrap;gap:8px;margin:0 0 30px}
  .flow div{background:var(--panel);border:1px solid var(--line);border-radius:999px;
    padding:5px 14px;font-size:13px;color:var(--text2)}
  .flow div b{color:var(--blue)}

  h2{font-size:18px;margin:38px 0 12px;padding-bottom:9px;border-bottom:2px solid var(--line);font-weight:650}
  h2 .n{display:inline-block;width:26px;height:26px;line-height:26px;text-align:center;
    background:var(--blue);color:#fff;border-radius:7px;font-size:13.5px;margin-right:9px;vertical-align:2px}
  h3{font-size:15.5px;margin:26px 0 8px;font-weight:650;
    background:#eef2f8;border-left:3px solid var(--blue);padding:4px 10px;border-radius:0 6px 6px 0}
  h4{font-size:14.5px;margin:20px 0 6px;font-weight:650;color:var(--text2)}
  p{margin:9px 0}
  ul{margin:9px 0;padding-left:21px}li{margin:4px 0}
  code{background:var(--code);border:1px solid var(--line);border-radius:4px;padding:1px 5px;
    font-size:13px;font-family:"Cascadia Mono",Consolas,monospace;color:#b3386b}

  .box{border-radius:10px;padding:13px 16px;margin:14px 0;border:1px solid;font-size:14px}
  .box b{display:block;margin-bottom:3px}
  .t-blue{background:var(--blue-soft);border-color:#c8dcff;color:#1b3f8c}
  .t-warn{background:var(--amber-soft);border-color:#f3d99a;color:#7a5000}
  .t-red{background:var(--red-soft);border-color:#f5c2bd;color:#8f2b1f}
  .t-green{background:var(--green-soft);border-color:#b7e2c9;color:#136b3f}

  .codeblock{margin:12px 0;position:relative}
  .bar{display:flex;align-items:center;justify-content:space-between;background:#eceff4;
    border:1px solid var(--line);border-bottom:0;border-radius:9px 9px 0 0;padding:5px 12px;
    font-size:12px;color:var(--text3);font-family:Consolas,monospace}
  .codeblock pre{margin:0;background:var(--code);border:1px solid var(--line);border-radius:0 0 9px 9px;
    padding:13px 15px;overflow-x:auto;font-family:Consolas,monospace;font-size:12.5px;
    line-height:1.6;color:#24292f;max-height:520px;user-select:text}
  .codeblock pre code{background:none;border:0;padding:0;color:inherit}
  .cp{background:#fff;border:1px solid var(--line);border-radius:6px;color:var(--text2);
    font-size:11.5px;padding:2px 10px;cursor:pointer;white-space:nowrap}
  .cp:hover{background:var(--blue);color:#fff;border-color:var(--blue)}
  .cp.ok{background:var(--green);color:#fff;border-color:var(--green)}

  table{width:100%;border-collapse:collapse;font-size:13.5px;background:var(--panel);
    border:1px solid var(--line);border-radius:10px;overflow:hidden;margin:12px 0}
  th,td{padding:9px 13px;text-align:left;border-bottom:1px solid var(--line2);vertical-align:top}
  th{background:#f1f4f8;font-weight:650;color:var(--text2);font-size:12.5px}
  tr:last-child td{border-bottom:0}
  .muted{color:var(--text3);font-size:13.5px}
  h3.adv{background:#fff7e6;border-left-color:#e0a416}
  .tag{display:inline-block;background:#e0a416;color:#fff;font-size:11px;font-weight:600;
    border-radius:4px;padding:1px 7px;margin-right:7px;letter-spacing:.02em;vertical-align:1px}
  .flow div.adv{border-style:dashed;border-color:#e6c88a}
  .flow div.adv b{color:#9a6400}
</style>

<div class="wrap">


  <p class="lead">这一版的机器人<b>能在群里 @ 出回复</b>。从上往下照着做，不需要看懂代码。全程约 30 分钟（第一次拉镜像会久一点）。</p>

  <div class="flow">
    <div><b>0</b> 清空旧程序</div>
    <div><b>1</b> 装 Docker</div>
    <div><b>2</b> 换镜像源 · 启动 NapCat</div>
    <div><b>3</b> 扫码登录小号</div>
    <div><b>4</b> 配连接通道</div>
    <div><b>5</b> 装机器人程序</div>
    <div><b>6</b> 群里 @ 它</div>
    <div class="adv"><b>附录E</b> 进阶玩法（可选）</div>
  </div>

  <div class="box t-blue">
    <b>这一版和上一版的区别</b>
    上一版用的是 <strong>QQ 官方机器人</strong>，那个方案个人用户<strong>收不到群消息</strong>，只能私聊。<br>
    这一版是让一个 <strong>QQ 小号</strong>来当机器人——它就是个普通群成员，<strong>任何群都能用</strong>，也没有人数限制。<br>
    <span class="muted">上一版的《机器人对接手册.html》可以不用管了，留着也不碍事。大模型 API Key 还是同一个，继续用。</span>
  </div>

  <div class="box t-red">
    <b>用之前必须知道的（就这一条，但很重要）</b>
    这是<strong>第三方方案，不是腾讯官方的</strong>。它的代价是：<strong>违反 QQ 用户协议，有被风控、被限制登录甚至封号的风险。</strong><br>
    👉 所以：<strong>绝对不要用你的主号</strong>。去注册一个新 QQ 号专门干这个，就算哪天号没了也不影响你正常用 QQ。
  </div>

  <h3>开始前，确认这几样在手边</h3>
  <table>
    <thead><tr><th>东西</th><th>从哪来</th></tr></thead>
    <tbody>
      <tr><td>一个 <strong>QQ 小号</strong></td><td>能正常登录的 QQ 号，<strong>最好是养过一段时间的</strong>（新注册的号登录服务器容易触发验证）。要能收到这个号绑定的手机短信</td></tr>
      <tr><td>服务器的<strong>公网 IP</strong></td><td>阿里云控制台实例列表里那串 IP</td></tr>
      <tr><td>服务器的<strong>登录密码</strong></td><td>买服务器时设的，或控制台「重置密码」重设的</td></tr>
      <tr><td>大模型 <strong>API Key</strong></td><td>你之前已经申请过（智谱 / DeepSeek / 龙猫都行），继续用它</td></tr>
    </tbody>
  </table>

  <div class="box t-warn">
    <b>先看一眼黑窗口怎么开</b>
    阿里云控制台 → 你那台服务器 → 点蓝色的「<strong>远程连接</strong>」或「<strong>登录</strong>」→ 选「<strong>Workbench 密码登录</strong>」→ 输入密码。<br>
    进去后提示符应该是 <code>root@... #</code>（结尾是井号）。是井号就对了，下面的命令全都是复制粘贴。
    <br><span class="muted">如果结尾是 <code>$</code>，先输入 <code>sudo -i</code> 再回车。</span>
  </div>

  <!-- ============ 0 ============ -->
  <h2><span class="n">0</span>先清空上一版留下的东西</h2>

  <p>把下面这一整行复制粘贴进黑窗口，回车。</p>

  <div class="codeblock">
    <div class="bar"><span>0　清空旧程序</span><button class="cp">复制</button></div>
<pre><code>systemctl disable --now qqbot 2>/dev/null; docker rm -f napcat 2>/dev/null; rm -rf /opt/qqbot /opt/napcat /var/log/qqbot.log /etc/systemd/system/qqbot.service; systemctl daemon-reload; echo "===== 0 完成 ====="</code></pre>
  </div>

  <p>看到 <code>===== 0 完成 =====</code> 就行了。（如果中间冒出几行 <code>Failed to stop...</code> 之类的红字，<strong>不用管</strong>，那是上一版还没装过，属于正常）</p>

  <!-- ============ 1 ============ -->
  <h2><span class="n">1</span>装 Docker</h2>

  <p>Docker 是运行小号程序用的「盒子」。先装它。</p>

  <h3>1-1　安装</h3>
  <div class="codeblock">
    <div class="bar"><span>1-1　装 Docker</span><button class="cp">复制</button></div>
<pre><code>apt-get update &amp;&amp; apt-get install -y docker.io; systemctl enable --now docker; echo "===== 1-1 完成 ====="</code></pre>
  </div>
  <p>等它跑完（1～3 分钟）。看到 <code>===== 1-1 完成 =====</code> 就装好了。</p>

  <h3>1-2　确认装好了</h3>
  <div class="codeblock">
    <div class="bar"><span>1-2　检查</span><button class="cp">复制</button></div>
<pre><code>docker --version</code></pre>
  </div>
  <p>显示类似 <code>Docker version 24.x.x</code> 就是正常的。</p>

  <div class="box t-warn">
    <b>顺手加个「虚拟内存」（可选，但推荐）</b>
    你的服务器内存不大，小号程序（一个完整的 QQ 客户端）比较吃内存。粘这一行加 2G 虚拟内存，能明显减少卡死：<br>
    <div class="codeblock" style="margin-top:8px">
      <div class="bar"><span>1-3　加虚拟内存（可选）</span><button class="cp">复制</button></div>
<pre><code>fallocate -l 2G /swapfile; chmod 600 /swapfile; mkswap /swapfile; swapon /swapfile; echo '/swapfile none swap sw 0 0' &gt;&gt; /etc/fstab; free -h</code></pre>
    </div>
    看到 <code>Swap</code> 那一行有 2.0Gi 就成了。（只做一次，重复做会报错，报错也不用管）
  </div>

  <!-- ============ 2 ============ -->
  <h2><span class="n">2</span>启动 NapCat（小号的运行环境）</h2>

  <h3>2-1　先让服务器认得「镜像仓库」（大陆服务器必做，只做一次）</h3>

  <p>Docker 装完默认去<strong>境外仓库</strong>取文件，大陆服务器基本连不上——会卡很久，最后报 <code>i/o timeout</code>。<br>
  先把取文件的路换成国内的。粘这一行，回车：</p>

  <div class="codeblock">
    <div class="bar"><span>2-1　换成国内镜像源</span><button class="cp">复制</button></div>
<pre><code>mkdir -p /etc/docker; echo '{"registry-mirrors":["https://docker.m.daocloud.io","https://docker.nju.edu.cn","https://mirror.baidubce.com","https://hub-mirror.c.163.com"]}' &gt; /etc/docker/daemon.json; systemctl restart docker; echo "===== 2-1 完成 ====="</code></pre>
  </div>

  <p class="muted">粘完可能安静 10 秒左右（正在重启 Docker），看到 <code>===== 2-1 完成 =====</code> 就行。</p>

  <div class="box t-warn">
    <b>如果没出现「2-1 完成」，而是红字报错</b>
    多半是那一行 JSON 粘掉字符了。这一行<strong>短，直接重粘一次</strong>基本就好；
    若提示 <code>Job for docker.service failed</code>，先粘 <code>cat /etc/docker/daemon.json</code> 看看内容，截图发我。
  </div>

  <h3>2-2　拉取并启动 NapCat</h3>

  <p>把下面这一段（<strong>两行都要</strong>）整体复制粘贴进黑窗口，回车。</p>

  <div class="codeblock">
    <div class="bar"><span>2-2　启动 NapCat</span><button class="cp">复制</button></div>
<pre><code>mkdir -p /opt/napcat/config /opt/napcat/qq
docker run -d --name napcat --restart always -e NAPCAT_UID=0 -e NAPCAT_GID=0 -e WEBUI_TOKEN=qqbot-2026-secret -e TZ=Asia/Shanghai -v /opt/napcat/config:/app/napcat/config -v /opt/napcat/qq:/app/.config/QQ -v /etc/localtime:/etc/localtime:ro -p 6099:6099 -p 127.0.0.1:3001:3001 mlikiowa/napcat-docker:latest</code></pre>
  </div>

  <div class="box t-warn">
    <b>第一次会下载一个几百 MB 的文件，可能要等 2～10 分钟</b>
    屏幕上会出现不断滚动的进度信息（<code>Pulling fs layer</code>、<code>Downloading</code> 之类），<strong>这是正常的，别关窗口</strong>。
  </div>

  <h3>2-3　确认容器在跑</h3>

  <p>等它停下来、光标回到 <code>root@... #</code> 之后，粘这一行确认它跑起来了：</p>

  <div class="codeblock">
    <div class="bar"><span>2-3　确认容器在跑</span><button class="cp">复制</button></div>
<pre><code>docker ps --filter name=napcat; echo "===== 2 完成 ====="</code></pre>
  </div>

  <p>能看到一行含 <code>napcat</code> 并且状态是 <code>Up</code> 的记录，就是成功了。</p>

  <!-- ============ 3 ============ -->
  <h2><span class="n">3</span>打开管理网页，扫码登录小号</h2>

  <p>这一步开始要<strong>离开黑窗口，用浏览器操作</strong>。</p>

  <h3>3-1　先去阿里云放行 6099 端口</h3>

  <p>这一步不做，后面网页打不开。</p>

  <table>
    <thead><tr><th>你买的是哪种服务器</th><th>去哪儿点</th></tr></thead>
    <tbody>
      <tr>
        <td><strong>轻量应用服务器</strong></td>
        <td>阿里云控制台 → 你这台服务器 → 左侧「<strong>防火墙</strong>」→「添加规则」→ 应用类型选「<strong>自定义</strong>」→ 协议 <strong>TCP</strong> → 端口范围填 <strong>6099</strong> → 授权对象 <strong>0.0.0.0/0</strong> → 确定</td>
      </tr>
      <tr>
        <td><strong>ECS 云服务器</strong></td>
        <td>控制台 → 实例 → 右侧「更多」→「网络和安全组」→「<strong>安全组配置</strong>」→「配置规则」→「入方向」→「手动添加」→ 端口 <strong>6099/6099</strong>，授权对象 <strong>0.0.0.0/0</strong> → 保存</td>
      </tr>
    </tbody>
  </table>

  <div class="box t-red">
    <b>⚠️ 6099 只是「临时开一下」，做完第 4 步立刻删掉这条规则</b>
    这个管理网页<strong>权限极高</strong>——能读服务器上的任意文件、能执行任意命令。<strong>把它暴露在公网，等于把服务器钥匙挂在门口。</strong><br>
    NapCat 历史上出过严重事故：有人扫描公网上暴露的这个网页，借用别人的机器人账号在 QQ 群里发违法信息，<strong>导致一批 QQ 号和群被永久封禁</strong>。<br>
    👉 所以：<strong>扫完码（第 3 步）、配好连接通道（第 4 步）之后，马上回阿里云把 6099 这条规则删掉。</strong>
    删了机器人照常运行，以后要再进网页把规则加回来即可。
  </div>

  <div class="box t-warn">
    <b>阿里云可能因此给你发「安全告警」短信，先别慌</b>
    装 Docker、跑这次这些命令、以及容器里那个 QQ 客户端，都会触发云安全中心的
    「<strong>异常调用系统工具</strong>」「<strong>容器内部敏感手工操作</strong>」这类告警。<strong>大概率是误报</strong>，
    怎么判断、怎么处理见 <b>附录 D</b>。
  </div>

  <h3>3-2　打开管理网页</h3>
  <p>在浏览器（电脑上的 Chrome 或 Edge）地址栏输入：</p>

  <div class="codeblock">
    <div class="bar"><span>把 IP 换成你自己的</span><button class="cp">复制</button></div>
<pre><code>http://你的服务器公网IP:6099/webui</code></pre>
  </div>

  <p>比如你的 IP 是 <code>47.105.93.192</code>，那就打开 <code>http://47.105.93.192:6099/webui</code>。</p>

  <div class="box t-blue">
    <b>要你填的登录口令</b>
    口令就是第 2 步里那个：<code>qqbot-2026-secret</code>（照抄就行）。
    <span class="muted">（如果提示口令不对，回黑窗口粘 <code>docker logs napcat | grep -i token</code>，屏幕上会打印真实口令。）</span>
  </div>

  <div class="box t-warn">
    <b>浏览器会弹一个「不安全」的红色警告——这是正常的，别怕</b>
    这个网页用的是 <strong>http（没有加密证书）</strong>，浏览器对<strong>所有</strong> http 网站都这么标。
    <strong>不是中毒，也不是被劫持。</strong><br>
    但它提醒的事情是真的：<strong>现在这个网页，全网任何人扫到你的 IP 都能打开登录框。</strong>
    所以照 3-1 红框说的——<strong>第 4 步做完就把 6099 规则删掉</strong>。<br>
    <span class="muted">想更保险（可选）：把那条防火墙规则的「授权对象」从 <code>0.0.0.0/0</code> 改成你自己家的公网 IP
    （浏览器里搜「我的IP」就能看到）。这样只有你家网络能打开这个网页，规则也可以一直留着不删。</span>
  </div>

  <h3>3-3　扫码登录小号</h3>
  <ol>
    <li>进去之后，页面上会自动出现一个<strong>二维码</strong>（如果没有，点左侧的「<strong>登录</strong>」或首页的「扫码登录」）。</li>
    <li>拿出手机，<strong>先切换到那个小号的 QQ</strong>（手机 QQ 可以同时登录多个账号，切账号就行）。</li>
    <li>用<strong>小号</strong>扫这个二维码 → 手机上会提示「Linux 设备登录」，点<strong>确认登录</strong>。</li>
    <li>如果弹出验证码或设备锁提示，按手机上的提示走完。</li>
  </ol>

  <div class="box t-green">
    <b>登录成功的样子</b>
    网页上会显示这个小号的 <strong>QQ 号</strong>和<strong>在线</strong>状态。到这一步，小号就已经「住进」你的服务器了。
  </div>

  <div class="box t-red">
    <b>登录不上去 / 一直提示验证</b>
    新注册的号、或者第一次在云服务器上登录，QQ 很容易拦。<br>
    解决顺序：① 先用<strong>手机 QQ 正常登录这个小号</strong>，聊几句、挂一两天再回来扫；② 扫的时候必须<strong>用这个小号自己扫</strong>（不是用主号扫）；③ 还是不行就换一个养过一段时间的号。
  </div>

  <!-- ============ 4 ============ -->
  <h2><span class="n">4</span>配一条「连接通道」，让程序能跟小号说话</h2>

  <p>小号住进服务器了，但机器人程序还不知道怎么跟它说话。这一步就是搭这条线。</p>

  <p>在刚才那个管理网页里：</p>

  <ol>
    <li>点左侧的「<strong>网络配置</strong>」</li>
    <li>点「<strong>新建</strong>」（或右上角的「+」）</li>
    <li>类型选「<strong>WebSocket 服务器</strong>」（有的版本叫「WebSocket Server」）</li>
    <li>照着下面这张表填：</li>
  </ol>

  <table>
    <thead><tr><th>要填的</th><th>填成</th></tr></thead>
    <tbody>
      <tr><td>名称</td><td>随便，比如 <code>bot</code></td></tr>
      <tr><td>主机 / Host</td><td><code>0.0.0.0</code></td></tr>
      <tr><td>端口 / Port</td><td><code>3001</code></td></tr>
      <tr><td>Token</td><td><code>qqbot-2026-secret</code> <span class="muted">（和第 2 步一样的那个，照抄）</span></td></tr>
      <tr><td>消息格式 / MessagePostFormat</td><td><code>array</code>（如果有这个选项的话）</td></tr>
      <tr><td>启用 / Enable</td><td><strong>点开</strong>（⚠️ 新建出来默认是<strong>关</strong>的，灰色）</td></tr>
    </tbody>
  </table>

  <div class="box t-red">
    <b>最容易漏的一步：左上角那个「启用」开关</b>
    新建弹出的窗口里，左上角的「<strong>启用</strong>」开关<strong>默认是关的（灰色）</strong>。
    <strong>不点开它，保存了也不生效</strong>——后面机器人日志会一直刷「连接断开…5 秒后重连」。<br>
    👉 点一下让它<strong>变粉</strong>，再点右下角「保存」。
  </div>

  <p>填完点「<strong>保存</strong>」。</p>

  <div class="box t-blue">
    <b>怎么知道配成功了</b>
    保存后回到列表，能看到刚建的那条，状态是「<strong>运行中</strong>」或者端口显示 <code>3001</code> 在监听，就对了。
  </div>

  <div class="box t-warn">
    <b>安全提醒（重要）</b>
    6099 这个管理网页现在对全网开放，别人只要知道你 IP 就能打开登录框。<br>
    <strong>做完第 4 步就把阿里云那条 6099 规则删掉</strong>——删了不影响机器人运行，只是以后想再进网页得重新加回来。
    <span class="muted">（详见 3-1 里的红框）</span>
  </div>

  <!-- ============ 5 ============ -->
  <h2><span class="n">5</span>装机器人程序（5-1 ～ 5-8）</h2>

  <div class="box t-warn">
    <b>动手之前，先把 6099 那条规则删掉</b>
    第 4 步配完通道之后，<strong>管理网页就已经不需要了</strong>，现在正是删掉它的时机
    （机器人程序连的是服务器内部的 <code>127.0.0.1:3001</code>，跟 6099 无关，删了完全不影响后面所有步骤）。<br>
    · 以后如果<strong>临时</strong>要看网页（比如小号掉线要重新扫码）→ 把规则加回来，用完再删，20 秒的事。<br>
    · 嫌麻烦 → 把规则的「授权对象」从 <code>0.0.0.0/0</code> 改成<strong>你家宽带的公网 IP</strong>，就可以一直留着。
  </div>

  <div class="box t-red">
    <b>规矩只有一条，务必遵守</b>
    <strong>一次只粘一段。看到 <code>root@... #</code> 那行回来了，再粘下一段。</strong><br>
    一次性粘一大段，网页版终端经常「接不住」，代码就没写进去（会报 <code>No such file</code>）。拆成小段就稳了。
  </div>

  <h3>5-1　装程序运行环境</h3>
  <div class="codeblock">
    <div class="bar"><span>5-1</span><button class="cp">复制</button></div>
<pre><code>mkdir -p /opt/qqbot &amp;&amp; apt-get install -y python3-venv python3-pip &amp;&amp; python3 -m venv /opt/qqbot/.venv &amp;&amp; /opt/qqbot/.venv/bin/pip install -q --upgrade pip &amp;&amp; /opt/qqbot/.venv/bin/pip install -q websockets httpx &amp;&amp; echo "===== 5-1 完成 ====="</code></pre>
  </div>

  <h3>5-2　写程序（第 1 段）</h3>
  <div class="codeblock">
    <div class="bar"><span>5-2</span><button class="cp">复制</button></div>
<pre><code>cat &gt; /opt/qqbot/bot.py &lt;&lt;'PYEOF'
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""QQ 群聊 AI 机器人 · 连接 NapCat（OneBot v11 正向 WebSocket）"""

import asyncio, json, os, re, time
from collections import OrderedDict

import httpx, websockets

# ---- 读取同目录下的 .env ----
_here = os.path.dirname(os.path.abspath(__file__))
_envf = os.path.join(_here, ".env")
if os.path.exists(_envf):
    for _l in open(_envf, encoding="utf-8"):
        _l = _l.strip()
        if _l and not _l.startswith("#") and "=" in _l:
            _k, _v = _l.split("=", 1)
            os.environ.setdefault(_k.strip(), _v.strip())

def env(k, d=""):
    return (os.environ.get(k) or d).strip()

WS_URL    = env("ONEBOT_WS", "ws://127.0.0.1:3001")
WS_TOKEN  = env("ONEBOT_TOKEN")
LLM_KEY   = env("LLM_API_KEY")
LLM_URL   = env("LLM_BASE_URL", "https://api.deepseek.com/v1").rstrip("/")
LLM_MODEL = env("LLM_MODEL", "deepseek-flash")
SYS       = env("SYS_PROMPT", "你是群里的聊天助手，说话自然简洁，不要自称 AI 或大模型。")
MAX_TURNS = int(env("MAX_TURNS", "8"))
MAX_LEN   = int(env("MAX_LEN", "1200"))

# ---- 两道保险（群聊专用）----
# 同一个群两次回复至少隔 REPLY_GAP 秒；全机器人每分钟最多回 REPLY_PER_MIN 条
REPLY_GAP     = float(env("REPLY_GAP", "5"))
REPLY_PER_MIN = int(env("REPLY_PER_MIN", "10"))
# 只服务这几个群号（留空 = 所有群都服务）。多个群号用英文逗号隔开
ALLOW_GROUPS  = [x for x in env("ALLOW_GROUPS").split(",") if x.strip()]

def log(*a):
    print(time.strftime("%Y-%m-%d %H:%M:%S"), *a, flush=True)
PYEOF
echo "===== 5-2 完成 ====="</code></pre>
  </div>

  <h3>5-3　写程序（第 2 段）</h3>
  <div class="codeblock">
    <div class="bar"><span>5-3</span><button class="cp">复制</button></div>
<pre><code>cat &gt;&gt; /opt/qqbot/bot.py &lt;&lt;'PYEOF'

HIST = OrderedDict()
LOCKS = {}
CQ_RE = re.compile(r"\[CQ:[^\]]*\]")

# 防刷屏：同一个会话连着问，间隔不够就不理；一分钟内全机器人最多回 REPLY_PER_MIN 条
LAST = {}
RECENT = []

def _allow(key):
    now = time.time()
    if now - LAST.get(key, 0) &lt; REPLY_GAP:
        return False
    RECENT[:] = [t for t in RECENT if now - t &lt; 60]
    if len(RECENT) &gt;= REPLY_PER_MIN:
        return False
    LAST[key] = now
    RECENT.append(now)
    return True

def get_lock(k):
    if k not in LOCKS:
        LOCKS[k] = asyncio.Lock()
    return LOCKS[k]

def push(key, role, content):
    h = HIST.setdefault(key, [])
    h.append({"role": role, "content": content})
    if len(h) &gt; MAX_TURNS * 2:
        del h[:len(h) - MAX_TURNS * 2]
    if len(HIST) &gt; 800:
        HIST.popitem(last=False)

async def ask(msgs):
    async with httpx.AsyncClient(timeout=90) as c:
        r = await c.post(
            LLM_URL + "/chat/completions",
            headers={"Authorization": "Bearer " + LLM_KEY},
            json={"model": LLM_MODEL,
                  "messages": [{"role": "system", "content": SYS}] + msgs},
        )
        r.raise_for_status()
        return r.json()["choices"][0]["message"]["content"].strip()

async def send(ws, action, params):
    await ws.send(json.dumps({"action": action, "params": params}, ensure_ascii=False))

def chunks(text, size=MAX_LEN):
    return [text[i:i + size] for i in range(0, len(text), size)] or [""]
PYEOF
echo "===== 5-3 完成 ====="</code></pre>
  </div>

  <h3>5-4　写程序（第 3 段：处理消息）</h3>
  <div class="codeblock">
    <div class="bar"><span>5-4</span><button class="cp">复制</button></div>
<pre><code>cat &gt;&gt; /opt/qqbot/bot.py &lt;&lt;'PYEOF'

async def handle(ws, ev):
    if ev.get("post_type") != "message":
        return
    self_id = str(ev.get("self_id", ""))
    segs = ev.get("message") if isinstance(ev.get("message"), list) else []
    raw = ev.get("raw_message") or ""
    mtype = ev.get("message_type")

    if mtype == "group":
        at_me = any(s.get("type") == "at"
                    and str(s.get("data", {}).get("qq")) == self_id for s in segs)
        if not at_me:
            return
        if ALLOW_GROUPS and str(ev.get("group_id")) not in ALLOW_GROUPS:
            return
        key = "g" + str(ev.get("group_id"))
        if not _allow(key):
            return
    elif mtype == "private":
        key = "p" + str(ev.get("user_id"))
    else:
        return

    text = CQ_RE.sub("", raw).strip() or "你好"
    log("收到消息", key, "->", text)

    if text in ("/重置", "重置对话", "/reset", "清空对话"):
        HIST.pop(key, None)
        reply = "对话已重置，我们重新开始吧～"
    else:
        async with get_lock(key):
            push(key, "user", text)
            try:
                reply = await ask(HIST[key])
                push(key, "assistant", reply)
            except Exception as e:
                log("模型调用失败：", type(e).__name__, e)
                reply = "（我这边有点忙，稍后再问我一次～）"

    for part in chunks(reply):
        if mtype == "group":
            await send(ws, "send_group_msg", {"group_id": ev.get("group_id"), "message": part})
        else:
            await send(ws, "send_private_msg", {"user_id": ev.get("user_id"), "message": part})
PYEOF
echo "===== 5-4 完成 ====="</code></pre>
  </div>

  <h3>5-5　写程序（第 4 段：启动入口）</h3>
  <div class="codeblock">
    <div class="bar"><span>5-5</span><button class="cp">复制</button></div>
<pre><code>cat &gt;&gt; /opt/qqbot/bot.py &lt;&lt;'PYEOF'

async def connect():
    kw = dict(ping_interval=20, max_size=2 ** 23, open_timeout=20)
    h = {"Authorization": "Bearer " + WS_TOKEN} if WS_TOKEN else None
    if h:
        try:
            return await websockets.connect(WS_URL, additional_headers=h, **kw)
        except TypeError:
            return await websockets.connect(WS_URL, extra_headers=h, **kw)
    return await websockets.connect(WS_URL, **kw)

async def main():
    log("启动中，正在连接 NapCat ...")
    while True:
        try:
            ws = await connect()
            try:
                log("已连上 NapCat，等待消息 ...")
                async for raw in ws:
                    try:
                        ev = json.loads(raw)
                    except Exception:
                        continue
                    if ev.get("post_type") == "meta_event":
                        continue
                    try:
                        await handle(ws, ev)
                    except Exception as e:
                        log("处理消息出错：", type(e).__name__, e)
            finally:
                await ws.close()
        except Exception as e:
            log("连接断开（" + type(e).__name__ + "），5 秒后重连")
            await asyncio.sleep(5)

if __name__ == "__main__":
    asyncio.run(main())
PYEOF
echo "===== 5-5 完成 ====="</code></pre>
  </div>

  <div class="box t-blue">
    <b>检查一下有没有写全</b>
    粘这一行，回车，应该输出 <code>171</code>（<strong>165～175 之间都算正常</strong>）。是这个范围就没问题。
    <div class="codeblock" style="margin-top:8px">
      <div class="bar"><span>检查程序行数</span><button class="cp">复制</button></div>
<pre><code>wc -l /opt/qqbot/bot.py</code></pre>
    </div>
    如果只有十几行，说明 5-3 / 5-4 / 5-5 有哪段没粘进去，按顺序重粘一遍就行。
  </div>

  <h3>5-6　填 4 个关键信息</h3>
  <p>复制下面这一整行（很长，是一行），粘进黑窗口，回车。然后它会<strong>依次问你 4 次</strong>，你粘一个、按一次回车。</p>

  <div class="codeblock">
    <div class="bar"><span>5-6</span><button class="cp">复制</button></div>
<pre><code>printf '1/4 OneBot Token（就是 qqbot-2026-secret，直接回车也行）: '; read TK; printf '2/4 大模型 API Key: '; read LK; printf '3/4 大模型接口地址（直接回车用 DeepSeek）: '; read LU; printf '4/4 模型名（直接回车用 deepseek-flash）: '; read LM; printf 'ONEBOT_WS=ws://127.0.0.1:3001\nONEBOT_TOKEN=%s\nLLM_API_KEY=%s\nLLM_BASE_URL=%s\nLLM_MODEL=%s\nSYS_PROMPT=你是本群的 AI 助手，群里大多是本频道的粉丝。说话轻松自然、简洁不啰嗦，能回答问题也能陪大家闲聊。有人问你是谁，就大方承认自己是群里的 AI 助手。不主动加好友、不主动发消息。\nMAX_TURNS=8\n' "${TK:-qqbot-2026-secret}" "$LK" "${LU:-https://api.deepseek.com/v1}" "${LM:-deepseek-flash}" &gt; /opt/qqbot/.env; chmod 600 /opt/qqbot/.env; echo "===== 5-6 完成 ====="</code></pre>
  </div>

  <table>
    <thead><tr><th>它问</th><th>你贴什么</th></tr></thead>
    <tbody>
      <tr><td>1) OneBot Token</td><td><strong>直接回车</strong>就行（默认就是 <code>qqbot-2026-secret</code>）</td></tr>
      <tr><td>2) 大模型 API Key</td><td>你手上那个 Key（智谱是 <code>92ce...</code> 那种，DeepSeek 是 <code>sk-</code> 开头）</td></tr>
      <tr><td>3) 接口地址</td><td>用 DeepSeek 就<strong>直接回车</strong>；用智谱/龙猫的看下面的「5-6B」</td></tr>
      <tr><td>4) 模型名</td><td>同上，<strong>直接回车</strong>就是 DeepSeek 的 <code>deepseek-flash</code></td></tr>
    </tbody>
  </table>

  <p class="muted">粘上去看不见字符是正常的，粘完直接回车。</p>

  <div class="box t-red">
    <b>用 DeepSeek 的话，模型名只有一个能选</b>
    就填 <code>deepseek-flash</code>（默认已经帮你填好，直接回车即可）。<br>
    网上教程里那两种写法——<code>deepseek-chat</code> 和 <code>deepseek-reasoner</code>——<strong>官方已于 2026 年 7 月 24 日彻底下架，现在填上去会直接报错</strong>。你要是照着网上的旧教程填，机器人一句话都说不出来。
  </div>

  <h3>5-6B　换大模型（用智谱或者龙猫的话，多粘这一行）</h3>
  <p>5-6 里接口地址和模型名默认填的是 <strong>DeepSeek</strong>。如果你用的是别的家，粘下面其中<strong>一行</strong>就行：</p>

  <div class="codeblock">
    <div class="bar"><span>换成智谱 GLM</span><button class="cp">复制</button></div>
<pre><code>sed -i 's|^LLM_BASE_URL=.*|LLM_BASE_URL=https://open.bigmodel.cn/api/paas/v4|; s|^LLM_MODEL=.*|LLM_MODEL=glm-4.7-flash|' /opt/qqbot/.env; echo "===== 5-6B 完成 ====="</code></pre>
  </div>

  <div class="codeblock">
    <div class="bar"><span>换成美团龙猫（额度大、几乎不限流）</span><button class="cp">复制</button></div>
<pre><code>sed -i 's|^LLM_BASE_URL=.*|LLM_BASE_URL=https://api.longcat.chat/openai/v1|; s|^LLM_MODEL=.*|LLM_MODEL=LongCat-Flash-Chat|' /opt/qqbot/.env; echo "===== 5-6B 完成 ====="</code></pre>
  </div>

  <div class="box t-blue">
    <b>用哪家、怎么看</b>
    看你第 5-6 步第 2 个空（API Key）是从哪拿的：<br>
    · <strong>智谱</strong>（Key 长得像 <code>92ce....AbCd</code>）→ 粘「换成智谱 GLM」那一行<br>
    · <strong>DeepSeek</strong>（Key 是 <code>sk-</code> 开头）→ <strong>跳过</strong>，直接去 5-7<br>
    · <strong>美团龙猫</strong>（Key 是 <code>ak_</code> 开头）→ 粘「换成美团龙猫」那一行<br>
    <span class="muted">各家 Key 都不同，换模型不等于换 Key。更多平台见文件夹里的《免费大模型对照表.html》。</span>
  </div>

  <div class="box t-blue">
    <b>用 DeepSeek 的话，这三点帮你省钱</b>
    <b>① 挑时段用。</b>工作日北京时间 <b>09:00–12:00</b> 和 <b>14:00–18:00</b> 是高峰，价钱翻倍；<strong>其余时间（含整个周末、节假日）全部半价</strong>。粉丝群主要晚上活跃，基本全程踩在半价上。<br>
    <b>② 它本身已经极便宜了。</b>一次问答折算下来<strong>不到一分钱</strong>，一千次问答大约 2～4 元。充 10 元够用很久。<br>
    <b>③ 先看有没有赠送额度。</b>刚注册的账号通常有一笔赠送余额，去后台「余额」里看一眼，先用完再说。没有赠送再充值，<strong>充 10 元就够</strong>。
  </div>

  <h3>5-7　设成开机自启并启动</h3>
  <p>最后一段。整段复制（<strong>三部分都要，包括最后的 <code>SVCEOF</code></strong>），粘进去回车。</p>

  <div class="codeblock">
    <div class="bar"><span>5-7</span><button class="cp">复制</button></div>
<pre><code>cat &gt; /etc/systemd/system/qqbot.service &lt;&lt;'SVCEOF'
[Unit]
Description=QQ AI Bot
After=network-online.target docker.service
[Service]
WorkingDirectory=/opt/qqbot
ExecStart=/opt/qqbot/.venv/bin/python /opt/qqbot/bot.py
Restart=always
RestartSec=5
StandardOutput=append:/var/log/qqbot.log
StandardError=append:/var/log/qqbot.log
[Install]
WantedBy=multi-user.target
SVCEOF
systemctl daemon-reload; systemctl enable qqbot &gt;/dev/null 2&gt;&amp;1; systemctl restart qqbot; sleep 6; echo "===== 部署结果 ====="; systemctl is-active qqbot; tail -n 12 /var/log/qqbot.log</code></pre>
  </div>

  <div class="box t-green">
    <b>看到这两句就是成功了</b>
    <code>active</code>（服务在跑）<br>
    <code>已连上 NapCat，等待消息 ...</code>（通道打通了）<br>
    <span class="muted">如果看到的是「连接断开…5 秒后重连」，说明第 4 步的 Token 和这里不一致，回第 4 步核对一下。</span>
  </div>

  <h3>5-8　锁定你的群（等你第 6 步 @ 成功之后，再回来做）</h3>

  <p>程序里已经自带两道保险，<strong>你什么都不用做就生效了</strong>：</p>
  <table>
    <thead><tr><th>保险</th><th>效果</th></tr></thead>
    <tbody>
      <tr><td><b>只在被 @ 时才回</b></td><td>群里正常聊天它完全不插嘴；也从不主动加好友、从不群发消息</td></tr>
      <tr><td><b>防刷屏</b></td><td>同一个群 5 秒内只回一条；整个机器人每分钟最多回 10 条。群友起哄连刷也不会把你的额度烧掉</td></tr>
    </tbody>
  </table>

  <div class="box t-warn">
    <b>还剩一个口子：小号是公开的</b>
    小号的 QQ 号在群里人人可见。别人可以把它<strong>拉进自己的群</strong>，白嫖你的大模型额度。
    下面这一步就是把这个口子堵上——<strong>让它只服务你指定的群</strong>。
  </div>

  <h4>第 1 步：拿到你的群号</h4>
  <p>先在群里 @ 它一次（确认能回），然后粘这一行：</p>
  <div class="codeblock">
    <div class="bar"><span>查群号</span><button class="cp">复制</button></div>
<pre><code>grep "收到消息" /var/log/qqbot.log | tail -n 3</code></pre>
  </div>
  <p>会输出类似这样的一行，那个 <code>g</code> 后面的一串数字就是群号：</p>
  <div class="codeblock">
    <div class="bar"><span>输出长这样</span><button class="cp">复制</button></div>
<pre><code>2026-10-02 10:00:00 收到消息 g123456789 -&gt; 你好</code></pre>
  </div>
  <p class="muted">
    也可以不走命令：手机 QQ → 你的群 → 右上角「⋯」→ 群资料里直接能看到「群号」那一串数字，效果一样。
    <br>注意：如果你已经填过 <code>ALLOW_GROUPS</code>，白名单之外的群就不会再被记录了，所以这一步要在填白名单<strong>之前</strong>做。
  </p>

  <h4>第 2 步：填进去</h4>
  <p>把下面这行里的 <code>123456789</code> 换成你的群号，整行复制、粘贴、回车：</p>
  <div class="codeblock">
    <div class="bar"><span>只服务这一个群</span><button class="cp">复制</button></div>
<pre><code>sed -i '/^ALLOW_GROUPS=/d' /opt/qqbot/.env; printf 'ALLOW_GROUPS=123456789\n' &gt;&gt; /opt/qqbot/.env; systemctl restart qqbot; echo "===== 5-8 完成 ====="</code></pre>
  </div>
  <p>再 @ 一次，有回复就成了。<strong>有几个群就写几个，用英文逗号隔开</strong>，例如 <code>ALLOW_GROUPS=123456789,987654321</code>。</p>

  <div class="box t-blue">
    <b>想调松紧（可选）</b>
    默认「同一个群 5 秒内只回一条」。嫌它反应慢，粘这一行改成 2 秒：<br>
    <span class="muted">（把最后那个 <code>2</code> 换成你要的秒数）</span>
    <div class="codeblock" style="margin-top:8px">
      <div class="bar"><span>改冷却时间</span><button class="cp">复制</button></div>
<pre><code>sed -i '/^REPLY_GAP=/d' /opt/qqbot/.env; printf 'REPLY_GAP=2\n' &gt;&gt; /opt/qqbot/.env; systemctl restart qqbot</code></pre>
    </div>
  </div>

  <div class="box t-blue">
    <b>主线到这就够了</b>
    再往下原本还有 5-9 人设、5-10 违规检测、5-11 联网三节，都是<strong>进阶加分项</strong>，
    已经整体挪到文末的 <strong>附录 E</strong>。<span class="muted">不做也完全能用，有空再翻。</span>
  </div>

  <!-- ============ 6 ============ -->
  <h2><span class="n">6</span>把小号拉进群，@ 它</h2>

  <ol>
    <li>打开手机 QQ，切到<strong>你的主号</strong>（群主那个号）</li>
    <li>进你的群 → 右上角「⋯」→「<strong>邀请好友</strong>」或「+」→ 搜你那个小号的 QQ 号 → 邀请进群</li>
    <li>（如果搜不到，先用主号把小号<strong>加为好友</strong>，再拉进群）</li>
    <li>在群里发：<code>@小号 你好</code></li>
  </ol>

  <p>几秒内有回复，就全部搞定了。</p>

  <div class="box t-blue">
    <b>小号进群后建议做的一件事</b>
    ① 在群里把小号设成「<strong>消息免打扰</strong>」——它不用看群里所有聊天，只在你 @ 它的时候才回应，省内存也更清爽。
  </div>

  <div class="box t-red">
    <b>⚠️ 千万不要把小号「禁言」</b>
    禁言是<strong>禁止发言</strong>，一旦设了，它在群里就<strong>一个字都发不出来</strong>，@ 它也没用。
    要的是「消息免打扰」（它自己不看群），不是「禁言」（不让它说话）。这两个别搞混。
  </div>

  <!-- ============ 附录 A ============ -->
  <h2>附录 A · 以后常用的几句话</h2>

  <div class="codeblock">
    <div class="bar"><span>看机器人日志（出问题先看这个）</span><button class="cp">复制</button></div>
<pre><code>tail -n 30 /var/log/qqbot.log</code></pre>
  </div>

  <div class="codeblock">
    <div class="bar"><span>重启机器人</span><button class="cp">复制</button></div>
<pre><code>systemctl restart qqbot</code></pre>
  </div>

  <div class="codeblock">
    <div class="bar"><span>看小号是不是还在线（NapCat 状态）</span><button class="cp">复制</button></div>
<pre><code>docker logs --tail 20 napcat</code></pre>
  </div>

  <div class="codeblock">
    <div class="bar"><span>重启小号程序</span><button class="cp">复制</button></div>
<pre><code>docker restart napcat</code></pre>
  </div>

  <div class="codeblock">
    <div class="bar"><span>改机器人的说话风格</span><button class="cp">复制</button></div>
<pre><code>nano /opt/qqbot/.env</code></pre>
  </div>
  <p class="muted">↑ 打开后找到 <code>SYS_PROMPT</code> 那一行，改掉等号后面的中文。
  改完按 <strong>Ctrl+O</strong> 再回车保存，按 <strong>Ctrl+X</strong> 退出，最后执行 <code>systemctl restart qqbot</code>。</p>

  <div class="codeblock">
    <div class="bar"><span>看内存够不够（1G 内存的机器要常看）</span><button class="cp">复制</button></div>
<pre><code>free -h; echo "-----"; docker stats --no-stream</code></pre>
  </div>
  <p class="muted">重点看两处：<code>free</code> 里的 <code>available</code>（还剩多少能用）、以及 <code>Swap</code> 的 used（有没有在拿硬盘当内存用）。
  <b>Swap 用得越多＝内存越不够</b>，机器会明显变慢。</p>

  <div class="box t-warn">
    <b>内存不够的典型症状（1G 的机器要认识这几个）</b>
    · 小号时不时掉线、自己重连<br>
    · <code>docker ps --filter name=napcat</code> 里状态变成 <code>Restarting</code> 或 <code>Exited</code><br>
    · 群里 @ 它反应特别慢，或者干脆不回<br>
    · <code>docker logs napcat</code> 里出现 <code>Killed</code> 字样<br>
    👉 出现这些＝1G 内存扛不住。去阿里云把这台服务器「<strong>升级套餐</strong>」到 <strong>2核2G</strong>：
    <strong>数据不丢、公网 IP 不变</strong>，只是要重启一次。
  </div>

  <div class="box t-blue">
    <b>服务器重启后会自动运行吗</b>
    会。机器人设了开机自启，NapCat 也带 <code>--restart always</code>，服务器重启后两个都会自己起来。
  </div>

  <!-- ============ 附录 B ============ -->
  <h2>附录 B · 出问题对着这张表查</h2>

  <table>
    <thead><tr><th>现象</th><th>原因和处理</th></tr></thead>
    <tbody>
      <tr><td>粘某一步后提示 <code>No such file</code></td><td>前面某一步没粘进去。看每一步结尾有没有打印 <code>===== x-x 完成 =====</code>，缺哪步补哪步</td></tr>
      <tr><td>5 之后 <code>wc -l</code> 只有十几行</td><td>5-3 / 5-4 / 5-5 有段落没粘全。按顺序重粘一遍（<code>cat &gt;&gt;</code> 是追加，重来即可）</td></tr>
      <tr><td>2-2 报 <code>i/o timeout</code> / <code>failed to resolve reference</code></td><td>服务器连不上境外镜像仓库。回 <b>2-1</b> 换成国内镜像源，再重粘 2-2</td></tr>
      <tr><td>2-2 报 <code>manifest unknown</code> 或 <code>not found</code></td><td>镜像名打错了。必须一字不差：<code>mlikiowa/napcat-docker:latest</code></td></tr>
      <tr><td>2-2 报 <code>port is already allocated</code></td><td>上次跑过一半。先粘 <code>docker rm -f napcat</code>，再重粘 2-2</td></tr>
      <tr><td>网页 <code>IP:6099</code> 打不开</td><td>① 阿里云「防火墙/安全组」没放行 6099（见 3-1）② 容器没跑起来，执行 <code>docker ps --filter name=napcat</code> 看</td></tr>
      <tr><td>网页打开但不知道口令</td><td><code>docker logs napcat | grep -i token</code></td></tr>
      <tr><td>扫码后提示登录失败 / 要验证</td><td>小号被风控了。先用手机 QQ 正常登录它、聊几天再来；或换一个养过的号</td></tr>
      <tr><td>日志一直「连接断开…5 秒后重连」</td><td>第 4 步的 Token 和 5-6 填的不一样，或者第 4 步的通道没「启用」。回第 4 步核对</td></tr>
      <tr><td>群里 @ 它，完全没反应</td><td>① 小号没被拉进这个群 ② 日志里没有「收到消息」→ 小号掉线了，进网页看在线状态（需先把 6099 规则加回来）③ 日志里有「收到消息」但没回 → 大模型问题（见下条）④ 做过 5-8 的话，确认这个群的群号填进白名单了</td></tr>
      <tr><td>刚 @ 过，紧接着再 @ 它就不理</td><td>撞上了 5 秒冷却（5-8 里那两道保险）。等一下再 @ 就行，这是故意设的，防群友连刷烧额度</td></tr>
      <tr><td>@<b>全体成员</b>时它不回</td><td><b>这是正常的，也是故意的</b>。程序只认「单独 @ 它本人」——「@全体成员」在 QQ 里是另一个东西，不算 @ 它。想让它答，就在同一条消息里再单独 @ 它一下</td></tr>
      <tr><td>回复「（我这边有点忙，稍后再问我一次～）」</td><td>大模型那边报错了。多半是免费额度被限流，或 Key 不对。执行 5-6 重填，或 5-6B 换一家模型</td></tr>
      <tr><td>小号掉线了</td><td>① 先把 6099 防火墙规则加回来 ② 进网页 <code>IP:6099/webui</code> 重新扫码 ③ 用完再把规则删掉。QQ 也会因为换 IP、版本升级等原因踢下线，属正常</td></tr>
      <tr><td>黑窗口粘不进去 / 乱码</td><td>换电脑上的 Chrome 或 Edge 打开控制台，别用手机操作</td></tr>
      <tr><td>窗口关了机器人还在跑吗</td><td>在。程序和容器都设了自动运行，关窗口不影响</td></tr>
    </tbody>
  </table>

  <div class="box t-warn">
    <b>卡住了别自己瞎试</b>
    屏幕上出现<strong>红色文字</strong>或者一大段英文报错，直接截图发我。
    尤其是日志里带 <code>【</code>、<code>Traceback</code>、<code>连接断开</code> 的，一眼就能看出问题。
  </div>

  <!-- ============ 附录 C ============ -->
  <h2>附录 C · 怎么把「被封号」的风险压到最低</h2>

  <div class="box t-red">
    <b>唯一的铁律</b>
    <strong>只用小号。</strong>这一条做到，最坏的结果就是损失一个 QQ 号，你的正常生活不受影响。
  </div>

  <h4>什么情况最容易出事</h4>
  <table>
    <thead><tr><th>情况</th><th>为什么危险</th></tr></thead>
    <tbody>
      <tr><td><strong>新注册的号</strong>（一两个月内）</td><td>最大的杀手。新号在云服务器上登录，腾讯基本一定要求验证。社区里"当天晚上就吃风控、之后每隔几小时被踢"的，几乎全是新号</td></tr>
      <tr><td>号长期没登录，突然在异地登录</td><td>腾讯判定"疑似被盗"，直接保护性下线</td></tr>
      <tr><td>机器人<strong>主动</strong>干活：加好友、拉人进群、大量私聊、群发</td><td>腾讯官方白纸黑字把「频繁发送广告/垃圾消息」和「通过非官方版本软件登录 QQ」列为冻结原因</td></tr>
      <tr><td><strong>被群里的人举报</strong></td><td>几个人一举报，人工复核基本就废了。这条最防不住，也最现实</td></tr>
      <tr><td>短时间内反复重试登录</td><td>越试越糟，会加重风控标记</td></tr>
      <tr><td>群里聊违法、敏感内容</td><td>连带封号，没有商量余地</td></tr>
    </tbody>
  </table>

  <h4>降低风险的做法（按重要性排）</h4>
  <ol>
    <li><strong>用养过一段时间的号</strong>——注册一个月以上，有好友、有聊天记录，QQ 等级越高越稳</li>
    <li><strong>上服务器之前，先用手机正常登录它、挂几天</strong>，让它有"正常使用"的痕迹</li>
    <li><strong>打开 NapCat 的反检测开关</strong>：在管理网页里找「配置 / 系统配置」里那组带「<strong>反检测</strong>」（可能写成 Bypass）的开关，<strong>全部打开</strong>。有的版本默认就是开的，确认一下</li>
    <li><strong>让机器人只做被动回复</strong>——本手册这套程序本身就是「只在被 @ 时才说话」。<strong>永不主动加人、永不主动群发</strong>，这条最有效</li>
    <li><strong>在群里公开说一句「这是 AI 助手」</strong>，请群友别举报。这条很俗，但确实管用</li>
    <li><strong>别频繁重启、别换服务器 IP</strong>。设备/IP 频繁变化本身就是风控特征</li>
    <li>如果掉线频繁，把 NapCat 换成<strong>社区反馈较稳的版本</strong>（有人实测最新版一两天必掉、退回 4.15.0 那类老版本就稳了）</li>
    <li><strong>在手机 QQ 里把「加我为好友时需要验证」打开</strong>——防止陌生人加它、拿它做别的事。顺手再把「允许通过群聊加我为好友」「允许陌生人查看资料」这类口子关掉</li>
  </ol>

  <div class="box t-warn">
    <b>手机 QQ 和服务器能同时在线，但别来回折腾</b>
    手机 QQ 占的是「手机」这个位置，服务器上的小号占的是「电脑」位置，<strong>两处可以同时登录，不会互相顶下线</strong>。<br>
    但<strong>别在两台设备之间反复切换登录</strong>——这本身就是风控特征。想改设置就用手机登一次，改完退出，让服务器那个安稳待着。
  </div>

  <h4>万一出事</h4>
  <table>
    <thead><tr><th>症状</th><th>怎么办</th></tr></thead>
    <tbody>
      <tr><td>被踢下线（最常见）</td><td>① 先把阿里云那条 <b>6099</b> 防火墙规则<b>加回来</b>（第 5 步之前删掉的那条）② 打开网页 <code>IP:6099/webui</code> 重新扫码 ③ 扫完<b>再把 6099 规则删掉</b>。几秒钟的事</td></tr>
      <tr><td>要求验证 / 部分功能被限制</td><td><strong>停 1～2 天别碰它</strong>，然后用手机登录，走一遍官方验证流程。别连续申诉，会被当成机器人</td></tr>
      <tr><td>被封号</td><td>换一个号重来。<strong>损失就是一个 QQ 号</strong>——所以千万别用主号</td></tr>
    </tbody>
  </table>

  <div class="box t-blue">
    <b>一句实在话</b>
    用「只在被 @ 时才回复、从不主动发消息」这种最温和的用法，社区里大多数人<strong>能长期稳定跑</strong>，偶尔掉线重扫即可。
    但如果你的号很新、或者群里有人举报，风险会明显上升。<strong>心里按"随时可能要换号"来准备，就不会被打乱节奏。</strong>
  </div>

  <!-- ============ 附录 D ============ -->
  <h2>附录 D · 阿里云发「安全告警」短信了，怎么办</h2>

  <p>装完这一套之后，阿里云云安全中心<strong>大概率会给你发告警</strong>，常见的名字有：</p>

  <table>
    <thead><tr><th>告警名称</th><th>为什么会被触发</th></tr></thead>
    <tbody>
      <tr><td><strong>异常调用系统工具</strong></td><td>你这次跑的 <code>fallocate</code>、<code>mkswap</code>、<code>swapon</code>、<code>systemctl</code>、<code>apt-get</code> 都属于"调用系统工具"。木马也爱用这套动作，所以规则会一起报</td></tr>
      <tr><td><strong>容器内部敏感手工操作</strong> / <strong>容器异常行为</strong></td><td>容器里的 QQ 客户端会装东西、探测环境、调用系统命令——这本来就是它的工作方式</td></tr>
      <tr><td><strong>疑似权限提升</strong> / <strong>容器高风险操作</strong></td><td>NapCat 的反检测机制会做一些"不该有的"动作（内存注入、隐藏模块），正是这类规则的典型触发源</td></tr>
    </tbody>
  </table>

  <p class="muted">阿里云官方文档对这几类告警的原话就写着：<b>「同时也有一定概率为正常业务或运维需求……如发现该告警为误报，可在告警处理页面选择『加白名单』或者『忽略』。」</b>——所以误报是被官方承认的常见情况。</p>

  <h3>第一步：先看告警详情（30 秒）</h3>
  <p>阿里云控制台 → <strong>云安全中心</strong> → 左侧「<strong>安全告警</strong>」（或"安全警告"）→ 点开那条告警，看三样：<br>
  <strong>进程路径 / 命令行 / 关联文件</strong>。</p>

  <table>
    <thead><tr><th>告警里出现这些字眼</th><th>结论</th></tr></thead>
    <tbody>
      <tr>
        <td><code>QQ</code>、<code>napcat</code>、<code>docker</code>、<code>containerd</code>、<code>apt</code>、<code>dpkg</code>、<code>systemctl</code>、<code>bash</code>、<code>sh</code>、<code>python</code>、<code>fallocate</code>、<code>swapon</code>、<code>mkswap</code></td>
        <td><strong>误报。</strong>全是这次装的东西和命令，正常</td>
      </tr>
      <tr>
        <td>不认识的随机名字（一串无意义英文/数字）、路径在 <code>/tmp</code> 或 <code>/dev/shm</code> 下、命令行里有 <code>curl</code> 一个陌生 IP、<code>base64 -d</code>、<code>/dev/tcp</code></td>
        <td><strong>要认真看。</strong>截图发我</td>
      </tr>
    </tbody>
  </table>

  <h3>第二步：黑窗口自查（可选，粘这一行）</h3>
  <div class="codeblock">
    <div class="bar"><span>看看有没有陌生进程和文件</span><button class="cp">复制</button></div>
<pre><code>ps aux --sort=-%cpu | head -12; echo "-----"; docker ps -a; echo "-----"; ls -lt /root /tmp | head -20</code></pre>
  </div>
  <p>正常情况下你应该只看到：<code>QQ</code>/<code>napcat</code> 相关进程、<code>docker</code>、<code>containerd</code>、系统自带进程。<br>
  有完全不认识的东西 → 截图发我。</p>

  <h3>第三步：确认是误报就「忽略」</h3>
  <p>在告警那一行的右侧点「<strong>处理</strong>」，选择：</p>
  <ul>
    <li><strong>加白名单</strong>（推荐）——以后同类行为不再打扰你</li>
    <li><strong>忽略</strong>——只是这条不响了，以后还会再报</li>
  </ul>
  <p class="muted">注意：部分处置功能需要云安全中心付费版。免费版如果点不了「处理」，在 App 里标记为"已读/误报"即可，不影响使用。</p>

  <div class="box t-red">
    <b>什么情况要真紧张（很少见，但要知道）</b>
    告警名称是这几种的，别忽略，立刻处理：<strong>反弹 Shell、挖矿/恶意进程、密码破解（暴力破解）、恶意文件</strong>。<br>
    处置：① 把 SSH 密码改强、最好改用密钥登录；② 关掉所有用不上的开放端口；③ 截图发我。
  </div>

  <div class="box t-blue">
    <b>还有一个「告警」不是误报，得认真对待</b>
    如果阿里云发的是关于 <strong>6099 端口暴露</strong> 或 <strong>Docker 接口对公网开放</strong> 的提示——那是<strong>对的</strong>。
    照 3-1 红框说的，配完第 4 步就把 6099 的防火墙规则删掉。
  </div>

  <!-- ============ 附录 E ============ -->
  <h2>附录 E · 进阶玩法（做完主线再回来）</h2>

  <p>下面三节都是<strong>加分项</strong>，不做也能正常用。想做哪个做哪个，互不影响。
  <span class="muted">编号沿用原来的 5-9 / 5-10 / 5-11 没动，方便和你之前的记录对上。</span></p>

  <table>
    <thead><tr><th style="width:16%">小节</th><th>做什么</th><th style="width:30%">值不值得做</th></tr></thead>
    <tbody>
      <tr><td><b>5-9</b></td><td>给它一句人设，决定它在群里怎么说话</td><td>推荐做，粘一行就行</td></tr>
      <tr><td><b>5-10</b></td><td>自动盯违规内容 + 你能 @ 它下管理指令</td><td>群大了再折腾</td></tr>
      <tr><td><b>5-11</b></td><td>让它能联网，能查最新比分 / 新闻 / 价格</td><td>要查实时消息才需要</td></tr>
    </tbody>
  </table>

  <div class="box t-warn">
    <b>做之前先确认一件事</b>
    上面的<strong>第 5 步和第 6 步都跑通了</strong>（群里 @ 它有回复），再回来动这里。
    不然出问题不好判断是哪一环的。
  </div>

  <h3 class="adv"><span class="tag">进阶</span>5-9　给它一句人设（决定它在群里怎么说话）</h3>
  <p>粘一次就生效，<strong>复制粘上去就行，一个字都不用改</strong>。
  以后想改，把这一行重新粘一次即可（会覆盖旧的，不会重复）。</p>

  <div class="codeblock">
    <div class="bar"><span>设置人设</span><button class="cp">复制</button></div>
<pre><code>sed -i '/^SYS_PROMPT=/d' /opt/qqbot/.env; printf 'SYS_PROMPT=%s\n' "你是本群的 AI 助手，群里大多是本频道的粉丝。说话轻松自然、简洁不啰嗦，能回答问题也能陪大家闲聊。有人问你是谁，就大方承认自己是群里的 AI 助手。不主动加好友、不主动发消息。" &gt;&gt; /opt/qqbot/.env; systemctl restart qqbot; echo "===== 5-9 完成 ====="</code></pre>
  </div>

  <p class="muted">想把频道名写进去也行：把那句里的「本群」改成你的频道名，其余照旧。</p>

  <div class="box t-blue">
    <b>最后那句「不主动加好友、不主动发消息」别删</b>
    这句让它保持<strong>只被动回复</strong>——不主动撩人、不群发。这是整条路上最有效的降险手段，留着它。<br>
    <span class="muted">（人设里没有写「不许聊违规内容」，也不需要写：模型自己就带内容安全策略，真问到违法违规的东西它自己会拒答。）</span>
  </div>

  <!-- ============ F-2 ============ -->
  <h3 class="adv"><span class="tag">进阶</span>5-10　违规内容检测 + 群主管理指令（可选）</h3>

  <p>装完之后它多两个能力：<strong>盯群里的违规内容</strong>，以及<strong>你 @ 它就能下命令</strong>。
  「只在被 @ 时才回复」这条完全不变——<strong>它依然不会主动找人说话、不会加好友</strong>。</p>

  <h4>它怎么处理违规</h4>
  <table>
    <thead><tr><th style="width:42%">情况</th><th>它的动作</th></tr></thead>
    <tbody>
      <tr><td>有人发<strong>明确违规</strong>的词<br><span class="muted">加微信、刷单、外挂、涉黄涉赌…</span></td>
          <td><strong>第 1 次</strong>：在群里 @ 他警告一句，<strong>不处置</strong><br>
              <strong>第 2 次起</strong>：禁言 10 分钟<br>
              每次都<strong>私聊告诉你</strong>是谁、发了什么、第几次</td></tr>
      <tr><td>有人发<strong>可疑</strong>的词<br><span class="muted">翻墙、炒币、破解、引流…</span></td>
          <td><strong>不动任何人</strong>，只私聊告诉你，由你决定怎么办</td></tr>
      <tr><td>你自己发的内容</td><td>一律不碰（程序跳过群主）</td></tr>
    </tbody>
  </table>

  <p class="muted">按 7 天一个周期算：7 天前的记录自动作废，不会无限累计。</p>

  <h4>怎么装</h4>
  <p>下面<strong>三段</strong>，<strong>按顺序粘</strong>，每段粘完等提示符（<code>root@... #</code>）回来再粘下一段。</p>
  <div class="codeblock">
    <div class="bar"><span>5-10-1　第 1 段</span><button class="cp">复制</button></div>
<pre><code>echo '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' &gt; /tmp/u1</code></pre>
  </div>

  <div class="codeblock">
    <div class="bar"><span>5-10-2　第 2 段</span><button class="cp">复制</button></div>
<pre><code>echo '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' &gt;&gt; /tmp/u1</code></pre>
  </div>

  <div class="codeblock">
    <div class="bar"><span>5-10-3　第 3 段</span><button class="cp">复制</button></div>
<pre><code>echo 'WeVVW0N7oFiAV2T51Ocnte3eXC/rEiWfNRJf+eQusyGSbYCgN3PMwJRVG/izvfSMF/ybTD6RjqTdg+w01bOALy0+c2emtyxDbWcBj+BQH2y7E4df6NG6GfUwGxGjdkbJ2WmvbgCFZW/e4mPauY3rzm57CRdYNqOBgxE5HGjgVwNRLxm7MVvu1s/uJ/XuMiA8It1tDbxbtb+bbzMQNQT0F2/WneILSg1tcSQja7pdFONNFchaOgLxl5MJpw9oTQ6tZY83YcOhTErh1YKYIPq/WlqQk2gIc0hhRk2P+MTMLmwG3VuT6Jb1GqwKhMgPq+kDnmq3IifBojZeEJt69O68mvq37X2KzeCnK6AEAQwvpB6IlVUEwcAseJ8ZGOCUPIdpQTvWxDRzm7NlotavAbFE37a1nmkdaIdJkUqeGT3SH1fllKZgjlkCk6P3aJEy1aDSks9ItE1MdOdTCZi3va22vc1Ja8KlPWO7pwqdFg909+TSGk8YaKl/K428ZNpfVtJGD4BSDSlAFXu1U2lOUTMv57qUSG2MsgqNbBigaDvNzYliu48lusGbzyjUhii9rrApvczBx/2VeJQJnpqbmQ3L/fKwkoePNgjeKtJaF0arnrJOdkTi6YRxL9Yd8x72zNSFTmngTetyLqFEyp7HaN1JlPnR3HNV5T4PKLiTXHBoa5mlyOJCy6fk6w/kUMpiaG8SHG14I6GlsXGtpyMiwsJgVs87B3ZOlE0JlKW23EPXrjIaObGch0h2ks9bvI7xGY7m6jI86xzAmJ24/nfmAcGDoiFf3Tp9SWkSQ/NXc3bLmHf28shNyyU9dMS0v6IyUl8Y8PvychYpDv1Z14SsJllHpymXSqSxm2+rPLMzVbSnrOA7Fj+PBeHgjeNSN0acc0l8kWrzcWnzmSe+lSjacq4/EnoSE+p47Ol0xuUs/wlQWcBBcXjnfj70Hd8WX9+G7S1uXGVZTqGMiu9/kltxbmP0R6Td0nxxc5vNbq1MwoU5sehS9tZLlnuFYLb4+g5ev5rDQ/Lx5zvXnlurl2C48f0VH55A8j7HT3YKd50a+t3RAiuOoVMX2hVYXZCmZY5YCBia3HfFllezeASXz1HAOXr4HP4ojkPzqgrH68ecwOKW6B7qm9df4quU1A0HdqF+CCtjYMdWgkcIaT2GWLNzebK0tYxqgl0xJxTva1QFfBr+4gBEW/xJtNyPYA6PPzyi59a4NjYMUwwUPj0unSlu/gS3+DYke+N1+vFvW9+LIcv3uB2un1dGctdFo8ah7JiurNgoiKVdGJamDhN1RcuPLT2zyJqWQpuC5KEwAknF3cuP/AUelG1ZLVl5/ZhbPkZrkyrhL7JjH2t71nrzCs98Lr4ytmcxwb00CfGYMTK5c2sZ6U7fAgVaY+gvOBVHBQiHkR+4R8FW5Ks6qmx73r/grMxG+cu4EJmBPRy77bVSLOg2hM7mK8rM53IKvrrCi2nRHUjiuywFLHdMgTOm9sqZxnrwm7LyeYl6XvVkP7jeB2K0YF1yCqZqo06QsLvjar8hOIDEdl4XpG6Jc9IPT7o9mYAgP/tqHN0XTeP2ctiLizHQ28kUYiBnJNup7o4B+uk+D9EZA5+GTQ+8+vE+M4EMqnL4JHsFwUZ4dycrp3IR5xUNzGROrxjjSzSVOoHVLPeWfG9xk3g8zh2yvu5URqGh4y5kpIeYPGSxGeHdioRhsvYzTF1cH3deIJ8oPRsz3gwzjezBpJydwyqjfL0oAVBY0T/F10+08Fq4UPScfcXXaZ13O0DS5b7wkrbKr3vs6djVAePx7GitbvhsGESAn07tKi2JQveHvvvEK2ErT4/vObtlxhW7caPdGU8C+Ei0YddT9U4M5iUwfxjMQ6Tz+9ZeITJqpJGRLktKLw0jfx/wXXeZcZQ/WtvTLlM7VV8ZMONylkFnZ32XN3auz3oNVr3PYtX75y0rdC4rA09k8po3qbAHS8pralDkzZvPwKEAW4gqNWhA8ZQBzB4I5UF8ORDMIrggME4MO+O2T4e0jKIUIgdRBeGr7DYo3ERJQlUkSaLngARGqD25CNNRUYF+oYJ/4aOtnn7v4uaq+5mMkVljeNHzhQ/+xQ37vVbv9zjc7184Tz/99KMm9gGM8ndfnQ8+sHezy7/5wN+J3UegmzU/QSvmnoLTjWeq4w/oxR3+hZGbq3Arks8+I+5XSxw0CDoe9NVKwt65NEaGWXF06fqceWOUu+yedy4FgI8ZqjfLxe15vHGvoLlXMMd+LD0YsrbvAur8Bh4JrGHn4YiApYsvXsGVMXVTKG4+Km1eEozRNWPyBv2zuGWtfAudXltDE+atxdLmd4KxcNOcuCgAa9A/lzeM68vWix+MqTWhuHW1uLkGUIzhYQELSUafCNbYz+YluHu0DqGPUNr4oXRxWbB+nTAm7wjwn7H1BMA/M6ZH8QrTMrde4hWWc/+yJJiPrpTGJozlBcF6sWb+9AZoYo69EozFW6Wrq4L54hZEK4K1hm9iC7h/7gdRDtDvqABfjN41Njec73sghT37S/dmLPgxFTrW2RQE8uw2WEIkP31NG0IFVhBKq0En2VdVyviueVe+a3b4rpnzXdlL0u/8WEg4x41yjtOUJKlOkY9q4LYm+VGA4ej8Qml703g4K/QWckLp4jVjfUgwJ26W5rYFc/yG9eu3lGuuYMkXZyHj9Q3z1yEBUDHm5oTSgxfW40dC6e6t0tgoZwzrzbAx/kQoDa3Czu/MvyrdXRaafTvzcdnO8M+tjDIKhO/Jx3xPmt9nT8A7w69tRKLkgkBtiPOVHvrhDs/eENIFjjqpPkfEf35Y1yh6On3zDccB2j+sp7LrPBRQDQsD9kS+ss+6WqfZ9ykA8men3SkRF0VbsR3Ede4MY3QH1MN1rj4vbk0yxUbnBUvXSz/Qwz7OI5LqLCn0S/wdcN93feo/q9GzBeioqKqzVD7RJziRtfLM/OUGni3NLQJnWduXA3T/4ANfHzummkDvjL22sX3buDrHvpZkjo+D3PLvJI0vgjHDiunNWVBFaNW4CLgoBfbE930j59NMwa8n2c8966QfYSL8i0x049kJc0LPgG9M85OEfR+KWiBygBPbvDdpjM+Xxl+ag0OA4IcRd1hKq8YXkXoVNjAq+j8tRT8qxb4MZX9a6n/owd3hlEoAAA==' &gt;&gt; /tmp/u1 &amp;&amp; base64 -d /tmp/u1 | gunzip &gt; /opt/upgrade.sh &amp;&amp; rm -f /tmp/u1 &amp;&amp; bash /opt/upgrade.sh</code></pre>
  </div>

  <div class="box t-warn">
    <b>第 3 段粘完就自动装好并重启了</b>
    屏幕上最后会打印 <code>服务状态：active</code> 和 <code>===== 升级完成 =====</code>。<br>
    它会先备份你现在的程序（存成 <code>bot.py.v1bak</code>），万一新程序有问题会自动还原。
  </div>

  <div class="box t-blue">
    <b>装完默认「群主自动识别」</b>
    它会自己在你的群里找出群主（也就是你），用来发私聊通知、以及判断谁能下指令。<br>
    <span class="muted">如果日志里提示没识别到，就粘这一行手动指定（把数字换成你自己的 QQ 号）：</span>
    <div class="codeblock" style="margin-top:8px">
      <div class="bar"><span>手动指定群主</span><button class="cp">复制</button></div>
<pre><code>sed -i '/^ADMIN_QQ=/d' /opt/qqbot/.env; echo "ADMIN_QQ=你的QQ号" &gt;&gt; /opt/qqbot/.env; systemctl restart qqbot</code></pre>
    </div>
  </div>

  <h4>怎么验证</h4>
  <p><strong>你自己发测试词是不动的</strong>（程序跳过群主），所以要么用小号、要么让群友发。
  或者先只看看词表：</p>
  <div class="codeblock">
    <div class="bar"><span>查看当前词表</span><button class="cp">复制</button></div>
<pre><code>cat /opt/qqbot/badA.txt; echo "-----"; cat /opt/qqbot/badB.txt</code></pre>
  </div>

  <h4>加词 / 删词（改完 10 秒内生效，不用重启）</h4>
  <div class="codeblock">
    <div class="bar"><span>加一个「明确违规」词</span><button class="cp">复制</button></div>
<pre><code>echo "新词" &gt;&gt; /opt/qqbot/badA.txt</code></pre>
  </div>

  <div class="codeblock">
    <div class="bar"><span>加一个「可疑」词</span><button class="cp">复制</button></div>
<pre><code>echo "新词" &gt;&gt; /opt/qqbot/badB.txt</code></pre>
  </div>

  <div class="codeblock">
    <div class="bar"><span>删掉某个词</span><button class="cp">复制</button></div>
<pre><code>sed -i '/^新词$/d' /opt/qqbot/badA.txt</code></pre>
  </div>

  <div class="box t-red">
    <b>「明确违规」词要选得够狠</b>
    命中它就会<strong>真的禁言</strong>，所以别放「链接」「微信」这种一半正常聊天都会用到的词。
    拿不准的词一律放 <code>badB.txt</code>（只通知你，不动人）。
  </div>

  <h4>你在群里怎么用（只有群主能用）</h4>
  <table>
    <thead><tr><th style="width:38%">你想干什么</th><th>在群里怎么发</th></tr></thead>
    <tbody>
      <tr><td>撤回某条消息</td><td>对那条消息点「<strong>引用</strong>」，再 @它 说「<strong>撤回</strong>」</td></tr>
      <tr><td>禁言某人</td><td>@它 说「<strong>禁言 @某人 10</strong>」（10 是分钟数，不写就按默认 10）</td></tr>
      <tr><td>解除禁言</td><td>@它 说「<strong>解禁 @某人</strong>」</td></tr>
      <tr><td>看谁被记过</td><td>@它 说「<strong>违规记录</strong>」</td></tr>
      <tr><td>把记录清零</td><td>@它 说「<strong>违规清零</strong>」</td></tr>
      <tr><td>忘了指令</td><td>@它 说「<strong>帮助</strong>」</td></tr>
    </tbody>
  </table>

  <div class="box t-blue">
    <b>别人 @ 它说这些词，它一个字都不回</b>
    既不执行，也不会浪费你的模型额度。
  </div>

  <h4>想改禁言时长 / 想退回上一版</h4>
  <div class="codeblock">
    <div class="bar"><span>改成禁言 30 分钟</span><button class="cp">复制</button></div>
<pre><code>sed -i '/^BAN_MINUTES=/d' /opt/qqbot/.env; echo "BAN_MINUTES=30" &gt;&gt; /opt/qqbot/.env; systemctl restart qqbot</code></pre>
  </div>

  <div class="codeblock">
    <div class="bar"><span>退回升级前的版本</span><button class="cp">复制</button></div>
<pre><code>cp -f /opt/qqbot/bot.py.v1bak /opt/qqbot/bot.py; systemctl restart qqbot; echo 已退回</code></pre>
  </div>

  <div class="box t-warn">
    <b>这一节和「只被动回复」的关系</b>
    装完之后它有两个动作会是「主动」的：<strong>群里警告/禁言</strong>、<strong>私聊通知你</strong>。
    这两个都只在你自己的群里、且只在有人违规时才发生，频率很低。<br>
    「不主动加好友、不主动发消息给陌生人」这条底线没有变。
  </div>

  <!-- ============ F-3 ============ -->
  <h3 class="adv"><span class="tag">进阶</span>5-11　让它能联网（问最新比分、新闻、价格不再说「我查不到」）</h3>
  <div class="box t-blue">
    <b>先说清楚它为什么不联网</b>
    这不是它偷懒，是<strong>大模型 API 本身就不带联网</strong>——它只有「训练时读到的东西」，
    没有浏览网页的能力。你之前用的 DeepSeek 那条通道<strong>压根没有搜索这个功能</strong>，
    所以它老老实实说「我拿不到实时数据」，其实比乱编比分靠谱。<br>
    <span class="muted">要让它联网，就得换一条「自带搜索」的通道。智谱就是这个。</span>
  </div>

  <h4>换过去之后有什么变化</h4>
  <table>
    <thead><tr><th style="width:34%">项目</th><th>现在（DeepSeek）</th><th>换成智谱后</th></tr></thead>
    <tbody>
      <tr><td>聊天模型</td><td>收费（很便宜）</td><td><strong>glm-4.7-flash，完全免费</strong></td></tr>
      <tr><td>问「斯诺克最新战况」</td><td>答不了，说没数据</td><td><strong>自动联网查了再答</strong></td></tr>
      <tr><td>联网费用</td><td>—</td><td>¥0.01／次，<strong>只有真要搜才扣</strong></td></tr>
      <tr><td>闲聊</td><td>正常</td><td>正常，<strong>不联网、不花钱</strong></td></tr>
      <tr><td>跟群友聊天的人设</td><td colspan="2">完全不变</td></tr>
    </tbody>
  </table>

  <p class="muted">通俗说：<strong>模型免费，只在它真去搜网页的时候每次收你一分钱。</strong>
  一天问满 100 次实时问题，也就 1 块钱。程序里还设了「每天最多搜 300 次」的闸，超了当天自动停搜。</p>
  <h4>5-11-1　去智谱领一个钥匙（免费，2 分钟）</h4>
  <ol>
    <li>浏览器打开 <code>open.bigmodel.cn</code>（智谱开放平台），用手机号注册 / 登录</li>
    <li>左边菜单点「<strong>API Keys</strong>」（有的页面叫「API 密钥」）</li>
    <li>点「<strong>创建 API Key</strong>」，名字随便填（比如 <code>qqbot</code>）</li>
    <li>复制弹出的那一长串（形如 <code>abc12345.xyz67890</code>）——<strong>只显示一次，先粘到记事本上</strong></li>
  </ol>

  <div class="box t-warn">
    <b>这串东西就是你 5-11-2 要填的「智谱 Key」</b>
    别发群里、别发给我，粘到服务器上就行。
  </div>
  <h4>5-11-2　把供应商改成智谱（三行，按顺序粘）</h4>
  <p>下面三段<strong>一行一行粘</strong>。第 3 段里那串英文<strong>要换成你刚复制的钥匙</strong>，别的字都别动。</p>
  <div class="codeblock">
    <div class="bar"><span>① 改成智谱的地址</span><button class="cp">复制</button></div>
<pre><code>sed -i '/^LLM_BASE_URL=/d' /opt/qqbot/.env; printf 'LLM_BASE_URL=%s\n' "https://open.bigmodel.cn/api/paas/v4" &gt;&gt; /opt/qqbot/.env; echo "===== 地址 OK ====="</code></pre>
  </div>
  <div class="codeblock">
    <div class="bar"><span>② 换成免费的智谱模型</span><button class="cp">复制</button></div>
<pre><code>sed -i '/^LLM_MODEL=/d' /opt/qqbot/.env; printf 'LLM_MODEL=%s\n' "glm-4.7-flash" &gt;&gt; /opt/qqbot/.env; echo "===== 模型 OK ====="</code></pre>
  </div>
  <div class="codeblock">
    <div class="bar"><span>③ 填你的智谱钥匙（把引号里那串换成你自己的）</span><button class="cp">复制</button></div>
<pre><code>sed -i '/^LLM_API_KEY=/d' /opt/qqbot/.env; printf 'LLM_API_KEY=%s\n' "这里换成你的智谱Key" &gt;&gt; /opt/qqbot/.env; echo "===== 钥匙 OK ====="</code></pre>
  </div>
  <div class="box t-red">
    <b>第 ③ 行一定要改</b>
    把 <code>这里换成你的智谱Key</code> 这整串换掉，<strong>两边的双引号留着</strong>。改成这样才对：<br>
    <code>printf 'LLM_API_KEY=%s\n' "abc12345.xyz67890" >> /opt/qqbot/.env; echo "===== 钥匙 OK ====="</code>
  </div>
  <h4>5-11-3　换上带联网功能的新程序（6 段）</h4>
  <p>先粘下面这一行<strong>做备份</strong>：</p>
  <div class="codeblock">
    <div class="bar"><span>准备</span><button class="cp">复制</button></div>
<pre><code>cd /opt/qqbot &amp;&amp; cp -f bot.py bot.py.v2bak &amp;&amp; rm -f b64.txt &amp;&amp; echo "===== 准备完成 ====="</code></pre>
  </div>
  <p>然后从第 1 段粘到第 6 段，<strong>每段粘完等屏幕上出现「完成」字样再粘下一段</strong>。
  这些是机器码，看不懂没关系，原样粘就行。</p>
  <div class="codeblock">
    <div class="bar"><span>5-11-3-1　第 1 段</span><button class="cp">复制</button></div>
<pre><code>printf '%s' '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' &gt;&gt; b64.txt &amp;&amp; echo "===== 1/6 完成 ====="</code></pre>
  </div>

  <div class="codeblock">
    <div class="bar"><span>5-11-3-2　第 2 段</span><button class="cp">复制</button></div>
<pre><code>printf '%s' 'OnmilUfV00E2n2x9U0vLqa+lr9pOnTvdjsCTw0RZDePGke/4AbC3THHEYRdAFw07gtzpLmiwHsySxxqRRRxtasWJz51t9vAs1+ziVGavj4XiL78UNqfRnhOIxcdjpaejlIpg4vau3Y983dTWKp092+LbbKcZ9uYbAvovCPmg8NfPjtTWImQKsLS2jkaCmFPYddiuSNNxQEgCz6zMjU6TGBMq/AGm1xeLzzbhC2rcS/lxa+Jf1LJGIm3nWpqlJqGSDemSU00Jc9hkrG3fulpcXqMICv8dvyaUnj+25qfQUpP1U3BHq4E7yoHjjT8BBx5A8Qn4KlO8H0AJ+WVFoEOyribQaoPUUnp8WWmonMqm3bFMRCoOZnI8YCgp9glBmqki4qPRTUIOo6hSH8W69O+9hbVSfiZy7ORx6etTbceRs6KifW0FRBi3nFILn0pPHsELeeK2Hd/tjUt7d17hk7WxBipWdGxaRuuNHpSZOcvpyFjopSDD9+BDVDzwzaED2UMHUsKBvzccONlwAMQjLhyU4yCgA0Zf41l9QEFgfz/RfhYQ47wYsHstp479A9G9MBI5dkZqa4ZHXUl0a9kcOB1RXexIHjvTkPy/js7Ogx2dIor1lyGjkh3Jt6PgvE5EOzuMg9G/Ndh3V+3Nue8NbUDvVmJ/g8ZkA4hjJz7pSk9S6jgEz6lPsKOj8+0oONGTsU4RnbDECUC2pYngCli1NR9rbsXnZGfkdHPr8ROtX9EOcPK/g6daR+DpH7hdM6VlUFkTdbVC8cm14g/PwW0s7eyAV2svvLHW0J0EnbZ3ecaaA29/kvs2IrUdQ9iiKTYIoMlhL5rgKdkJD0fJwwjbE0lX5JQ0pOkpI4qcxHZHGzApovhi6ufLbg/6RdTlwuEhHhc4pEKP101C9ZdJqwpqQF8XAQlTYXfANeNctCHXQxvyO2hBgGwFCTkHeKaiQxSiMtyt5MD3bW/WdU0vf5WTDYP3sOBLRhx9IKMYUTaBqiGehGEJs1KggBp2HBKA4kkgd6fwuVBXy3md2NwEzY0eUlPtFfMOOxo+7KhvmEmGwaw80tDDkO4DY2Iqwya48giDYZ+h2EO740u4XvQQbgsZ28A7xUOu0wHd8OglM5vWg0OrpioRHxNb67P2DdAtr6znt6yLT3kepSoB1oo6inETc44Z0n+a8RhiOEECp4r2eFihmfwPAqPyV+wLhgcjqSEPKjyWWte3YRia2RzQGIcIn0AUA69iCPbQjLpf3N8KCOqpgWwuCpOCHsSvjAFdkWSjO51u/BJdvzJ/gDnQlVxG7lboNESiQ1eMUynlqVA1i2CzcZdWXpReror0Y5iORBRN6BijmLr7RW1bHPQXM17tnm5mz2h/66mzJ778hiq79nPtzce9oBx7RgaXzf8FMSWbCmgrsb62/rNDdbWHauuJlwtNdfWOAutC2vSmU3FhIJ1iu9IP4MUDxvcHDFE4IJR7q8gxVcFJk0gE8bHJmmmIFQdNGCuLuin8j+A4Q53O146ygSEUIvk+2Y+yCt2OssgolHTtMVAUn9bWcqoCZ+7vJ9IG0S4blWyog0GdXqagqOW0XLQfcEOxY4tw+dTZHQqEF1JEAPBxbDL6IFK3NgC22EfEcDpxUMKJFUb3avRzECEejqT14FfeiNf1HmEyymlkIjAWZCxwhOthgH1I95yXtH53bqoFA3zhR5EN24+ip8zsMEZtDBbzGb+NDGsimaSRfkA5wdHajBNoF7LC4WqswIaF8gJDJ8gMDA/0mfxKmfcEfZk4v4KWdC2TkVLyeccMmhq8OPQJem6iSy0i6JQliBzHhI8a6dflBZAxSdqP5CHd/l6VdNW6zWUuLysOMtThAub/ZpQe08GaWwZPnKw8HAXnKBCPHiJRD7cCVcStjvlmQA/7PTOEw/GCycp6fyUwHhqEAwNjUxd5D2FcHW+9/tWbkpgubE3ZN1eFA6ka8LuBJ4hclKcNUoeg7+EnlkmH2AcCb56DSG5SoEtFR8yI' &gt;&gt; b64.txt &amp;&amp; echo "===== 2/6 完成 ====="</code></pre>
  </div>

  <div class="codeblock">
    <div class="bar"><span>5-11-3-3　第 3 段</span><button class="cp">复制</button></div>
<pre><code>printf '%s' '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' &gt;&gt; b64.txt &amp;&amp; echo "===== 3/6 完成 ====="</code></pre>
  </div>

  <div class="codeblock">
    <div class="bar"><span>5-11-3-4　第 4 段</span><button class="cp">复制</button></div>
<pre><code>printf '%s' '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' &gt;&gt; b64.txt &amp;&amp; echo "===== 4/6 完成 ====="</code></pre>
  </div>

  <div class="codeblock">
    <div class="bar"><span>5-11-3-5　第 5 段</span><button class="cp">复制</button></div>
<pre><code>printf '%s' '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' &gt;&gt; b64.txt &amp;&amp; echo "===== 5/6 完成 ====="</code></pre>
  </div>

  <div class="codeblock">
    <div class="bar"><span>5-11-3-6　第 6 段</span><button class="cp">复制</button></div>
<pre><code>printf '%s' 'Cr/5UPm++r4OPF0wnANJrnSFz4axCsa0aL7d+Jv8eAO7MFV5evxNr/JttIrDmG/Qk0gB+Gisoep5dg9mvVl6Axz32B9be4UArJEEYKYsKYMkw/THgFfdZcpR3qBwX7tMbGB9ZcCUy2mhJT1lu7y5t7DIG8N6jzWs984buA8XuC3YndEM/jh/H1aalV6jOrFvPAcdAHYW1bXfOGPelf5636f46yZgcsHTge/EsNNl5xjFyChKLvopqjf82TYHFG6iJKGakyS2hc4X+oAapfovFvl/AmME0k1SAAA=' &gt;&gt; b64.txt &amp;&amp; echo "===== 6/6 完成 ====="</code></pre>
  </div>

  <p>6 段都粘完，最后粘这一行<strong>让它生效</strong>：</p>
  <div class="codeblock">
    <div class="bar"><span>安装并重启</span><button class="cp">复制</button></div>
<pre><code>base64 -d b64.txt | gunzip &gt; bot.py &amp;&amp; python3 -c "import ast;ast.parse(open('/opt/qqbot/bot.py',encoding='utf-8').read());print('语法OK')" &amp;&amp; rm -f b64.txt &amp;&amp; systemctl restart qqbot &amp;&amp; sleep 2 &amp;&amp; systemctl is-active qqbot &amp;&amp; echo "===== 5-11 完成 ====="</code></pre>
  </div>
  <div class="box t-warn">
    <b>看到这两行就成了</b>
    <code>语法OK</code> 和 <code>active</code>，最后跟着 <code>===== 5-11 完成 =====</code>。<br>
    它会先把你现在的程序备份成 <code>bot.py.v2bak</code>，出问题可以一键退回去。
  </div>
  <h4>5-11-4　怎么验证联网真的生效了</h4>
  <ol>
    <li>用你的大号<strong>私聊</strong>小号，发：<code>斯诺克最近有什么比赛</code></li>
    <li>再发一句闲聊：<code>讲个冷笑话</code>（这句不该联网）</li>
    <li>在你群里 @ 它，问同样的问题</li>
    <li>（群主专用）在群里 @ 它 说「<strong>联网</strong>」→ 它会回你今日已用几次</li>
  </ol>

  <div class="box t-blue">
    <b>怎么判断它这次到底搜没搜</b>
    最容易看的是它回答里有没有「根据最新报道」这类说法、有没有具体日期。
    另外你可以随时 @ 它 说「联网」，看今日用量有没有涨。<br>
    <span class="muted">闲聊、答题、写文案这类不需要实时信息的，它不会去搜，也就不扣钱。</span>
  </div>
  <h4>想调一调（可选）</h4>
  <div class="codeblock">
    <div class="bar"><span>把每天联网上限改成 100 次（默认 300）</span><button class="cp">复制</button></div>
<pre><code>sed -i '/^SEARCH_DAILY_MAX=/d' /opt/qqbot/.env; echo "SEARCH_DAILY_MAX=100" &gt;&gt; /opt/qqbot/.env; systemctl restart qqbot; echo 改好了</code></pre>
  </div>
  <div class="codeblock">
    <div class="bar"><span>临时关掉联网（模型照常用，就是不再搜）</span><button class="cp">复制</button></div>
<pre><code>sed -i '/^SEARCH=/d' /opt/qqbot/.env; echo "SEARCH=off" &gt;&gt; /opt/qqbot/.env; systemctl restart qqbot; echo 已关联网</code></pre>
  </div>
  <div class="codeblock">
    <div class="bar"><span>再打开联网</span><button class="cp">复制</button></div>
<pre><code>sed -i '/^SEARCH=/d' /opt/qqbot/.env; echo "SEARCH=on" &gt;&gt; /opt/qqbot/.env; systemctl restart qqbot; echo 已开联网</code></pre>
  </div>
  <table>
    <thead><tr><th style="width:34%">搜索引擎</th><th>特点</th><th>价格</th></tr></thead>
    <tbody>
      <tr><td><code>search_std</code>（默认）</td><td>智谱自研基础版，够用、快</td><td>¥0.01／次</td></tr>
      <tr><td><code>search_pro</code></td><td>多引擎协作，召回更全</td><td>¥0.03／次</td></tr>
      <tr><td><code>search_pro_sogou</code></td><td>搜狗引擎，微信 / 知乎内容多</td><td>¥0.05／次</td></tr>
      <tr><td><code>search_pro_quark</code></td><td>夸克引擎，时效性强</td><td>¥0.05／次</td></tr>
    </tbody>
  </table>

  <div class="codeblock">
    <div class="bar"><span>换成 search_pro（更全，贵 2 分钱）</span><button class="cp">复制</button></div>
<pre><code>sed -i '/^SEARCH_ENGINE=/d' /opt/qqbot/.env; echo "SEARCH_ENGINE=search_pro" &gt;&gt; /opt/qqbot/.env; systemctl restart qqbot; echo 已切换</code></pre>
  </div>
  <h4>万一不顺利</h4>
  <table>
    <thead><tr><th style="width:40%">症状</th><th>怎么办</th></tr></thead>
    <tbody>
      <tr><td>日志里刷 <code>接口报错 401</code></td><td>钥匙填错了。回 5-11-2 第 ③ 行重填一次</td></tr>
      <tr><td>日志里刷 <code>接口报错 404</code> 或提示模型不存在</td><td>把这行粘上，换个备用模型：<br>
          <code>sed -i '/^LLM_MODEL=/d' /opt/qqbot/.env; echo "LLM_MODEL=glm-4-flash" &gt;&gt; /opt/qqbot/.env; systemctl restart qqbot</code></td></tr>
      <tr><td>能看到 <code>联网工具不可用，本次改为不联网回答</code></td><td>这个模型不支持联网，换成 <code>glm-4.7-flash</code> 或 <code>glm-4-flash</code></td></tr>
      <tr><td>回「我这边有点忙，稍后再问我一次」，日志里有 <code>1305</code></td><td>智谱<strong>免费档全平台拥堵</strong>，不是你的问题。<br>
          ① 等几分钟再问；② 换收费但极便宜的版本（约 5 毛／百万字，基本不排队）：<br>
          <code>sed -i '/^LLM_MODEL=/d' /opt/qqbot/.env; echo "LLM_MODEL=glm-4.7-flashx" &gt;&gt; /opt/qqbot/.env; systemctl restart qqbot</code></td></tr>
      <tr><td>还是答「我查不到」</td><td>先 @ 它 说「联网」看今天次数还有没有；用完了等明天自动恢复</td></tr>
      <tr><td>整个机器人不回话了</td><td>一键退回上一版（下面第一条命令）</td></tr>
    </tbody>
  </table>

  <div class="codeblock">
    <div class="bar"><span>退回换联网之前的那一版（v2）</span><button class="cp">复制</button></div>
<pre><code>cp -f /opt/qqbot/bot.py.v2bak /opt/qqbot/bot.py; systemctl restart qqbot; echo 已退回</code></pre>
  </div>

  <div class="codeblock">
    <div class="bar"><span>整体退回 DeepSeek（连地址和模型一起换回来）</span><button class="cp">复制</button></div>
<pre><code>sed -i '/^LLM_BASE_URL=/d' /opt/qqbot/.env; printf 'LLM_BASE_URL=%s\n' "https://api.deepseek.com/v1" &gt;&gt; /opt/qqbot/.env; sed -i '/^LLM_MODEL=/d' /opt/qqbot/.env; printf 'LLM_MODEL=%s\n' "deepseek-flash" &gt;&gt; /opt/qqbot/.env; systemctl restart qqbot; echo 已换回 DeepSeek</code></pre>
  </div>

  <div class="box t-blue">
    <b>退回之后会怎样</b>
    机器人照常聊天、照常管违规，只是<strong>不再联网</strong>，回到「问实时问题它说不知道」的状态。
    你的群、违规记录、人设这些都不会丢。
  </div>

  <div class="box t-warn">
    <b>关于钱</b>
    模型（glm-4.7-flash）本身免费，<strong>唯一的开销就是联网搜索</strong>，每次一分钱。
    程序默认每天最多 300 次（上限 3 元），到顶当天自动停搜，第二天自动恢复。
    你随时可以 @ 它 说「联网」查当天用了多少次。
  </div>

  <!-- ============ 附录 E END ============ -->

</div>

<script>
  function copyText(t) {
    return new Promise(function (res, rej) {
      if (navigator.clipboard && window.isSecureContext) {
        navigator.clipboard.writeText(t).then(res, rej);
      } else {
        var a = document.createElement('textarea');
        a.value = t;
        a.style.position = 'fixed';
        a.style.top = '0';
        a.style.left = '0';
        a.style.opacity = '0';
        document.body.appendChild(a);
        a.focus(); a.select();
        a.setSelectionRange(0, t.length);
        var ok = false;
        try { ok = document.execCommand('copy'); } catch (e) { ok = false; }
        document.body.removeChild(a);
        ok ? res() : rej(new Error('execCommand failed'));
      }
    });
  }

  document.querySelectorAll('.cp').forEach(function (b) {
    var timer = null;
    b.addEventListener('click', function () {
      var box = b.closest('.codeblock');
      var pre = box.querySelector('pre');
      var t = pre.innerText.replace(/\s+$/, '');

      // 无论如何先把文字选中，这样即使复制失败，用户也能直接按 Ctrl+C
      try {
        var r = document.createRange();
        r.selectNodeContents(pre);
        var s = window.getSelection();
        s.removeAllRanges();
        s.addRange(r);
      } catch (e) {}

      copyText(t).then(function () { flash('已复制 ✓'); },
                        function () { flash('已选中，请按 Ctrl+C'); });
    });

    function flash(msg) {
      if (timer) clearTimeout(timer);
      b.textContent = msg;
      b.classList.add('ok');
      timer = setTimeout(function () {
        b.textContent = '复制';
        b.classList.remove('ok');
      }, 1800);
    }
  });
</script>
