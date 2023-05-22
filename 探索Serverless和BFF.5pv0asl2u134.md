原文链接：[https://juejin.cn/post/6844903844745330695](https://juejin.cn/post/6844903844745330695)
## 前端开发模式的演进
首先回顾一下前端开发模式的演进，我觉得主要有四个阶段。

1. 基于模板渲染的动态页面
2. 基于 AJAX 的前后端分离
3. 基于 Node.js 的前端工程化
4. 基于 Node.js 的全栈开发
### 基于模板渲染的动态页面
在早起的互联网时代，我们的网页很简单，就是一些静态或动态的页面，主要目的是用来做信息的展示和传播。这个时候开发一个网页也很容易，主要就是通过 JSP、PHP 等技术写一些动态模板，然后通过 Web Server 将模板解析成一个个 HTML 文件，浏览器只负责渲染这些 HTML 文件。这个阶段还没有前后端的分工，通常是后端工程师顺便写了前端页面。
### 基于 AJAX 的前后端分离
2005 年 AJAX 技术的正式提出，翻开了 Web 开发的新篇章。基于 AJAX，我们可以把 Web 分为前端和后端，前端负责界面和交互，后端负责业务逻辑的处理。前后端通过接口进行数据交互。我们也不再需要在各个后端语言里面写着难以维护的 HTML。网页的复杂度也由后端的 Web Server 转向了浏览器端的 JavaScript。也正因如此，开始有了前端工程师这个职位。
### 基于 Node.js 的前端工程化
2009年 Node.js 的出现，对于前端工程师来说，也是一个历史性的时刻。随着 Node.js 一同出现的还有 CommonJS 规范和 npm 包管理机制。随后也出现了 Grunt、Gulp、Webpack 等一系列基于 Node.js 的前端开发构建工具。
在 2013 年前后，前端三大框架 React.js/Angular/Vue.js 相继发布第一个版本。我们可以从以往基于一个个页面的开发，变为基于一个个组件进行开发。开发完成后使用 webpack 等工具进行打包构建，并通过基于 Node.js 实现的命令行工具将构建结果发布上线。前端开发开始变得规范化、标准化、工程化。
### 基于 Node.js 的全栈开发
Node.js 对前端的重要意义还有，以往只能运行在浏览器中的 JavaScript 也可以运行在服务器上，前端工程师可以用自己最熟悉的语言来写服务端的代码。于是前端工程师开始使用 Node.js 做全栈开发，开始由前端工程师向全栈工程师的方向转变。这是前端主动突破自己的边界。
另一方面，前端在发展，后端也在发展。也差不多在 Node.js 诞生那个时代，后端普遍开始由巨石应用模式由微服务架构转变。这也就导致以往的前后端分工出现了分歧。随着微服务架构的兴起，后端的接口渐渐变得原子性，微服务的接口也不再直接面向页面，前端的调用变得复杂了。于是 BFF（Backend For Frontend）架构应运而生，在微服务和前端中间，加了一个 BFF 层，由 BFF 对接口进行聚合、裁剪后，再输出给前端。而 BFF 这层不是后端本质工作，且距离前端最近和前端关系最大，所以前端工程师自然而然选择了 Node.js 来实现。这也是当前 Node.js 在服务端较为广泛的应用。
### 下一代前端开发模式
可以看到，每一次前端开发模式的变化，都因某个变革性的技术而起。先是 AJAX，而后是 Node.js。那么下一个变革性的技术是什么？不言而喻，就是 Serverless。
## 基于 Serverless 的前端开发模式
在本章节，主要以几个案例来说明基于 Serverless 的前端开发模式，以及它和以往的前端开发有什么不一样。
在开始具体的案例之前，先看一下传统开发流程。
![](https://cdn.nlark.com/yuque/0/2023/png/785653/1676364755718-bc2ca0de-8c22-47cc-94f2-6e5f347839c9.png#averageHue=%23494b46&clientId=ucf21f50c-80d6-4&from=paste&id=u95167c7a&originHeight=150&originWidth=1402&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=uc9f380cd-95e2-4abc-ac14-fdcf4897bf5&title=)
在传统开发流程中，我们需要前端工程师写页面，后端工程师写接口。后端写完接口之后，把接口部署了，再进行前后端联调。联调完毕后再测试、上线。上线之后，还需要运维工程师对系统进行维护。整个过程涉及多个不同角色，链路较长，沟通协调也是一个问题。
而基于 Serverless，后端变得非常简单了，以往的后端应用被拆分为一个个函数，只需要写完函数并部署到 Serverless 服务即可，后续也不用关心任何服务器的运维操作。后端开发的门槛大幅度降低了。因此，只需要一个前端工程师就可以完成所有的开发工作。
![](https://cdn.nlark.com/yuque/0/2023/png/785653/1676364755721-3149829c-1703-44ca-83d9-4f6ce0ddea11.png#averageHue=%23259264&clientId=ucf21f50c-80d6-4&from=paste&id=ua21f9424&originHeight=174&originWidth=1136&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u73ab88a7-b90e-4f6c-93fa-7fb0ed485af&title=)
当然，前端工程师基于 Serverless 去写后端，最好也需要具备一定的后端知识。涉及复杂的后端系统或者 Serverless 不适用的场景，还是需要后端开发，后端变得更靠后了。
## BFF的认知
主要有以下几点优势👇

- 可以降低沟通成本：后端同学追求解耦，希望客户端应用和内部微服务不耦合，通过引入BFF这中间层，使得两边可以独立变化
- 多端应用适配：展示不同的（或更少量的）数据，比如PC端页面设计的API需要支持移动端，发现现有接口从设计到实现都与桌面UI展示需求强相关，无法简单适应移动端的展示需求 ，就好比PC端一个新闻推荐接口，接口字段PC端都需要，而移动端呢H5不需要，这个时候根据不同终端在BFF层做调整，同时也可以进行不同的（或更少的）API调用（聚合）来减少http请求

总结：当你在设计 API 时，会因为不同终端存在不同的区分，它们对服务端提供的 API 访问也各有其特点，需要做一些区别处理。这个时候如果考虑在原有的接口上进行修改，会因为修改导致耦合，破坏其单一的职责。
**痛点**

- 重复开发：每个设备开发一个 BFF 应用，也会面临一些重复开发的问题展示，增加开发成本
- 维护问题：需要维护各种 BFF 应用。以往前端也不需要关心并发，现在并发压力却集中到了 BFF 上
- 链路复杂：流程变得繁琐，BFF引入后，要同时走前端、服务端的研发流程，多端发布、互相依赖，导致流程繁琐
- 浪费资源: BFF层多了，资源占用就成了问题，会浪费资源，除非有弹性伸缩扩容
## Serverless
我们可以将 Serverless 拆解为 server 和 less 两个单词，从字面上推断词意即为“少服务器的，亦或是无服务器的，弱化后端和运维概念,当前比较成熟的 Serverless 云产品主要有 Amazon Lambda、Google Cloud Function、Azure Function、AliCloud Function Compute、Tencent CloudBase等
Serverless = Faas (Function as a service) + Baas (Backend as a service)
![](https://cdn.nlark.com/yuque/0/2023/png/785653/1676364755740-7713d374-3a6e-446a-8438-9180cdb9bf0e.png#averageHue=%23fdfefd&clientId=ucf21f50c-80d6-4&from=paste&id=u8079dd76&originHeight=519&originWidth=1280&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u9cbe860c-21d2-4c02-8b6c-d1fcc8b1dc3&title=)
### 云函数（Faas）
FaaS（Function-as-a-Service）是服务商提供一个平台、提供给用户开发、运行管理这些函数的功能，而无需搭建和维护基础框架，是一种事件驱动由消息触发的函数服务
前端同学调用Faas服务如同调用本地函数一样简洁，如下所示，是一个腾讯云中一个简单的小程序云开发demo，cloudfunction是用来定义云函数的方法
### 后端即服务（ BaaS）
BaaS（Backend-as-a-Service）后端即服务，包含了后端服务组件，它是基于 API 的第三方服务，用于实现应用程序中的核心功能，包含常用的数据库、对象存储、消息队列、日志服务等等。
比如腾讯云云开发中下面的这些服务👇：

- 微信小程序的云调用 [wx-server-sdk](https://link.juejin.cn/?target=https%3A%2F%2Fdevelopers.weixin.qq.com%2Fminiprogram%2Fdev%2Fwxcloud%2Fguide%2Fopenapi%2Fopenapi.html)
- 云开发数据库 [wx.cloud.database](https://link.juejin.cn/?target=https%3A%2F%2Fdevelopers.weixin.qq.com%2Fminiprogram%2Fdev%2Fwxcloud%2Freference-client-api%2Fdatabase%2Fdatabase.html)
### Serverless的架构
![](https://cdn.nlark.com/yuque/0/2023/png/785653/1676364755863-9bad4f53-789b-4b1b-96a9-6fe0d21a01a4.png#averageHue=%23b0d2e5&clientId=ucf21f50c-80d6-4&from=paste&id=ua8ed3939&originHeight=562&originWidth=1280&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u64147dea-a3c9-4739-9428-cf18364ee57&title=)
### Serverless的优势

- 环境统一: 不需要搭建服务端环境,, 保持各个机器环境一致 Serverless 的机制天然可复制
- 按需计费: 我们只在代码运行的时候付费，没有未使用资源浪费的问题
- 丰富的SDK: 有完善的配套服务, 如云数据库, 云存储, 云消息队列, 云音视频和云 AI 服务等
- 弹性伸缩: 不需要预估流量, 关心资源利用率, 备份容灾, 扩容机器 ，可以根据流量动态提前峰值流量

![](https://cdn.nlark.com/yuque/0/2023/png/785653/1676364755704-98906df9-eeab-4e68-9ad5-f24046c23f1e.png#averageHue=%23fbfbfb&clientId=ucf21f50c-80d6-4&from=paste&id=u4c6987b1&originHeight=407&originWidth=1059&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u50b274cd-6e9f-43cb-8524-a3ec6291fef&title=)
❝
“ Serverless 带来的其实是前端研发模式上的颠覆。相对以往纯前端研发的方式，Serverless 屏蔽底层基础设施的复杂度，后台能力通过FaaS平台化，我们不再需要关注运维、部署的细节，开发难度得到了简化，前端开发群体的边界就得以拓宽，能够参与到业务逻辑的开发当中，更加贴近和理解业务，做更有价值的输出。”
❞
### Serverless的缺点

- 云厂商强绑定：它们常常会和厂商的其他云产品相绑定，如对象存储、消息队列等，意味你需要同时开通其他的服务，迁移成本高，如果想迁移基本原有的逻辑不可服用，kennel需要重构
- 不适合长时间任务：云函数平台会限制函数执行时间，如阿里云 Function Compute 最大执行时长为 10 min
- 冷启动时间：函数运行时，执行容器和环境需要一定的时间，对 HTTP 请求来讲，可能会带来响应时延的增加
- 调试与测试：开发者需要不断调整代码，打印日志，并提交到函数平台运行测试，会带来开发成本和产生费用

![](https://cdn.nlark.com/yuque/0/2023/png/785653/1676364759234-b7912fb4-5623-43e8-9136-d71fd2007b79.png#averageHue=%23f5f5f5&clientId=ucf21f50c-80d6-4&from=paste&id=u788ff9d6&originHeight=245&originWidth=806&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u3004815a-8095-423d-92b4-3cbfdd2c498&title=)
## 基于 Serverless 的服务端渲染
基于当下最流行的三大前端框架（React.js/Anguler/Vue.js），现在的渲染方式大部分都是客户端渲染。页面初始化的时候，只加载一个简单 HTML 以及对应的 JS 文件，再由 JS 来渲染出一个个页面。这种方式最主要的问题就是白屏时间和 SEO。
为了解决这个问题，前端又开始尝试服务端渲染。本质思想其实和最早的模板渲染是一样的。都是前端发起一个请求，后端 Server 解析出一个 HTML 文档，然后再返回给浏览器。只不过以往是 JSP、PHP 等服务端语言的模板，现在是基于 React、Vue 等实现的同构应用，这也是如今的服务端渲染方案的优势。
但服务端渲染又为前端带来了一些额外的问题：运维成本，前端需要维护用于渲染的服务器。
Serverless 最大的优点就是可以帮我们减少运维，那 Serverless 能不能用于服务端渲染呢？当然也是可以的。
传统的服务端渲染，每个请求的 path 都对应着服务端的每个路由，由该路由实现对应 path 的 HTML 文档渲染。用于渲染的服务端程序，就是这些集成了这些路由的应用。
使用 Serverless 来做服务端渲染，就是将以往的每个路由，都拆分为一个个函数，再在 FaaS 上部署对应的函数。这样用户请求的 path，对应的就是每个单独的函数。通过这种方式，就将运维操作转移到了 FaaS 平台，前端做服务端渲染，就不用再关心服务端程序的运维部署了。
![](https://cdn.nlark.com/yuque/0/2023/png/785653/1676364759230-e9fa681f-fe61-4f53-914e-66ba4b236af7.png#averageHue=%23325a75&clientId=ucf21f50c-80d6-4&from=paste&id=ud4de1a60&originHeight=668&originWidth=1706&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u77711671-09f3-4a9e-89fd-316ac6d9a43&title=)
[ZEIT](https://link.juejin.cn/?target=https%3A%2F%2Fzeit.co) 的 [Next.js](https://link.juejin.cn/?target=https%3A%2F%2Fnextjs.org%2Fdocs%2F%23serverless-deployment) 就对基于 Serverless 的服务端渲染做了很好的实现。下面就是一个简单的例子。
代码结构如下：
.
├── next.config.js
├── now.json
├── package.json
└── pages
    ├── about.js
    └── index.js
// next.config.js
module.exports = {
  target: 'serverless'
}
其中 pages/about.js 和 pages/index.js 就是两个页面，在 next.config.js 配置了使用 Zeit 提供的 Serverless 服务。
然后使用 now 这个命令，就可以将代码以 Serverless 的方式部署。部署过程中，pages/about.js 和 pages/index.js 就分别转换为两个函数，负责渲染对应的页面。
![](https://cdn.nlark.com/yuque/0/2023/png/785653/1676364759234-6432c91d-7f27-4cb9-bc2f-ef324012d9f2.png#averageHue=%23f4f4f4&clientId=ucf21f50c-80d6-4&from=paste&id=u3dd45807&originHeight=630&originWidth=1214&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u5f9d5aac-9f02-4555-822d-9b51c03d1a9&title=)
## 基于 Serverless 的小程序开发
目前国内使用 Serverless 较多的场景可能就是小程开发了。具体的实现就是小程序云开发，支付宝小程序和微信小程序都提供了云开发功能。
在传统的小程序开发中，我们需要前端工程师进行小程序端的开发；后端工程师进行服务端的开发。小程序的后端开发和其他的后端应用开发，本质是是一样的，需要关心应用的负载均衡、备份冗灾、监控报警等一些列部署运维操作。如果开发团队人很少，可能还需要前端工程师去实现服务端。
但基于云开发，就只需要让开发者关注于业务的实现，由一个前端工程师就能够完成整个应用的前后端开发。因为云开发将后端封装为了 BaaS 服务，并提供了对应的 SDK 给开发者，开发者可以像调用函数一样使用各种后端服务。应用的运维也转移到了提供云开发的服务商。
![](https://cdn.nlark.com/yuque/0/2023/png/785653/1676364759315-766642c3-4ada-45a5-b0be-8f2104dd44c6.png#averageHue=%23f0e0b7&clientId=ucf21f50c-80d6-4&from=paste&id=u7426455e&originHeight=640&originWidth=1480&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u49c2ceaa-533a-49af-a4e7-71230b1b268&title=)
下面分别是使用[支付宝云开发（Basement）](https://link.juejin.cn/?target=https%3A%2F%2Fdocs.alipay.com%2Fmini%2Fdeveloper%2Ftodo-basement)的一些例子，函数就是定义在 FaaS 服务中的函数。

操作数据库
```javascript
// `basement` 是一个全局变量
// 操作数据库
basement.db.collection('users')
	.insertOne({
		name: 'node',
		age: 18,
	})
	.then(() => {
		resolve({ success: true });
	})
	.catch(err => {
		reject({ success: false });
	});
```

**上传图片**

```javascript
// 上传图片
basement.file
	.uploadFile(options)
	.then((image) => {
		this.setData({
			iconUrl: image.fileUrl,
		});
	})
	.catch(console.error);
```

**调用函数**

```javascript
// 调用函数
basement.function
	.invoke('getUserInfo')
	.then((res) => { 
		this.setData({ 
			user: res.result
		});
	})
	.catch(console.error}
```
