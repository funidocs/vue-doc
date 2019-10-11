# FuniAuditButtomBtn

#### 参数
| 入参        | 类型   |  默认值  | 说明  |
| --------   | -----:  | :----:  |:----:  |
| btns      | array   |   []     | 按钮集合    |

##### btn对象参数
| 入参        | 类型   |  默认值  | 说明  |
| --------   | -----:  | :----:  |:----:  |
| key        |   string   |   无   | 按钮关键字，例 submit,cancel   |
| name       |   string    |  无  | 按钮文本  |
| type       |   string    |  default  | ant提供的按钮类型  |
| icon       |   string    |  无  | ant提供的icon  |

#### 事件
| 方法           |  返回         | 说明           |  示例   |
| --------      |  :----:        |      :----:  | :----:  |
| clickBtnEvent |    object      | 按钮监听事件   | {type:'submit'}|

#### JS代码
```javascript
//按钮集合
btns:[{
		name:'回退',
		key:'key1',
		icon:'copy'
	},{
		name:'退件',
		key:'key2',
		icon:'delete'
	},{
		name:'不予受理',
		key:'key3',
		icon:'edit'
	},{
		name:'同意',
		type:'primary',
		key:'key4',
		icon:'form'
	}];

//按钮点击监听事件
_clickBtnEvent(obj){
    switch(obj.type){
		case 'submit':
		break;
	}
}
```

#### vue代码
```html
<funi-audit-buttom-btn :btns="btns" @clickBtnEvent="_clickBtnEvent"></funi-audit-buttom-btn>
```



### End