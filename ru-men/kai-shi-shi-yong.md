---
description: 通过此章节，您可以快速开始一个项目。
---

# 开始使用

## 前期准备

* [vue.js](https://cn.vuejs.org/)
* [vue-router](https://router.vuejs.org/zh/)
* [vuex](https://vuex.vuejs.org/zh/)
* [typescript](https://www.tslang.cn/index.html)
* [element-ui](https://element.faas.ele.me/#/zh-CN/component/installation)

## 环境要求

* node &gt;= 7
* 服务端支持（配套服务端[https://github.com/ccqiuqiu/base-api](https://github.com/ccqiuqiu/base-api)）

## 安装使用

```bash
# clone项目到本地
git clone https://github.com/ccqiuqiu/iface.git
# 安装依赖
npm install
# 开发模式
npm run dev
# mock开发
npm run mock
# record(接口录制)模式
npm run record
# build
npm run build
# build(带mock数据)
npm run build-m
```

## 目录结构

```text
├─ public                       // 公共资源目录            
│   ├─ favicon.ico              // 网站favicon
│   └─ index.html               // 主页
├─ src                          // 源码目录          
│   ├─ assets                   // 静态资源目录   
│   │   ├─ css                  // 样式文件目录
│   │   │   ├─ base.scss        // 基础样式
│   │   │   ├─ theme.scss       // 主题相关样式
│   │   │   └─ vars.scss        // 样式变量定义
│   │   ├─ icons                // 图标目录
│   │   │   ├─ svg              // svg文件目录
│   │   │   │   └─ *.svg        // svg文件
│   │   │   └─ icon.ts          // 读取.svg文件      
│   │   └─ utils                // 工具类/方法目录
│   │       ├─ constant.ts      // 常量
│   │       ├─ CrudUtils.ts     // CRUD相关的工具方法
│   │       ├─ index.ts         // 统一导出工具类
│   │       ├─ lsUtils.ts       // 本地存储相关的工具方法
│   │       ├─ uiUtils.ts       // UI相关的工具方法
│   │       └─ utils.ts         // 其他一些工具方法          
│   ├─ baseConmponents          // 业务无关的基础组件
│   │   ├─ *.vue                // 一些组件
│   ├─ gloabl                   // 全局的一些类
│   │   ├─ api.ts               // 全局的API配置
│   │   ├─ conn.ts              // 全局的网络请求实例
│   │   ├─ regComponents.ts     // 全局的组件注册
│   │   ├─ router.ts            // 全局的路由
│   │   └─ store.ts             // 全局的store             
│   ├─ record                   // 接口录制服务目录
│   │   ├─ app.js               // 录制服务启动文件 
│   │   └─ CcRecord.vue         // 录制模式启动的时候，加载的组件          
│   └─ modules                  // 业务模块目录
│   │   ├─ common               // common模块
│   │   │   ├─ fragment         // .vue片段片段目录
│   │   │   │   └─ *.vue        // .vue片段文件，主要用于细化组件
│   │   │   ├─ view             // 组件目录
│   │   │   │   └─ *.vue        // .vue组件，一般是对应路由的component或者是完整的page
│   │   │   ├─ router.ts        // 模块的router
│   │   │   └─ vuex.ts          // 模块的vuex(store、action、mutations等)
│   │   └─ ......               // 其他一些模块，每个模块的目录和文件同common一致
│   ├─ typings                  // ts声明文件目录
│   │   └─ *.d.ts               // ts声明文件
│   ├─ App.vue                  // 根组件
│   └─ main.ts                  // 入口文件
├─ .env.development             // development环境的环境变量配置
├─ .env.mock                    // mock环境的环境变量配置
├─ .env.production              // 生产环境的环境变量配置
├─ .gitignore                   // git忽略文件
├─ babel.config.js              // babel配置文件
├─ package.json                 // 项目的npm配置文件
├─ package-lock.json            // npm版本锁
├─ README.md                    // readme
├─ tsconfig.json                // ts配置文件
├─ tslint.json                  // tslint配置文件
└─ veu.config.js                // vue-cli配置
```

