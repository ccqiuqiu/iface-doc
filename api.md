---
description: 这个章节主要描述了实现iFace基础框架需要的基本接口，后端必须提供这些接口才能让iFace正常运行
---

# API文档

{% api-method method="post" host="" path="/版本号/模块/接口名\[query\|/params\]" %}
{% api-method-summary %}
 公共请求
{% endapi-method-summary %}

{% api-method-description %}
**这是所有请求的公共参数，所有的接口都遵循这个规律，  
  
所以后面的接口将只列出接口独有的入参和请求成功返回的业务数据（data属性）**
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    success: true, // 成功状态，true是成功，false是失败
    data: {}, // 业务数据，当success为true时有这个属性
    error: { // 异常对象，当success为false时有这个属性
      code: 123,  // 错误码
      message: '' // 错误信息
    }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    success: false,
    error: {
      code: 401,
      message: '未登录或已登录，请重新登录'
    }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=402 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    success: false,
    error: {
      code: 402,
      message: '越权操作，请联系管理员'
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## CRUD相关接口

{% hint style="info" %}
以下5个接口是CRUD页面使用的接口，实际后端应该每一个实体后分别有这5个接口，将接口名里面的Modle替换成具体的实体名称，给前端调用。
{% endhint %}

{% api-method method="post" host="" path="/v1/page/searchModel" %}
{% api-method-summary %}
查询实体列表
{% endapi-method-summary %}

{% api-method-description %}
用于查询动态CURD页面的数据列表的接口，这个接口的入参会包含页面上搜索表单中所有非空的字段和下面列表的参数
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="pageSize" type="number" required=false %}
每页显示条数，默认10
{% endapi-method-parameter %}

{% api-method-parameter name="pageNum" type="number" required=false %}
 当前页码，默认1
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Cake successfully retrieved.
{% endapi-method-response-example-description %}

```javascript
{
    success: true,
    data: {
      rows: any[],  // 当前页的数据
      total: number  // 总条数
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="" path="/v1/page/getModel/:id" %}
{% api-method-summary %}
查询单个实体
{% endapi-method-summary %}

{% api-method-description %}
查询单个实体，用于CRUD页面编辑表单的数据初始化
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
实体的id
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    success: true,
    data: any // 查询到的实体
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="" path="/v1/page/saveModel" %}
{% api-method-summary %}
保存实体
{% endapi-method-summary %}

{% api-method-description %}
 CRUD页面的新增和更新实体的操作
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="object" required=true %}
 需要新增/更新的实体
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    success: true,
    data: {} // 空
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="" path="/v1/page/delModel/:id" %}
{% api-method-summary %}
 删除一条数据
{% endapi-method-summary %}

{% api-method-description %}
CRUD页面通过id删除一条数据的接口
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
实体的id
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    success: true, 
    data: {} // 空
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="" path="/v1/page/viewModel/:id" %}
{% api-method-summary %}
 查看详情的
{% endapi-method-summary %}

{% api-method-description %}
CRUD页面查看数据详情的接口
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
实体id
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    success: true, // 成功状态，true是成功，false是失败
    data: any // 查询到的实体
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## 表单相关接口

{% api-method method="post" host="" path="/v1/base/getOptions" %}
{% api-method-summary %}
获取选项
{% endapi-method-summary %}

{% api-method-description %}
获取选择型组件的选项数据  
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="code" type="string" required=true %}
 数据源的标识，后端根据这个标识返回不同的数据
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=false %}
 数据源类型，后端根据这个类型返回不同的数据结构，如树、表格等
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    success: true
    data: any // 这里返回的数据根据入参type会有不同
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="" path="/v1/base/getPageOptions/:code" %}
{% api-method-summary %}
 获取选项（dialog）
{% endapi-method-summary %}

{% api-method-description %}
 获取弹窗选择器的选择项数据  
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="code" type="string" required=true %}
 CRUD页面的code
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    success: true
    data: Page // page对象
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Dashboard相关接口

{% api-method method="post" host="" path="/v1/base/getAllDashboard" %}
{% api-method-summary %}
 查找所有的Dashboard
{% endapi-method-summary %}

{% api-method-description %}
 查找所有可以添加到首页的仪表盘
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    success: true
    data: Dashboard[] // 仪表盘数组
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="" path="/v1/base/getUserDashboard" %}
{% api-method-summary %}
 用户的DashBoard布局
{% endapi-method-summary %}

{% api-method-description %}
 查找用户已经添加到首页的仪表盘布局，如果用户没有配置过，则返回所有仪表盘的前8个
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    success: true
    data: Array<Dashboard | UserDashboard> // 仪表盘数组或用户的仪表盘布局
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="" path="/v1/base/saveUserDashboard" %}
{% api-method-summary %}
 保存用户的Dashboard布局
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="userDashboards" type="array" required=true %}
 用户仪表盘配置数组
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    success: true
    data: {} // 空
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## 其他业务接口

{% api-method method="post" host="" path="/v1/public/login" %}
{% api-method-summary %}
 用户登录
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="name" type="string" required=true %}
 用户名
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=true %}
 密码
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    success: true
    data: {} // 空
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="" path="/v1/base/getAuth" %}
{% api-method-summary %}
 获取权限数据
{% endapi-method-summary %}

{% api-method-description %}
 获取用户的权限数据
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    success: true
    data: {
      user: User, // 用户数据
      auth: {
        menus: Menu[], // 有权限的菜单数组
        resources: string[] // 有权限的资源code数组
      }
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="" path="/v1/public/logout" %}
{% api-method-summary %}
 退出登录
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    success: true
    data: {} // 空
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="" path="/v1/page/searchPage" %}
{% api-method-summary %}
 查询表单/页面列表
{% endapi-method-summary %}

{% api-method-description %}
 查询系统配置好的动态表单和页面的分页数据
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="pageSize" type="number" required=false %}
 每页显示数据条数，默认10
{% endapi-method-parameter %}

{% api-method-parameter name="pageNum" type="number" required=false %}
 当前页，默认1
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    success: true
    data: {
      rows: Page[], // 当前页数据
      total: number // 总条数
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="" path="/v1/page/getPage/:code" %}
{% api-method-summary %}
 获取表单/页面数据
{% endapi-method-summary %}

{% api-method-description %}
 通过页面代码获取页面数据
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="code" type="string" required=true %}
 页面代码
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    success: true
    data: Page // 页面数据
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="" path="/v1/page/savePage" %}
{% api-method-summary %}
 保存表单/页面数据
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="" type="object" required=true %}
page对象
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    success: true
    data: {} // 空
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="" path="/v1/page/delPage/:id" %}
{% api-method-summary %}
 删除表单/页面
{% endapi-method-summary %}

{% api-method-description %}
 根据id删除表单或页面
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
 要删除的页面id
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    success: true
    data: {} // 空
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="" path="/v1/system/menuTree" %}
{% api-method-summary %}
获取菜单树
{% endapi-method-summary %}

{% api-method-description %}
 以树形结构查询所有的菜单
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    success: true
    data: Array<{
      id: string, // 菜单id
      name: string, // 菜单名称
      url?: string, // 菜单的URL
      icon?: string, // 菜单的图标
      children: Menu[] // 子菜单
    }>
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="" path="/v1/system/saveMenu" %}
{% api-method-summary %}
 保存菜单
{% endapi-method-summary %}

{% api-method-description %}
 新增或修改菜单
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="" type="object" required=true %}
 菜单对象
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    success: true
    data: {} // 空
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="" path="/v1/system/delMenu/:id" %}
{% api-method-summary %}
 删除菜单
{% endapi-method-summary %}

{% api-method-description %}
 通过id删除菜单
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
 菜单id
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    success: true
    data: {} // 空
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

