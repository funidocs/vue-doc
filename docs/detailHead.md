# DetailHead 详情头部组件

 为统一头部而诞生
## 使用
直接在vue文件中 写入（以下为完整案例）<br/>

## template里示例 

      <FuniDetailHead :option="detailHeadOption" ></FuniDetailHead>

## data 里示例 
   
        data(){
             detailHeadOption:{
                      no:'1234558',
                      title:'预售转现售详情',
                      btns:[{key:1,name:'打印',code:'print'},{key:2,name:'测试按钮',code:'test'}],
                      status:'有效'
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
            <td>no</td> 
            <td>编号</td>
            <td>''</td>
            <td>是</td>
            <td>'/chs/salesPrograms/list'</td>
         </tr> 
         <tr>
             <td>title</td> 
             <td>标题</td>
             <td>''</td>
             <td>是</td>
             <td>'/chs/salesPrograms/list'</td>
          </tr> 
           <tr>
               <td>btns</td> 
               <td>功能按钮</td>
               <td>[]</td>
               <td>否</td>
               <td>[{key:1,name:'打印',code:'print'},{key:2,name:'测试按钮',code:'test'}]</td>
            </tr>
             <tr>
                 <td>status</td> 
                 <td>状态</td>
                 <td>''</td>
                 <td>否</td>
                 <td>'有效'</td>
              </tr>
       </tbody>
   </table>
   




