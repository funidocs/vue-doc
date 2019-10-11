# FuniProcessBottomBtn -表单页底部切换组件
	当currentStep大于0时，显示上一步按钮
	当currentStep等于submitStep时，显示提交按钮，隐藏下一步按钮。

#### 参数
| 入参        | 类型   |  默认值  | 说明  |
| --------   | -----:  | :----:  |:----:  |
| currentStep      | number   |   0     | 当前步骤    |
| submitStep      | number   |  0     | 提交步骤    |

#### 事件
| 方法           |  返回         | 说明           |  示例   |
| --------      |  :----:        |      :----:  | :----:  |
| clickBtnEvent |    object      | 按钮监听事件   | {type:'nextStep'}|

#### JS代码
```javascript
//按钮点击监听事件
_clickBtnEvent(obj){
    switch(obj.type){
		case 'nextStep':
		break;
	}
}
```

#### vue代码
```html
<funi-process-bottom-btn :current-step="1" :submit-step="1" @clickBtnEvent="_clickBtnEvent">
</funi-process-bottom-btn>
```



### End