# 网络请求

## 主要文件

* [conn.ts ](https://github.com/ccqiuqiu/iface/blob/7489643b579a46af24aa17b69649551e1f9e6734/src/global/conn.ts)- axios实例，公用配置，请求和响应拦截
* [api.ts](https://github.com/ccqiuqiu/iface/blob/7489643b579a46af24aa17b69649551e1f9e6734/src/global/api.ts) - 接口配置

## 流程

* 组件中通过action发起网络请求
* action调用api.ts里面的方法
* api.ts调用axios的request方法发起请求
* request方法返回promise
* action或组件处理返回数据

## 请求和响应拦截器

iFace在conn.ts文件里面定义了统一的请求和响应的拦截器，其中请求拦截器主要用于添加公共参数（如token\)、显示loading等，响应拦截器则主要用于处理隐藏loading、错误提示、日志记录等



