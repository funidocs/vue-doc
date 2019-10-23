# Curd 表格

基于ant Design Vue 实现可配置化表格，支持动态配置列头拖拽、配置可显示列、自动记忆当前表格配置等功能

## 使用
直接在vue文件中 写入（以下为完整案例）<br/>

## template里示例 

      <funi-curd @btnClick="_btnClick" ref="curd" :option="curdOption" :data="tableList" :filterForm="filterForm"></funi-curd>

## data 里示例 
   
        data(){
         return {
           filterForm:{a:111},
           cardTab: [
             {
               key: 'query',
               // tab: '数据查询',
               scopedSlots: { tab: 'customRender'}
             },
             {
               key: 'count',
               tab: '数据统计',
             },
           ],
           listType: 'query',
           curdOption:{
             api:'/chs/salesPrograms/list',
             method:'post',
             scroll:{x:'150%'},
             selectionType:'radio',
             columnFilterShow:true,
             pagination:true,
             title:'销售方案管理',
             selectionShow:true,//是否显示复选框
             requestOtherParams:{type:'todo'},
             columns: [
               {
                 title: '销售方案号1',
                 dataIndex: 'sellNo',
                 fixed: 'left',
                 width: 50,
                 scopedSlots: { customRender: 'id' },
                 align: 'center',
                 className:'allowDrag',
                 customCell:record => {
                   return {
                     on: { // 事件
                       click: () => {
                         console.log('点击了列',record);
                       }
                     },
                   }
                 }
               },
               {
                 title: '许可证号',
                 dataIndex: 'licenseNo',
                 align: 'center',
                 className:'allowDrag',
               },
               {
                 title: '状态',
                 dataIndex: 'status',
                 align: 'center',
                 className:'allowDrag',
               },
               {
                 title: '业务状态',
                 dataIndex: 'businessStatus',
                 align: 'center',
                 className:'allowDrag',
               },
               {
                 title: '销售类型',
                 dataIndex: 'saleType',
                 key: 'state',
                 // scopedSlots: { customRender: 'status' },
                 align: 'center',
                 className:'allowDrag',
                 customRender: (text, row, index) => {
                   if (text  == 3) {
                     return <span>
                     <a-icon type="minus-circle" style="color:red;margin-right:3px;"/>{text}
                       </span>
                   }else if(text == 2){
                     return <span>
                     <a-icon type="check-circle" style="color:green;margin-right:3px;"/>{text}
                       </span>
                   } else{
                     return text
                   }
                 }
               },
               {
                 title: '开发企业名称',
                 dataIndex: 'companyName',
                 align: 'center',
                 className:'allowDrag',
               },
               {
                 title: '项目名称',
                 dataIndex: 'projectName',
                 className:'allowDrag',
                 align: 'center'
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
             btns:[
               {label:'许可证编辑',name:'edit',icon:'edit',disabled:false},
             ],
             action:[
               {label:'初审',name:'sc',disabled:false},
               {label:'编辑',name:'edit',disabled:false}
             ]
           },
           tableList:[]
           }
      
## methods 里示例           
         methods: {
              _btnClick(obj){
                console.log('_btnClick',obj);
                if(obj.name === 'add'){
                  this.$refs.createModal.show();
                }
              }
## API              
<table>
  <thead>
      <tr>
            <th>名称</th> 
            <th>说明</th>
            <th>默认值</th>
            <th>必填</th>
            <th>示例</th>
      </tr>
  </thead>
  <tbody>
      <tr>
          <td>option</td> 
          <td>当前表单的配置 类型为Object</td>
          <td>{}</td>
          <td>是</td>
          <td>参考代码示例</td>
       </tr>
     <tr>
         <td>data</td> 
         <td>支持手动传入表格数据显示，格式请参考示例</td>
         <td>[]</td>
         <td>否</td>
         <td>参考代码示例</td>
      </tr>
           <tr>
               <td>filterForm</td> 
               <td>筛选JSON对象 传入就会带上该对象请求api 重新渲染表格</td>
               <td>{}</td>
               <td>否</td>
               <td>{name:'张三'}</td>
            </tr>  
     </tbody>
 </table>
 
## option对象可以配置的参数       

  <table>
    <thead>
        <tr>
            <th>名称</th> 
            <th>说明</th>
            <th>默认值</th>
            <th>必填</th>
            <th>示例</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>api</td> 
            <td>该表格请求后端数据的api</td>
            <td>''</td>
            <td>是</td>
            <td>'/chs/salesPrograms/list'</td>
         </tr> 
         <tr>
             <td>method</td> 
             <td>该表格请求后端数据的方法</td>
             <td>'post'</td>
             <td>否</td>
             <td>'post'或 'get'</td>
          </tr> 
         <tr>
             <td>scroll</td> 
             <td>配置滚动条，一般在需要用到固定列的时候需要配置</td>
             <td>{}</td>
             <td>否</td>
             <td>{x:'150%',y:'150px'}</td>
          </tr> 
           <tr>
               <td>selectionType</td> 
               <td>配置表格是否可以选中： 单选|多选|无</td>
               <td>''</td>
               <td>否</td>
               <td>'radio' | ‘checkbox’</td>
            </tr>
           <tr>
               <td>columnFilterShow</td> 
               <td>是否显示 过滤列</td>
               <td>true</td>
               <td>否</td>
               <td>true | false</td>
            </tr>
           <tr>
               <td>pagination</td> 
               <td>是否显示 分页</td>
               <td>true</td>
               <td>否</td>
               <td>true | false</td>
            </tr> 
           <tr>
               <td>columns</td> 
               <td>列配置-参考ant官网columns配置</td>
               <td>[]</td>
               <td>是</td>
               <td>true | false</td>
            </tr>
           <tr>
               <td>btns</td> 
               <td>表格上方显示的操作按钮</td>
               <td>[]</td>
               <td>否</td>
               <td>[{label:'许可证编辑',name:'edit',icon:'edit',disabled:false}]</td>
            </tr>   
       </tbody>
   </table>
   
## 事件

  <table>
    <thead>
        <tr>
            <th>事件</th> 
            <th>说明</th>
            <th>回调参数</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>_btnClick</td> 
            <td>当前点击的操作按钮的回调函数</td>
            <td>obj(包含当前点击按钮的信息)</td>
         </tr> 
       </tbody>
   </table>





