# wc-editor

> 微尘云编辑器一期应用

## 一、项目构建说明
技术栈：vue2.0 + webpack + npm

``` bash

coding

```

## 二、项目展示
![](https://github.com/yinggege/wc-editor/blob/dev/static/pro-view-img/product-details.png)
![](https://github.com/yinggege/wc-editor/blob/dev/static/pro-view-img/payment.png)
![](https://github.com/yinggege/wc-editor/blob/dev/static/pro-view-img/payment-success.png)
![](https://github.com/yinggege/wc-editor/blob/dev/static/pro-view-img/myorder.png)
## 三、需求分析
### 1、基本需求
*通用功能*
* 实现组件在页面上的添加、删除、移位
* 实现操作历史记录，回退、前进、保存，当前版本预览、发布

*页面-商品详情*
* 商品详情页可重命名、可增加多个
* 限时抢购为整体组件，有两种样式
* 购买组件有多种样式，热点区域为整个组件
* 页面-订单结算
* 实现收货地址自动获取并保存openid，用户可编辑地址并覆盖原记录
* 配送方式可选快递免邮或自提
* 收货人编辑名字电话，收货地址地区选择详细地址填写
* 订单备注

*页面-支付成功*

*页面-我的订单*

*组件-通用组件：*
* 文本（商品详情页标题除外）：大小 颜色（选色板 输入色号） 内容
* 图片：尺寸（高度自由设置 宽度自由设置或100%填充） 样式（图片 颜色）
* 轮播图：尺寸（高度） 数量（下拉选择1-5个） 属性（选中轮播页后做图片替换或颜色填充） 事件（点击无事件或下拉框选择跳转页面）
* 视频：文本框输入视频地址
* 一键拨号：文本框输入电话号码

*组件-电商组件：*
* 添加购物车 形式为底部弹出框，规格一默认单选
* 查看购物车 点击进入商品详情

### 2、数据分析
* 商品：商品名称、规格、SKU主图、SKU缩略图、商品描述、原价、抢购价格、库存、已抢购数量、剩余数量、抢购时间
* 顾客：收货人姓名、电话、地址
* 购买：数量、配送方式
* 订单：订单编号、商品总价、运费、订单总价

### 3、数据模型

## 四、开发思路
### 1、界面构成
* 一期应用分成4个界面：【商品详情界面】【订单结算界面】【支付成功界面】【我的订单界面】

### 2、跳转关系
* 【商品详情界面】点击‘购买按钮’跳到【订单结算界面】，点击‘订单图标’跳到【我的订单界面】，点击‘一键拨号图标’弹出一键拨号浮层，点击‘购物车图标’弹出购物车浮层
* 【订单结算界面】点击‘提交订单’跳到【支付成功界面】，点击‘配送方式’切换到配送方式选择组件，点击‘所在地区’切换到城市选择组件
* 【支付成功界面】点击‘查看订单’跳到【我的订单界面】
* 【我的订单界面】点击订单列表组件切换到订单详情界面

### 3、组件划分
``` txt
└─APP：挂载整个应用
  ├─product-details：【商品详情界面】
  │ ├─page-title:页面标题
  │ ├─flash-sale:限时抢购
  │ ├─add-cart:添加购物车
  │ ├─shopping-cart:购物车
  │ └─buy-now:立即购买
  ├─payment：【订单结算界面】
  │ ├─distribution:配送方式
  │ ├─delivery-addr:收货地址
  │ └─place-order：提交订单
  ├─payment-success：【支付成功界面】
  │ └─delivery-info:收货信息
  ├─payment-success：【我的订单界面】
  │ ├─logistics-info:物流信息
  │ └─order-list:订单列表
  ├─view-order:查看订单
  ├─purchase-quantity:购买数量
  ├─productp-list:商品列表
  ├─TEXT:文本组件
  ├─GRAPHICAL:图形组件
  ├─CAROUSEL：轮播图组件
  ├─VIDEO：视频组件
  └─PHONE：一键拨号组件
  ```

### 4、文件结构
```txt
└─build：最终发布的代码存放位置
├─config：构建的配置文件
├─node_modules：npm加载的项目依赖模块
├─src：前端开发源码
│   ├─assets：图片等静态资源
│   ├─components：前端组件
│   ├─router：前端路由
│   ├─App.vue：应用的外层结构
│   └─main.js：应用的入口文件
├─static：静态资源目录
└─README.md：项目的说明文档
```
