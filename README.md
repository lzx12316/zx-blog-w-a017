# 在线BLOG网

> 🎓 **计算机毕业设计 · 在线BLOG网**
>
> 本仓库只放**项目介绍 + 运行截图**（截图是站点带水印的原图，存在仓库 `images/` 里）。
>
> 👉 **完整可运行源码 / 数据库脚本 / 部署文档：[点我获取](https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github)**
>
> 💬 咨询微信：**ir9372**　|　🌐 更多项目：[极客代码 geekcode.top](https://geekcode.top/?utm_source=github)
>
> 📌 项目详情页：<https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github>


<table><td width="230" align="center"><a href="https://geekcode.top/?utm_source=github"><img src="images/35.jpg" alt="微信名片" width="220"></a><br><b>扫码加微信 ir9372</b></td><td valign="middle">📦 源码 = 项目介绍 + 全部运行截图 + 数据库 + 部署文档<br>👉 点上方任意截图，直接跳到 <b>极客代码 geekcode.top</b> 详情页</td></table>

---

<h1>在线BLOG网</h1>
<h2>项目概述</h2>
<p>本项目名为“在线BLOG网”，是一个基于 Spring Boot 与 MyBatis-Plus 技术栈构建的综合性内容管理与社区交流平台。系统采用前后端分离或集成架构，包含前台用户展示端与后台管理维护端。核心功能涵盖博客文章的发布与管理、图库相册分享、论坛交流互动、新闻资讯推送以及错题本（cuotiben）和考试记录（kaoshijilu）等学习辅助模块。适用人群包括普通注册用户、内容创作者及系统管理员。通过 Shiro 框架实现安全认证与授权，旨在提供一个集信息浏览、社交互动及个人知识管理于一体的 Web 应用平台。</p>
<h2>技术架构</h2>
<h3>后端架构</h3>
<p>系统后端基于 Java 语言开发，主要依赖以下技术组件：</p>
<ul>
<li><strong>Web 框架</strong>：使用 <code>spring-boot-starter-web</code> 构建 RESTful API 接口，处理 HTTP 请求与响应。</li>
<li><strong>持久层框架</strong>：采用 <code>MyBatis-Plus</code> (<code>mybatis-plus</code>, <code>mybatisplus-spring-boot-starter</code>) 作为 ORM 框架，简化单表 CRUD 操作，并配合 <code>mysql-connector-java</code> 连接 MySQL 数据库。</li>
<li><strong>安全框架</strong>：引入 <code>Shiro</code> (<code>shiro-spring</code>) 进行身份验证、会话管理及权限控制，保障系统安全性。</li>
<li><strong>工具类库</strong>：使用 <code>commons-lang3</code> 提供字符串处理等通用功能，<code>validation-api</code> 用于数据校验，<code>protobuf-java</code> 支持高效的数据序列化传输。</li>
<li><strong>控制器层</strong>：代码中定义了多个 Controller，如 <code>BokeController</code>（博客）、<code>ForumController</code>（论坛）、<code>NewsController</code>（新闻）、<code>TukuxiangceController</code>（图库相册）、<code>StoreupController</code>（收藏）等，分别对应不同的业务逻辑模块。</li>
</ul>
<h3>前端架构</h3>
<p>项目类型为 <code>vue-integrated</code>，表明前端界面可能基于 Vue.js 框架构建，并与后端工程集成部署。虽然提供的上下文未列出具体前端路由细节，但根据截图功能列表可知，前端实现了完整的页面交互，包括登录注册、各类内容列表页、详情页以及后台管理界面的动态渲染。</p>
<h3>数据库设计要点</h3>
<p>数据库存储了多类实体数据，依据 Controller 命名推断主要表结构包括：</p>
<ul>
<li><strong>用户相关</strong>：<code>yonghu</code>（用户表），存储账号密码及个人信息。</li>
<li><strong>内容相关</strong>：<code>boke</code>（博客表）、<code>news</code>（新闻表）、<code>lunbotuguanli</code>（轮播图/公告表）。</li>
<li><strong>分类与标签</strong>：<code>bokefenlei</code>（博客分类）、<code>bokebiaoqian</code>（博客标签），用于内容的归类检索。</li>
<li><strong>多媒体资源</strong>：<code>tukuxiangce</code>（图库相册），支持图片上传与展示。</li>
<li><strong>互动数据</strong>：<code>discussboke</code>（博客评论）、<code>discusstukuxiangce</code>（相册评论）、<code>forum</code>（论坛帖子）。</li>
<li><strong>其他业务</strong>：<code>storeup</code>（收藏记录）、<code>adminexam</code>（管理员考试/错题相关数据）、<code>config</code>（系统配置）。</li>
</ul>
<h2>功能模块</h2>
<p>根据后台路由 <code>/news, /lunbotuguanli, /bokebiaoqian, /bokefenlei, /yonghu, /tukuxiangce, /boke, /storeup, /luntanguanli, /adminexam</code> 及截图功能列表，系统主要功能模块如下：</p>
<h3>前台用户端功能</h3>
<ol>
<li><strong>账户体系</strong>：</li>
</ol>
<ul>
<li><strong>登录/注册</strong>：用户可通过前台页面进行账号注册与登录，进入个人中心。</li>
</ul>
<ol start="2">
<li><strong>博客中心</strong>：</li>
</ol>
<ul>
<li><strong>博客浏览</strong>：查看博客列表，支持按分类（<code>bokefenlei</code>）和标签（<code>bokebiaoqian</code>）筛选文章。</li>
<li><strong>博客详情</strong>：阅读完整文章内容，查看作者信息及发布时间。</li>
<li><strong>博客评论</strong>：在博客详情页发表评论内容，并可查看他人的评论列表。</li>
</ul>
<ol start="3">
<li><strong>图库相册</strong>：</li>
</ol>
<ul>
<li><strong>相册浏览</strong>：查看图库相册列表及单个相册详情。</li>
<li><strong>相册评论</strong>：对特定相册或图片进行评论互动。</li>
</ul>
<ol start="4">
<li><strong>论坛社区</strong>：</li>
</ol>
<ul>
<li><strong>论坛发帖与浏览</strong>：访问论坛列表，查看话题详情，参与讨论。</li>
</ul>
<ol start="5">
<li><strong>资讯与公告</strong>：</li>
</ol>
<ul>
<li><strong>新闻资讯</strong>：浏览最新新闻列表及详情。</li>
<li><strong>轮播图/公告</strong>：首页展示系统配置的轮播图或重要公告信息。</li>
</ul>
<ol start="6">
<li><strong>个人学习与记录</strong>：</li>
</ol>
<ul>
<li><strong>错题本（cuotiben）</strong>：查看和管理个人的错题记录列表。</li>
<li><strong>考试记录（kaoshijilu）</strong>：查看历史考试成绩或练习记录。</li>
</ul>
<ol start="7">
<li><strong>收藏管理</strong>：</li>
</ol>
<ul>
<li><strong>我的收藏</strong>：查看已收藏的博客、相册或其他内容列表及详情。</li>
</ul>
<h3>后台管理端功能</h3>
<ol>
<li><strong>系统基础管理</strong>：</li>
</ol>
<ul>
<li><strong>管理员登录</strong>：后台入口需经过身份验证。</li>
<li><strong>首页仪表盘</strong>：展示系统概览信息。</li>
</ul>
<ol start="2">
<li><strong>内容管理</strong>：</li>
</ol>
<ul>
<li><strong>博客管理</strong>：增删改查博客文章，审核评论内容。</li>
<li><strong>分类与标签管理</strong>：维护博客分类树和标签字典，便于前台检索。</li>
<li><strong>图库相册管理</strong>：上传、编辑、删除相册资源及处理相册评论。</li>
<li><strong>新闻管理</strong>：发布和维护新闻资讯内容。</li>
<li><strong>轮播图管理</strong>：配置首页展示的轮播图片或公告栏内容。</li>
</ul>
<ol start="3">
<li><strong>社区管理</strong>：</li>
</ol>
<ul>
<li><strong>论坛管理</strong>：监控论坛帖子，处理违规内容或回复。</li>
</ul>
<ol start="4">
<li><strong>用户与权限管理</strong>：</li>
</ol>
<ul>
<li><strong>用户管理</strong>：查看注册用户信息，执行启用、禁用或重置密码等操作。</li>
</ul>
<ol start="5">
<li><strong>业务数据统计与维护</strong>：</li>
</ol>
<ul>
<li><strong>收藏管理</strong>：查看用户的收藏行为数据。</li>
<li><strong>考试/错题管理（adminexam）</strong>：针对错题本或考试记录模块的管理功能，可能涉及题目维护或成绩统计。</li>
</ul>
<h2>用户角色与权限</h2>
<p>系统主要划分为两类角色，基于 Shiro 框架进行权限隔离：</p>
<ol>
<li><strong>普通用户（Registered User）</strong></li>
</ol>
<ul>
<li><strong>权限范围</strong>：仅拥有前台访问权限。</li>
<li><strong>核心能力</strong>：</li>
<li>注册新账号并登录。</li>
<li>浏览所有公开的内容（博客、新闻、相册、论坛）。</li>
<li>进行互动操作：发表评论、点赞（若隐含）、收藏内容。</li>
<li>管理个人数据：查看自己的收藏列表、错题本、考试记录。</li>
<li><strong>限制</strong>：无法访问后台管理路径，不能修改或删除他人发布的内容。</li>
</ul>
<ol start="2">
<li><strong>系统管理员（Admin）</strong></li>
</ol>
<ul>
<li><strong>权限范围</strong>：拥有最高权限，可访问后台管理系统及部分前台特殊视图。</li>
<li><strong>核心能力</strong>：</li>
<li><strong>全量内容管控</strong>：对所有博客、新闻、相册、论坛帖子进行创建、编辑、删除操作。</li>
<li><strong>元数据维护</strong>：管理博客分类、标签、轮播图等基础配置项。</li>
<li><strong>用户治理</strong>：查看所有用户信息，管理用户状态。</li>
<li><strong>互动审核</strong>：审查和处理来自用户的评论内容。</li>
<li><strong>业务配置</strong>：管理错题本或考试相关的后台数据（adminexam 模块）。</li>
</ul>
<h2>项目特色与创新点</h2>
<ol>
<li><p><strong>多元化内容形态融合</strong>：
   不同于单一的博客系统，本项目集成了图文博客、图片相册、文本论坛、新闻资讯等多种内容形态，满足了用户从深度阅读到碎片化浏览的不同需求。</p>
</li>
<li><p><strong>嵌入式学习辅助功能</strong>：
   在传统 CMS 基础上，创新性地引入了“错题本（cuotiben）”和“考试记录（kaoshijilu）”模块。这使得平台不仅是一个社交分享空间，更具备个人知识管理和自我提升的工具属性，特别适用于学生群体或终身学习者。</p>
</li>
<li><p><strong>精细化的内容组织体系</strong>：
   通过独立的“博客分类”和“博客标签”管理模块，构建了二维的内容索引体系。这种设计提高了海量内容下的检索效率，增强了用户体验。</p>
</li>
<li><p><strong>安全的权限控制机制</strong>：
   采用 Apache Shiro 框架替代简单的拦截器，提供了更为成熟和细粒度的认证与授权方案，有效保障了用户隐私数据（如考试记录、收藏）的安全性以及后台管理操作的规范性。</p>
</li>
</ol>
<h2>部署环境</h2>
<p>为确保“在线BLOG网”正常运行，服务器及客户端需满足以下软件环境要求：</p>
<ol>
<li><strong>Java 运行环境 (JDK)</strong>：</li>
</ol>
<ul>
<li>建议版本：JDK 1.8 或以上。Spring Boot 和 MyBatis-Plus 均高度兼容 JDK 8+。</li>
</ul>
<ol start="2">
<li><strong>数据库系统</strong>：</li>
</ol>
<ul>
<li>类型：MySQL。</li>
<li>版本：建议 MySQL 5.7 或 MySQL 8.0。</li>
<li>驱动：项目依赖 <code>mysql-connector-java</code>，需确保驱动版本与数据库服务端版本兼容。</li>
</ul>
<ol start="3">
<li><strong>Web 容器/应用服务器</strong>：</li>
</ol>
<ul>
<li>内置 Tomcat：由于使用 <code>spring-boot-starter-web</code>，项目打包为 Jar 包后可直接内嵌 Tomcat 运行，无需单独安装外部 Tomcat。</li>
</ul>
<ol start="4">
<li><strong>前端运行环境</strong>：</li>
</ol>
<ul>
<li>Node.js：鉴于项目类型为 <code>vue-integrated</code>，若需本地编译前端代码或运行 Vue CLI 服务，需安装 Node.js（建议 LTS 版本，如 v14.x 或 v16.x+）。</li>
<li>浏览器：支持 Chrome、Firefox、Edge 等主流现代浏览器。</li>
</ul>
<ol start="5">
<li><strong>构建工具</strong>：</li>
</ol>
<ul>
<li>Maven：用于管理 Java 依赖和项目构建（根据标准 Spring Boot 项目结构推断）。</li>
</ul>
<ol start="6">
<li><strong>操作系统</strong>：</li>
</ol>
<ul>
<li>Windows Server, Linux (CentOS/Ubuntu), macOS 均可。</li>
</ul>
<h2>五、技术特性</h2>
<ul>
<li>前后端集成部署，前端资源打包至后端 static 目录</li>
<li>使用 MyBatis-Plus 简化数据访问层开发</li>
<li>集成 Shiro 权限框架实现角色权限控制</li>
</ul>
<h2>六、功能模块截图</h2>
<h3>前台用户端</h3>
<h4>前台登录页</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/01.jpg" alt="前台登录页"></a></p>
<h4>前台注册页</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/02.jpg" alt="前台注册页"></a></p>
<h4>前台-博客列表</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/03.jpg" alt="前台-博客列表"></a></p>
<h4>前台-博客标签列表</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/04.jpg" alt="前台-博客标签列表"></a></p>
<h4>前台-博客分类列表</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/05.jpg" alt="前台-博客分类列表"></a></p>
<h4>前台-错题本</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/06.jpg" alt="前台-错题本"></a></p>
<h4>前台-博客评论列表</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/07.jpg" alt="前台-博客评论列表"></a></p>
<h4>前台-图库相册评论列表</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/08.jpg" alt="前台-图库相册评论列表"></a></p>
<h4>前台-论坛列表</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/09.jpg" alt="前台-论坛列表"></a></p>
<h4>前台-考试记录</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/10.jpg" alt="前台-考试记录"></a></p>
<h4>前台-新闻资讯列表</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/11.jpg" alt="前台-新闻资讯列表"></a></p>
<h4>前台-shijianliebiao列表</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/12.jpg" alt="前台-shijianliebiao列表"></a></p>
<h4>前台-收藏列表</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/13.jpg" alt="前台-收藏列表"></a></p>
<h4>前台-图库相册列表</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/14.jpg" alt="前台-图库相册列表"></a></p>
<h4>前台-博客-详情</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/15.jpg" alt="前台-博客-详情"></a></p>
<h4>前台-博客标签-详情</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/16.jpg" alt="前台-博客标签-详情"></a></p>
<h4>前台-博客分类-详情</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/17.jpg" alt="前台-博客分类-详情"></a></p>
<h4>前台-博客评论-详情</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/18.jpg" alt="前台-博客评论-详情"></a></p>
<h4>前台-图库相册评论-详情</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/19.jpg" alt="前台-图库相册评论-详情"></a></p>
<h4>前台-论坛-详情</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/20.jpg" alt="前台-论坛-详情"></a></p>
<h4>前台-考试记录详情</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/21.jpg" alt="前台-考试记录详情"></a></p>
<h4>前台-新闻资讯-详情</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/22.jpg" alt="前台-新闻资讯-详情"></a></p>
<h4>前台-收藏-详情</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/23.jpg" alt="前台-收藏-详情"></a></p>
<h4>前台-图库相册-详情</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/24.jpg" alt="前台-图库相册-详情"></a></p>
<h3>后台管理端</h3>
<h4>后台-博客信息</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/25.jpg" alt="后台-博客信息"></a></p>
<h4>后台-博客标签</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/26.jpg" alt="后台-博客标签"></a></p>
<h4>后台-博客分类</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/27.jpg" alt="后台-博客分类"></a></p>
<h4>后台首页</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/28.jpg" alt="后台首页"></a></p>
<h4>后台-登录</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/29.jpg" alt="后台-登录"></a></p>
<h4>后台-轮播图管理</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/30.jpg" alt="后台-轮播图管理"></a></p>
<h4>后台-luntanguanli</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/31.jpg" alt="后台-luntanguanli"></a></p>
<h4>后台-公告信息</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/32.jpg" alt="后台-公告信息"></a></p>
<h4>后台-收藏</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/33.jpg" alt="后台-收藏"></a></p>
<h4>后台-图库相册</h4>
<p><a href="https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github" title="查看完整源码"><img src="images/34.jpg" alt="后台-图库相册"></a></p>

---

## 获取完整源码

| 项目 | 说明 |
| --- | --- |
| 项目名 | 在线BLOG网 |
| 运行截图 | 本文 34 张（站点带水印原图，仓库 `images/` 目录） |
| 完整源码 | [https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github](https://geekcode.top/archives/%E5%9C%A8%E7%BA%BFBLOG%E7%BD%91?utm_source=github) |
| 咨询微信 | **ir9372**（备注：jingpin-yuanma） |
| 更多项目 | [极客代码 geekcode.top](https://geekcode.top/?utm_source=github) |

> 需要源码、部署、改配置、跑不起来等问题，加微信 ir9372 沟通，说明项目名即可。
