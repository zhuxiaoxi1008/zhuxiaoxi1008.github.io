### 前端面试准备笔记

基础面试题
1. 讲讲你做的最有挑战性的前端项目？难点怎么解决的？
使用 STAR 法 回答：

Situation：背景（什么系统、什么痛点）
Task：你的职责
Action：用了什么技术、怎么优化的、踩了什么坑
Result：数据提升 / 问题解决结果
加分点：提到权限控制、XSS 防护、性能监控、与安全团队协作的经历。

2. Vue2 和 Vue3 最大的区别？响应式原理区别？
简答：

Vue2：Object.defineProperty，深度遍历、无法侦测新增/删除属性、数组需特殊处理
Vue3：Proxy + Reflect，直接代理整个对象，支持新增/删除、Map/Set/WeakMap，更高效
额外：Composition API、更小的打包体积、Teleport、Fragment、Suspense

加分点：说说 ref / reactive 区别、effectScope、<script setup> 语法糖。

3. Vue 组件间通信有哪些方式？（至少说 6 种）
常见回答：

props / $emit
v-model / .sync（Vue2）/ defineModel（Vue3）
provide / inject
全局事件总线（mitt / tiny-emitter）
Vuex / Pinia
$attrs / $listeners（Vue2）→ attrs + emit（Vue3）
父子通过 ref 操作 / $parent / $children / $root

4. XSS 是什么？怎么分类？前端如何防御？
分类：反射型、存储型、DOM-based

防御（前端能做的）：

输入：白名单校验、正则过滤
输出：对用户内容做转义（textContent / innerText > innerHTML）
富文本：使用成熟库 + 过滤（DOMPurify / js-xss）
CSP（Content-Security-Policy）限制加载资源
HttpOnly + Secure Cookie（防窃取）
避免 eval / new Function / innerHTML
加分点：提 DOM-based XSS 示例（location.hash / document.write）。

5. CSRF 是什么？怎么防御？
简答：跨站请求伪造，利用用户登录态发送恶意请求。

防御：

SameSite=Strict/Lax Cookie
token（form 隐藏域 / header）
双重验证（密码/短信）
Referer / Origin 校验

6. 同源策略是什么？跨域有哪些解决方案？
同源：协议+域名+端口三相同。

解决方案（按常用排序）：

CORS（后端 Access-Control-Allow-*）
jsonp（只限 get）
postMessage（iframe / window.open）
nginx / devServer proxy
document.domain（主域相同子域）
WebSocket / SSE（不严格受同源限制）

7. 浏览器从输入 URL 到页面渲染发生了什么？（经典全链路）
简要版： DNS解析 → TCP三次握手 → TLS握手（HTTPS） → 发送HTTP请求 → 服务端响应 → 浏览器接收 → 构建DOM/CSSOM → Render Tree → Layout → Paint → Composite

加分点：提到强缓存/协商缓存、304、preconnect/dns-prefetch、关键渲染路径优化。


中高级面试题
1. 手写防抖/节流函数（至少两种实现）
```javascript
// 防抖（最后一次执行）
function debounce(fn, delay = 300) {
  let timer = null;
  return function (...args) {
    clearTimeout(timer);
    timer = setTimeout(() => fn.apply(this, args), delay);
  };
}

// 节流（固定时间间隔）
function throttle(fn, delay = 300) {
  let last = 0;
  return function (...args) {
    const now = Date.now();
    if (now - last >= delay) {
      fn.apply(this, args);
      last = now;
    }
  };
}
```

2. HTTPS 握手过程（详细点）
客户端 hello（支持的协议、加密套件、随机数）
服务端 hello + 证书 + 随机数
客户端验证证书 → 生成预主密钥 → 用服务端公钥加密 → 发送
服务端用私钥解密得到预主密钥
双方用相同算法生成主密钥 → 对称加密通信
加分点：提中间人攻击、证书链、HSTS、证书透明度。

3. 前端性能优化（8 条以上）
资源层面：压缩、合并、CDN、WebP、懒加载、预加载
渲染层面：减少重排重绘、GPU 加速（will-change）、避免阻塞（async/defer）
代码层面：tree-shaking、code-split、虚拟列表、骨架屏
缓存：强缓存、协商缓存、Service Worker
监控：Web Vitals（LCP、FID、CLS）

4. JWT 是什么？优缺点？怎么存储？
优点：无状态、跨域友好
缺点：无法主动失效、payload 可解码（不加密敏感信息）、体积较大
存储：httpOnly + Secure 的 cookie（防 XSS） > localStorage（防 XSS 但易被脚本读取）
刷新机制：access token 短过期 + refresh token 长过期

5. Vite 为什么比 webpack 快？原理是什么？
开发时不打包，利用浏览器支持 ES Module + esbuild 超快转译
按需编译（on demand）
HMR 速度更快（只更新改动模块）
生产打包用 Rollup（tree-shaking 更强）

终面/综合面试题
1. 项目权限管理怎么做？（RBAC / 前后端分离）
前端：路由守卫 + 动态路由 + 按钮级权限（v-permission 指令）
后端：接口鉴权 + 数据权限
存储：用户信息 + 角色 + 权限码 → Pinia / localStorage
加分点：提到细粒度权限、权限缓存失效机制、越权校验。

2. 前端如何防止敏感信息泄露？（身份证、手机号等）
前端不存储、不展示完整信息（只显示后四位）
日志脱敏
禁止控制台打印敏感数据
传输走 HTTPS
避免 URL 传参敏感字段

3. 对网络安全行业了解？为什么想来绿盟？
可说：国内头部网络安全厂商，主营态势感知、Web 防火墙、等保测评等；
想来原因：对安全有兴趣、前端安全是 Web 安全重要一环、公司技术氛围好、能接触更多安全场景等。