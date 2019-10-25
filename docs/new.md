
> .
> 开发说明
> .

# 关于工程

## 目录结构

```bash
src
├── App.vue     # 主文件
├── apps        # 所有子系统
   ├── ccs      # 子系统名
      ├── config.js      # 子系统字符串常量存储位置 如:api地址
      ├── router.json    # 开发阶段的路由配置 
      ├── store.js       # 状态管理
      ├── pages          # 子系统所有页面
         ├── common          # 子系统系统级公用资源
            ├── assets          # 资源文件
            ├── components      # 子系统系统级公用组件
            ├── modal           # 子系统系统级公用弹窗
         ├── gov             # 政务端页面
         ├── org             # 开发企业端页面
         ├── oper            # 运营端
         ├── conf            # 配置端
         ├── suy             # 测绘端
         ├── bank            # 金融端
         ├── brok            # 经纪端
         ├── rent            # 租赁端

├── assets      # 资源文件
├── components  # 自定义组件
├── config      # 配置
├── layouts     # 布局
├── main.js     # 主文件
├── pages       # 具体页面
├── router      # 路由配置
├── store       # vuex 状态
└── utils       # 工具库

```
### 所有子系统名称

1. ccs 配置管理
2. pro 项目管理
3. svy 测绘成果管理
4. hse 楼盘表管理
5. chs 商品房交易管理
6. shs 存量房交易管理
7. rent 房屋租赁管理
8. hm 房屋抵押管理
9. trs 交易产权管理
10. pct 从业主体管理
11. fps 预售资金监管
12. fsh 存量房资金监管


### 一点要求

1. 整个河南房屋交易生态平台根据功能模块采用拆分为子系统的方式进行独立开发(生产会集成一个系统打包发布)
2. 各终端页面在对应目录下开发，终端和终端之间文件不能引用，有公用的必须放common里面(为后面各终端独立部署做准备)
3. 路由name必须加子系统名称且不能重复， 如： 配置系统 名称为 ccs， 路由name->  CCSxxxx
4. 子系统中的字符串常量、枚举 放config.js中， 使用方式: this.$config.ccs.xxx(ccs为子系统名，xxx为自己定义的路径)
5. console.log统一用 this.f.c('内容') 代替，方便后期一键关闭log打印
6. 命名规则：
   * 6.1 公用组件名大驼峰 如: FuniCurd
   * 6.2 目录名、文件名统一小驼峰 如: index.vue / devQuery.vue 
7. 如有系统级公用组件、js库 的增加， 需先在自己本地测试通过后 提交 @李强 统一添加至主工程仓库，再通知大家执行:yarn run update
8. 提供有2个.vue文件模板(有不明白使用方法的可 @古加文 @蒋韩肖)
   * 8.1 普通页.vue  [WebStorm](https://github.com/funidocs/vue-doc/blob/master/docs/webStormModal.txt)  [VSCode](https://github.com/funidocs/vue-doc/blob/master/docs/vscodeModal.json)
   * 8.2 列表页.vue  [WebStorm](https://github.com/funidocs/vue-doc/blob/master/docs/webStormList.txt)  [VSCode](https://github.com/funidocs/vue-doc/blob/master/docs/vscodeModal.json)
9. .vue文件顶部 必须注释 页面所属路径说明 如: 
   ``` <!-- 项目管理子系统-开发项目查询-项目备案设立-项目基本信息tag --> ```
10. 写自定义组件之前先看 demo->demo内是否已存在, 提供给整个系统使用的组件先本地测试通过后 @李强 加入主工程仓库，再通知大家更新。 
11. 项目分为母工程和子工程，两者整体目录结构一样，我们开发都是基于子工程，最终打包上线的时候只会把子工程下src/apps/子系统名 内文件进行整合，所有非子系统文件目录下的改动都不会在生产环境生效，切记在非子系统目录下增改，如有改动需求在群里面 @李强  统一修改。
12. yarn run update 命令 用于更新母工程文件到本地(除src/apps外其他会全部覆盖)
