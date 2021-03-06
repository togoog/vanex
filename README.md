# vanex
[![](https://img.shields.io/npm/dm/vanex.svg)](https://www.npmjs.com/package/vanex)

[![NPM](https://nodei.co/npm/vanex.png)](https://npmjs.org/package/vanex)  

[github](https://github.com/alibaba/vanex)

Vanex 是基于 mobx 的 React 数据流管理框架，旨在借助 mobx 提供的基础能力，帮助用户组织更大规模的 React 项目。

# 文档

[https://alibaba.github.io/vanex/](https://alibaba.github.io/vanex/)

# Quick Start

Vanex 提供两个简洁的 API：@vanex 和 start

```js
import React from 'react';
import { vanex, start } from 'vanex';

const Model = {};

@vanex('Model')
class Comp extends React.Component{
}

start({
    component: Comp,
    container: '#root',
    models: {
        Model,
    }
});
```

See more: [https://alibaba.github.io/vanex/quick-start.html](https://alibaba.github.io/vanex/quick-start.html)

# 说明

- mobx是基于`Object.defineProperties()`(无法监听新增属性)实现的，所以会导致：如果在model的data里没有预先设置某项值，后面对该值做改动的时候就不会触发UI的重新渲染，解决方案：调用React刷新UI的API，手动触发UI更新：`this.foreceUpdate()`；
- ES7 decorator语法的编译需要babel插件支持：[babel-plugin-transform-decorators-legacy](https://www.npmjs.com/package/babel-plugin-transform-decorators-legacy)。

# TODO

- [x] 修复`autorun`里执行effects里的方法会导致死循环的问题；