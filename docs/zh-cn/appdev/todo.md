## Vue前端/APP模板
- [ ] flames-pda本地接口调用日志文件上传，异常上报；——张港港
- [ ] flames-pda项目增加截屏插件；——张港港
- [x] MacAddress插件上传npm及cordova;
- [x] 文件夹js（`langs\routers`）自动导入；前端按配置打包不同`routers`及`views`

## PDA/客户端优化异常排查设计
- 统一同一个后端系统对应一个PDA/客户端
    - 统一管理，要求新需求逻辑必须兼容和自洽，会引起冲突的需求，开发务必慎重，向上反馈，需要服务端和Leader确认方案后才能通过！！！对于影响生产的异常，临时处理方案之后，也需要进行优化 —— 刘新伟
- 支持服务器地址修改
- 异常提示信息：区分接口/本地异常报错，提示
- 统一接口处理业务逻辑判断
- 区分工厂/客户的逻辑判断需走系统参数（getSystemParams）/数据字典(AJ-report)/系统参数（FLAMES）
- MES 2.0服务端接口日志
- 非MES2的接口报错统一通过addClientMessage接口上传日志
- Flames 客户端异常日志 上报功能
- 模拟数据-框架API设计-API文档—多项目代码迁移与合并-分模块打包

## 旧看板/PDA异常维护，优化源码管理
- 汇总不同工厂的源码项目地址
- gitlab group分组管理源码，新项目上gitlab, 旧项目有新增需求也可以视情况迁移
  ref: http://10.12.5.188:10023/appdev/mes3/snippets/10
- 错误提示中添加源码路径标识+版本（谢文俊）

## 报表中心设计
- [x] 产品选型: AJ-Report
- [ ] 代码生成分析
- [ ] 多系统集成部署

## 开发流程优化
- [ ] Gitlab runner for Android / Cordova —— 谢文俊
- [ ] 优化237下载中心(nodejs) —— ？
  
## Android统一PDA（缺少策划梳理）
- [ ] 统一工厂、客户选择
- [ ] 统一上料模块
- [x] MES2新模板项目：transferPDA 
- [x] MES3项目: flames PDA/client
- [ ] wms3.0项目：刘新伟
- [ ] wms成品仓/GB/WIP —— 陈流勇
  
## Admin Projects优化迭代
- [Vue Admin Beautiful](https://chu1204505056.gitee.io/admin-pro/#/login)

关注下这个项目的，tabs数据缓存的具体实现，其他都还好~

## RestClient or apiPost?

接口测试框架/脚本(restClient in browser and integrated with tester frameworks, like jmeter or httpRunner? )

https://www.apipost.cn/ based on postman.

RestClient doesn't work in <https://vscode.dev/> yet.

ref: https://code.visualstudio.com/api/extension-guides/web-extensions