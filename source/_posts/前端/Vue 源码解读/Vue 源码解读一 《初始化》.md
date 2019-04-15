

Vue 运行时对象的初始化分可以划分为三部分：

* 一个是 Vue 类的定义，这一块主要包括实例方法属性和 Vue 的实例化过程。
* 一个是 Vue 的全局 API 的初始化，这一块主要包含了对 Vue 类操作的一些类静态方法，包括 Vue.use、Vue.mixins、Vue.extend 等类方法，以及其类属性(这也是 Vue 实例化的一部分)。
* 一个服务端渲染相关的模块（这算是更深的扩展）。

代码如下：

```js
// src/core/index.js
import Vue from './instance/index'
import { initGlobalAPI } from './global-api/index'
import { isServerRendering } from 'core/util/env'
import { FunctionalRenderContext } from 'core/vdom/create-functional-component'

initGlobalAPI(Vue) 

Object.defineProperty(Vue.prototype, '$isServer', {
  get: isServerRendering
})

Object.defineProperty(Vue.prototype, '$ssrContext', {
  get () {
    /* istanbul ignore next */
    return this.$vnode && this.$vnode.ssrContext
  }
})

// expose FunctionalRenderContext for ssr runtime helper installation
Object.defineProperty(Vue, 'FunctionalRenderContext', {
  value: FunctionalRenderContext
})

Vue.version = '__VERSION__'

export default Vue
```

其中 *import Vue from './instance/index'* 是引入了 Vue 的实例化部分，*initGlobalAPI(Vue)* 及后续部分是则是 Vue 类方法和属性的实例化。关键部分在 initGlobalAPI，这部分的主要操作如下：







这些方法全都是挂在在 Vue 类上的，有些是全局方法和属性，有些是在实例化过程中用的比较多的工具函数。这些函数的实现都影响着 Vue 实例化的过程。其中任何一个模块都值得深究。

不过全局配置这块，用的不算多，而且也不影响后续核心代码的理解，暂时先不看这块的代码。几个 Util 方法有必要先熟悉一下，因为在后续的代码中会频繁的用到这些方法，如果不理解将会很困难。另外 Vue.extend 也是需要先了解的一部分，因为这个方法表示了一种 Vue 的实例化方式，而实例化的过程必然和实例化方式相关，所以需要先了解实例化的大环境。



那么这篇就像看看 util 的工具方法和 extend 的实现吧。



