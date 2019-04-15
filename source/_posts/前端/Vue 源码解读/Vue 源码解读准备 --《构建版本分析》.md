---
title: Vue 源码解读一《目录和构建版本分析》
categories:
  - 前端
date: 2019-03-16 08:30:53
tags:
  - Vue
---

目标： 

1. 了解 Vue 的构建版本区别。
2. 解决 '搭建项目是该怎么选用构建版本'，以及 '为什么选了这个版本' 的问题。
3. 解决 '想要看源码我该从哪里入手’ 的问题。



### 问题1. Vue 构建版本的区别

![image.png](https://upload-images.jianshu.io/upload_images/4580053-c832fb9deafc6356.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

Vue 提供了不同功能，不同环境的与不同打包方式的包，以满足各种情况的需求。不过这只是Vue 官网的描述了的内容，实际源码中还有更多的构建方式。比如测试版本的构建，比如 weex 版的构建，比如 ssr 版的构建。比如 types 版本的构建。源码如下：



```js
"scripts": {
  "dev": "rollup -w -c scripts/config.js --environment TARGET:web-full-dev",
  "dev:cjs": "rollup -w -c scripts/config.js --environment TARGET:web-runtime-cjs-dev",
  "dev:esm": "rollup -w -c scripts/config.js --environment TARGET:web-runtime-esm",
  "dev:test": "karma start test/unit/karma.dev.config.js",
  "dev:ssr": "rollup -w -c scripts/config.js --environment TARGET:web-server-renderer",
  "dev:compiler": "rollup -w -c scripts/config.js --environment TARGET:web-compiler ",
  "dev:weex": "rollup -w -c scripts/config.js --environment TARGET:weex-framework",
  "dev:weex:factory": "rollup -w -c scripts/config.js --environment TARGET:weex-factory",
  "dev:weex:compiler": "rollup -w -c scripts/config.js --environment TARGET:weex-compiler ",
  "build": "node scripts/build.js",
  "build:ssr": "npm run build -- web-runtime-cjs,web-server-renderer",
  "build:weex": "npm run build -- weex",
  "test": "npm run lint && flow check && npm run test:types && npm run test:cover && npm run test:e2e -- --env phantomjs && npm run test:ssr && npm run test:weex",
  "test:unit": "karma start test/unit/karma.unit.config.js",
  "test:cover": "karma start test/unit/karma.cover.config.js",
  "test:e2e": "npm run build -- web-full-prod,web-server-basic-renderer && node test/e2e/runner.js",
  "test:weex": "npm run build:weex && jasmine JASMINE_CONFIG_PATH=test/weex/jasmine.js",
  "test:ssr": "npm run build:ssr && jasmine JASMINE_CONFIG_PATH=test/ssr/jasmine.js",
  "test:sauce": "npm run sauce -- 0 && npm run sauce -- 1 && npm run sauce -- 2",
  "test:types": "tsc -p ./types/test/tsconfig.json",
  "lint": "eslint src scripts test",
  "flow": "flow check",
  "sauce": "karma start test/unit/karma.sauce.config.js",
  "bench:ssr": "npm run build:ssr && node benchmarks/ssr/renderToString.js && node benchmarks/ssr/renderToStream.js",
  "release": "bash scripts/release.sh",
  "release:weex": "bash scripts/release-weex.sh",
  "release:note": "node scripts/gen-release-note.js",
  "commit": "git-cz" 
},
```


面对如此多的构建方式，选用的时候，改怎么选？看源码的时候应该从哪里看？ 

### 问题2. 搭建项目是该怎么选用构建版本？

关于选用的问题，可以从按功能，打包方式，和应用场景选择。(看起来各种版本可能有点多，实际很清晰，现在看这个问题，感觉当时我第一次用的时候怎么会有该选哪个版本的问题这种个问题。。。)



### 问题3. 想要看源码我该从哪里入手

看源码，我认为，当然是从运行时开始，这是核心功能，其他都是辅助工具(包括编译模板，因为当使用了打包工具 vue-loader 后编译模板实际上就再是Vue 源码这块去负责了，而是由 vue-loader 完成了)。那么就可以通过此处的打包配置去找真正的入口文件了(第一次看源码，有种不知道该从哪个文件入手的感觉)。然后配合源码目录就可以很明了的看到各个文件模块的作用以及从哪里来到哪里去问题。



看打包配置此时只需要关注 runtime 就可以了，至于是 esm 还是 cjs 都无所谓。那么选择 **dev:esm** 这条配置，从中可以看出该配置指向 **scripts/config.js** 文件，并附带了一下参数。

```js
"dev:esm": "rollup -w -c scripts/config.js --environment TARGET:web-runtime-esm"
```

从 TAEGET 可以找到一下代码：

```js
  'web-runtime-esm': {
    entry: resolve('web/entry-runtime.js'),
    dest: resolve('dist/vue.runtime.esm.js'),
    format: 'es',
    banner
  },
```

说明了运行时的输入文件入口为 *web/entry-runtime.js*，输出文件为 *dist/vue.runtime.esm.js*。其中输入文件中的 web 目录在 .flowconfig 中定义指向目录 */src/platforms/web/* 。



