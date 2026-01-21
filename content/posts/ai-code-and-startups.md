---
title: "AI, Code, and Startups"
date: 2026-01-21
draft: false
tags: ["AI", "Vibe Coding", "Web开发", "Startups"]
---

## Coding

### AI Sucks at UI Design

最新的模型在后端编程上提升极大，但涉及到视觉层面，如UI设计，Opus 4.5并没有太大突破。AI生成的UI都是一个味儿：蓝紫配色+渐变+大圆角+阴影+毛玻璃+动画，AI味太重了。

<!--more-->

就算你在Figma画好了设计图，让AI严格按照设计稿执行，最终效果也完全谈不上还原。目前如果想让AI做前端，最好还是让它使用组件库，选一个Material Design风格的，可以最大程度避免AI味UI。

我相信准确还原UI设计这个问题很快会被解决。Figma有个MCP，或许能解决这个问题，不过我还没试过。

### Web Devs Are Panicking

一些前端程序员对AI和Vibe Coding很反感，可能是触发了existential crisis。毕竟前端程序员约等于JS程序员，JS门槛低，训练资料多，AI能发挥的作用也就更大。自然，你写JS的话也就更容易被AI替代。

不仅是JS开发者，整个web dev工作的很大一部分都可被Agent自动化，无论是写Go、Rust还是Ruby。Web dev抽象来说就是CRUD、字符串处理和API调用。之前看r/webdev，总能看见shit on AI的帖子，现在估计更严重。

[Don't Fall into the Anti-AI Hype](https://antirez.com/news/158) by Salvatore Sanfilippo，Redis作者。

### Let AI Produce Good Code

以我最近让Opus写的一个Rust微服务的Rules为例。第一条规则永远是让AI遵守一个style guide。如果你用的语言有Google style guide就用Google的，没有就用官方的。比如"严格遵守Rust官方的Rust Style Guide"。这样可以保证AI不会生成有异味的代码。第二条规则是让AI"遵守DRY、KISS、YAGNI等编程原则"。

之后的规则是为了避免AI到处拉屎，导致仓库AI味过重：

- 编写简单可靠的测试
- 仅对必要的地方进行测试
- 仅在必要的地方进行注释
- 如果代码本身已显而易见，则不需要注释解释功能
- 不得在代码注释、程序输出、文档、Git提交等任何地方使用Emoji
- 每实现一个功能或模块就进行一次Git提交，避免大提交
- 保证Git commit信息简短，只进行概括，保持在20词以内
- Git commit必须遵守Conventional Commits规范

还有最重要的一条：禁止AI生成多余的Markdown文档。默认情况下AI可能在每完成一个任务后生成一份总结文档，浪费token。

除了详细的规则文件，还需要一个详细的初始prompt。在prompt里一定要说明技术栈，列出要用哪些库，详细描述应用逻辑和交互逻辑，最大程度避免AI瞎编。

### Move Fast and Break Things

你的web app不需要太多测试，特别是单元测试，尽量不要让AI编写单元测试。我知道AI编写单元测试很轻松，但它写的测试大多没有意义，只会占用context和增加维护成本。

既然已经选择Vibe Coding，维护的肯定不是什么mission critical的金融级代码库。对于面向用户的web app，完全可以编写最少量的必要测试，然后test in production。当然，前提是你的公司或startup有一个完整的上线流程。

比如一个新的vibe coded微服务上线后，先给一小部分流量，观察是否有问题，没问题就缓慢提升流量直到100%。即使程序出现问题，也只会影响一小部分用户，对大部分业务来说这是可以接受的。

分享一条Tweet：

> **In my 5 years at FB (infra/ops) I've never written a single test. It was cheaper to test in prod and forward fix.**
>
> @ptashek_eire [Source](https://web.archive.org/web/20220722144711/twitter.com/ptashek_eire/status/1550492213334925313)

### How to Spot Vibe Coded Project

现在GitHub充斥着用AI写的项目，我经常在HN首页看到AI写的开源项目，排名还很高。但质量嘛……这些项目通常不会有太多维护，AI生成完就晾在那了。除非项目维护者是有声望的开发者，例如Armin Ronacher（Flask作者，最近沉迷Vibe Coding），一定要避坑。

这类AI生成项目有以下特征：

- Commit少，且初始commit特别大
- Emoji everywhere，这是最明显的特征
- Markdown files everywhere，且文档包含明显的AI特征，如em dash
- README又臭又长
- 代码注释过多
- Commit message风格不一致，有的commit符合规范，有的则是"efefe"这样的滚键盘
- 包含claude.md，这个是最明显的
- README包含过多promotional language
- more...

如果这些特征都没发现，也不能百分之百保证没有AI介入，但项目作者至少有点taste，知道处理AI痕迹。那我觉得倒是可以考虑使用这个项目。

不是说不能用AI写的开源项目，如果是一些高质量的库倒是可以用。但不要用AI写的大项目，除非你自己去code review一遍。我相信这种大项目作者本人可能都没看过代码。

## Startups

### Idea Matters Most

现在可能是最适合独立开发的时代，从idea到验证的时间被极大压缩。当然，如果每个独立开发者都用AI提升上线效率，那么竞争会更激烈，好想法会更快被别人做出来，现有产品也会更快被抄袭。最重要的是，新产品会被其它同样vibe code出来的产品淹没，难以脱颖而出。AI虽然提升了效率，但也加剧了竞争。

做产品可以简化成三个流程：最初的灵感 (构思、设计、规划）、实现（Coding）、宣传推广。以前，中间那部分是最重要也是决定成败的，因为Web 2.0时期编程门槛还很高，所以execution才会被如此看重，才有了"execution is everything"这句话。现在AI agent时代，可以基本忽略中间部分，专注于灵感和推广，因为这两个阶段才是最重要的。**Execution doesn't matter.**

### Do Things that Don't Scale

如果一个产品scales well，这个产品的开发成本和运营成本都不会太高，那肯定已经被别人做过了。如果没人做，那就是伪需求，或需求过低，不值得去做。什么样的产品scale well？各种AI wrapper，各种Chat WebUI，开发成本低，运营成本也低，直接接入OpenRouter API就好。所以，在这样充满竞争对手的赛道上，别人为什么选择你的Chat UI？

什么样的产品don’t scale well？举个粗俗的例子，做一个AI视频去码网站。有实际需求，有流量。但开发成本和运营成本太高。这样的产品don’t scale well，但是并不是不可能去做，如果你做了就不会有多少竞争对手。

### Don't Make Trash

因为AI让开发变简单，导致很多trash idea被实现出来。Product Hunt和Show HN堆满了无用的垃圾产品。

被spam最严重的是V2EX分享创造节点，每天都能看见几个高度SEO的垃圾站。都算不上产品，就是AI写的HTML，就一个页面，美其名曰信息站，里面的信息全是AI生成的。当Google傻吗？而且Google已经在给自家用户喂AI overview了，就算能获得排名，用户第一个看到的也是Google的AI。SEO已死，怎么还有人做这种垃圾站？记得之前的小X知识网吗？

话说，我高度怀疑这些垃圾站是某位"SEO guru"的学生做的，具体是谁就不说了。

### When Not to Use AI

**不要在写作上用AI**，无论是Reddit post、blog post等等。可以用AI去做翻译，让它忠实翻译，并且告诉它不要用em dash。但不要让AI完全生成一篇文章。

**不要用AI生成任何宣传图**，现阶段纯AI生成的图片太过明显，你的用户一眼就知道是AI slop。

我在HN上连续看了两个上首页的帖子，两个项目不仅全是AI写的，就连HN post都是AI写的。最不尊重人的是，连回复的评论都是AI写的。发帖者连掩饰都不做，回复存在"You are absolutely right"这种明显的Claude痕迹，严重怀疑都是一些阿三在发这种spam。

V站也有这种AI发帖的情况。这样做太不尊重人，太没有诚意了。连回复都要AI生成，要么是太懒，要么是太无能连回复都不会写。

### AI Is Killing SaaS

不要做micro SaaS，可替代性极强，AI可以轻易复制。客户完全可以用AI开发一个本地版，更过分的甚至可以开源。2C的SaaS不用想了，普通消费者恨死订阅制了。2B的SaaS复杂点还能做，但如果你的SaaS面向软件公司，早晚他们会自己用AI做一个替代品。
