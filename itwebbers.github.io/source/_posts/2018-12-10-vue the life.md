---
layout: post
title: 'vue生命周期详解'
categories:
  - Vuejs
tags:
  - vue
  - JavaScript
---

# vue2.0 生命周期详解

> [参考链接](https://segmentfault.com/a/1190000008010666)

|     阶段      |                                                 状态                                                  |
| :-----------: | :---------------------------------------------------------------------------------------------------: |
| beforeCreate  |                                         el 和 data 并未初始化                                         |
|    created    |                                完成了 data 数据初始化，但是 el 并没有                                 |
|  beforeMount  |                                     完成了 el 和 data 数据初始化                                      |
|    mounted    |                                               完成挂载                                                |
| beforeUpdate  |                                          data 变化时会被触发                                          |
|    updated    |                                          data 变化时会被触发                                          |
| beforeDestroy |                                     实例销毁前调用，依然可以使用                                      |
|   destroyed   | 对 data 的方法不会再出发周期函数，说明此时 vue 实例已经接触了事件监听和 dom 的绑定，但是 dom 依然存在 |

[参考链接](https://juejin.im/post/5ad10800f265da23826e681e)
