

基于ant design vue 的表单装饰器. 以json形式配置表单,兼容原来的参数，无修改，扩展部分功能.

> 说明：
>
> 使用前最好先熟悉and design vue 官方的[Form文档](https://vue.ant.design/components/form-cn/)


### Demo

```vue
<template>
  <funi-form ref="funi-form" @get-form="res => (form = res)" v-bind="formData">
    <template #curd>
      <funi-curd
        :option="curdOption"
        :data="tableList"
        :filterForm="filterForm"
        v-decorator="curdDecorator"
      ></funi-curd>
    </template>
  </funi-form>
</template>

<script>
const responsive = {
  colProps: { span: 12 },
};
export default {
  data() {
    return {
      form: null,
      formData: {
        responsive: {
          colProps: { span: 12 },
          itemProps: {
            labelCol: { span: 12 },
            wrapperCol: { span: 12 },
          },
        },
        schema: [
          {
            field: 'name',
            type: 'a-input',
            default: 'Beautify',
            label: '名字',
            rowId: '1',
            ...responsive,
            rules: [{ required: true, message: '请输入姓名' }],
          },
          {
            field: 'age',
            type: 'a-input',
            default: 20,
            label: '年龄',
            rowId: '1',
            ...responsive,
            rules: [{ required: true, message: '请输入年龄' }],
          },
          {
            field: 'gender',
            type: 'a-input',
            label: '性别',
            ...responsive,
            rowId: '2',
          },
          {
            field: 'country',
            type: 'funi-label',
            label: '国籍',
            default: 'China',
            ...responsive,
            rowId: '2',
          },
          {
            field: 'date',
            type: 'funi-search',
            label: '全局组件使用',
            props: {},
            itemProps: {
              wrapperCol: { span: 20 },
            },
          },
          {
            label: '插槽使用',
            slot: 'curd',
            itemProps: {
              wrapperCol: { span: 20 },
            },
          },
        ],
      },
      filterForm: { a: 111 },
      curdOption: {
        api: '/chs/salesPrograms/list',
        method: 'post',
        scroll: { x: '150%' },
        selectionType: 'radio',
        columnFilterShow: true,
        pagination: true,
        title: '销售方案管理',
        selectionShow: true, //是否显示复选框
        requestOtherParams: { type: 'todo' },
        columns: [
          {
            title: '销售方案号',
            dataIndex: 'sellNo',
            fixed: 'left',
            width: 50,
            scopedSlots: { customRender: 'id' },
            align: 'center',
            className: 'allowDrag',
            customCell: record => {
              return {
                on: {
                  // 事件
                  click: () => {
                    console.log('点击了列', record);
                  },
                },
              };
            },
          },
          {
            title: '许可证号',
            dataIndex: 'licenseNo',
            align: 'center',
            className: 'allowDrag',
          },
          {
            title: '状态',
            dataIndex: 'status',
            align: 'center',
            className: 'allowDrag',
          },
          {
            title: '业务状态',
            dataIndex: 'businessStatus',
            align: 'center',
            className: 'allowDrag',
          },

          {
            title: '销售类型',
            dataIndex: 'saleType',
            key: 'state',
            // scopedSlots: { customRender: 'status' },
            align: 'center',
            className: 'allowDrag',
            customRender: (text, row, index) => {
              if (text == 3) {
                return (
                  <span>
                    <a-icon type="minus-circle" style="color:red;margin-right:3px;" />
                    {text}
                  </span>
                );
              } else if (text == 2) {
                return (
                  <span>
                    <a-icon type="check-circle" style="color:green;margin-right:3px;" />
                    {text}
                  </span>
                );
              } else {
                return text;
              }
            },
          },
          {
            title: '开发企业名称',
            dataIndex: 'companyName',
            align: 'center',
            className: 'allowDrag',
          },
          {
            title: '项目名称',
            dataIndex: 'projectName',
            className: 'allowDrag',
            align: 'center',
          },
          {
            title: '预售范围',
            dataIndex: 'presellRange',
            align: 'center',
            width: '150px',
            // scopedSlots: { customRender: 'action' },
          },
          {
            title: '区域',
            dataIndex: 'region',
            align: 'center',
            width: '150px',
            // scopedSlots: { customRender: 'action' },
          },
          {
            title: '销售面积(m²)',
            dataIndex: 'sellArea',
            align: 'center',
            width: '150px',
            // scopedSlots: { customRender: 'action' },
          },
          {
            title: '销售方式',
            dataIndex: 'sellMode',
            align: 'center',
            width: '150px',
            // scopedSlots: { customRender: 'action' },
          },
          {
            title: '生效时间',
            dataIndex: 'takeDate',
            align: 'center',
            width: '150px',
            // scopedSlots: { customRender: 'action' },
          },
        ],
        btns: [{ label: '许可证编辑', name: 'edit', icon: 'edit', disabled: false }],
        action: [{ label: '初审', name: 'sc', disabled: false }, { label: '编辑', name: 'edit', disabled: false }],
      },
      tableList: [],
      curdDecorator: ['curd'],
    };
  },
  created() {},
  methods: {},
};
</script>

```

### 网格布局

布局配置可以对整个表单进行配置也可以针对某个item进行配置。

##### 全局配置

```vue
formData: {
  responsive: {
    colProps: { span: 12 },
    itemProps: {
      labelCol: { span: 12 },
      wrapperCol: { span: 12 },
    },
  },
  schema: [...],
}
```

##### 局部配置

```vue
formData: {
  schema: [
    {
      field: 'name',
      type: 'a-input',
      default: 'Beautify',
      label: '名字',
      rowId: '1',
			colProps: { span: 12 },
    	itemProps: {
      	labelCol: { span: 12 },
      	wrapperCol: { span: 12 },
    	},
      rules: [{ required: true, message: '请输入姓名' }],
    }],
}
```


>  当全局配置和局部配置同事存在时，局部覆盖全局




### API

#### FormProps

|       参数        |                             说明                             |   类型   |
| :---------------: | :----------------------------------------------------------: | :------: |
| createFormOptions | 创建表单时携带配置项（详情见[Ant Form API](https://vue.ant.design/components/form-cn/#API)） |  Object  |
|       size        |       默认表单内组件的size,统一配置,也可以单独配置覆盖       |  String  |
|    responsive     |                  表单项的响应布局统一配置项                  |  Object  |
|      schema       |                    表单配置（详情见下方）                    |  Array   |
|   transformDate   |                          时间格式化                          | Function |



#### schema

|       参数        |                             说明                             |   类型   |
| :---------------: | :----------------------------------------------------------: | :------: |
|       field       |                 输入控件唯一标志==（必填）==                 |  String  |
|      default      |                         表单域默认值                         |    -     |
|       type        |    控件类型（全局注册组件有用，局部注册的组件请使用slot）    |  String  |
|       label       |                            标签名                            |  String  |
|       rowId       | 当需要多控件一行展示时，配置相同rowId，同时配置对应colProps（[见网格配置](#FormProps)）;若非需要同一行展示多列表单域，可忽略。 |  String  |
|       rules       |                           校验规则                           |  Array   |
|     colProps      |                           布局配置                           |  Object  |
|     itemProps     |                           布局配置                           |  Object  |
|       props       |                     自定义组件时，传值用                     |  Object  |
|       slot        |                插槽name，详情见[Demo](#Demo)                 |  String  |
|      `show`       |                控制表单域是否展示，详情见下方                | Function |
|       `on`        |                  表单域时间监听，详情见下方                  | Function |
|      `when`       |               表单任意值变化时触发，详情见下方               | Function |
| getValueFromEvent | 见[Ant_v-decorator_options.getValueFromEvent](https://vue.ant.design/components/form-cn/#API) |          |
|     normalize     | 见[Ant_v-decorator_options.normalize](https://vue.ant.design/components/form-cn/#API) |          |
|     preserve      | 见[Ant_v-decorator_options.preserve](https://vue.ant.design/components/form-cn/#API) |          |
|       rules       | 见[Ant_v-decorator_options.rules](https://vue.ant.design/components/form-cn/#API) |          |
|      trigger      | 见[Ant_v-decorator_options.trigger](https://vue.ant.design/components/form-cn/#API). 默认值: output |          |
|   validateFirst   | 见[Ant_v-decorator_options.validateFirst](https://vue.ant.design/components/form-cn/#API) |          |
|  validateTrigger  | 见[Ant_v-decorator_options.validateTrigger](https://vue.ant.design/components/form-cn/#API) |          |
|   valuePropName   | 见[Ant_v-decorator_options.valuePropName](https://vue.ant.design/components/form-cn/#API) |          |

**show**

```vue
// 输入框
{
  field: 'name',
  type: 'input',
  label: '商品名称',
  props: {
    placeholder: '请输入商品名称'
  },
  show: (data) => {
    return true/false
  }
}
```

**on**

```vue
// 数值输入框
{
  field: 'num',
  type: 'input-number',
  label: '商品数量',
  props: {
    style: { width: '200px' },
    min: 1,
    max: 10,
    placeholder: '请输入商品数量'
  },
  on: {
    change: (value) => {
      console.log('input-number-changed', value)
    },
		someEvent: (v) => {
			//...
		}
  },
  ...createRules('商品价格不能为空')
},
```

**when**

```vue
// 输入框
{
  field: 'name',
  type: 'input',
  label: '商品名称',
  props: {
    placeholder: '不可以输入'
  },

	// 通过setItem可动态配置表单域
  when: ({ formData, setItem }) => {
    const isInput = formData.isSetName === '2'
    setItem({
      props: {
        disabled: !isInput,
        placeholder: isInput ? '可以输入' : '不可以输入'
      }
    })
  }
}
```



#### 表单操作

设置表单值通过ref引用**setFieldsValue**，获取校验后的表单值通过监听**submit**事件，如果不需要校验，可直接通过`this.form.getFieldsValue()`获取，其他事件也可直接通过`this.form`调用Ant官方方法。
