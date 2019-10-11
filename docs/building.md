# 楼栋组件
 可视化查看房屋基本数据的组件，支持列表 和 树 模式，树模式支持检索
  <br>该组件由2个组件组合而成（buildingList，building）  
  buildingList：楼栋组件的框架
  building：楼栋房屋的具体展示组件
## 使用
直接在vue文件中 写入（以下为完整案例）<br/>

## template里示例 
    <buildingList
      :buildingData="buildingData"
      mode="tree"
      placeholder="预售证号"
      :headShow="true"
      :explainShow="true"
      @getBuildingInfo="_getBuildingInfo">
      <template v-slot:building>
        <building :houseData="houseData"></building>
      </template>
    </buildingList>
## data 里示例 
   
        data(){
            buildingData:[
              {
                id:1,
                name:'1栋',
                unitList:[
                  {id:1,name:'1单元'},
                  {id:2,name:'2单元'},
                ],
              },
              {
                id:2,
                name:'2栋',
                unitList:[
                  {id:1,name:'1单元'},
                  {id:2,name:'2单元'},
                  {id:3,name:'3单元'},
                ],
              },
              {
                id:3,
                name:'3栋',
                unitList:[
                  {id:1,name:'1单元'},
                  {id:2,name:'2单元'},
                ],
              },
              {
                id:4,
                name:'4栋',
                unitList:[
                  {id:1,name:'1单元'},
                  {id:2,name:'2单元'},
                  {id:3,name:'3单元'},
                ],
              },
              {
                id:5,
                name:'5栋',
                unitList:[
                  {id:1,name:'1单元'},
                  {id:2,name:'2单元'},
                  {id:3,name:'3单元'},
                ],
              },
            ],
            houseData: [
                      {
                        floor: 1,
                        houses: [
                          {
                            no: '1101',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                          {
                            no: '2102',
                            area: '102.21',
                            status: 'normal',
                          },
                          {
                            no: '3103',
                            area: '102.21',
                            status: 'normal',
                          },
                          {
                            no: '4104',
                            area: '102.21',
                            price: '132.21',
                            status: 'shut',
                          },
                          {
                            no: '5105',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                        ],
                      },
                      {
                        floor: 2,
                        houses: [
                          {
                            no: '2101',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                          {
                            no: '2102',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                          {
                            no: '2103',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                          {
                            no: '2104',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                          {
                            no: '2105',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                        ],
                      },
                      {
                        floor: 2,
                        houses: [
                          {
                            no: '3101',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                          {
                            no: '2102',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                          {
                            no: '2103',
                            area: '102.21',
                            price: '132.21',
                            status: 'impawn',
                          },
                          {
                            no: '2104',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                          {
                            no: '2105',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                        ],
                      },
                      {
                        floor: 2,
                        houses: [
                          {
                            no: '4101',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                          {
                            no: '2102',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                          {
                            no: '2103',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                          {
                            no: '2104',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                          {
                            no: '2105',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                        ],
                      },
                      {
                        floor: 2,
                        houses: [
                          {
                            no: '5101',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                          {
                            no: '2102',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                          {
                            no: '2103',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                          {
                            no: '2104',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                          {
                            no: '2105',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                        ],
                      },
                      {
                        floor: 2,
                        houses: [
                          {
                            no: '6101',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                          {
                            no: '2102',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                          {
                            no: '2103',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                          {
                            no: '2104',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                          {
                            no: '2105',
                            area: '102.21',
                            price: '132.21',
                            status: 'protocol',
                          },
                        ],
                      },
                      {
                        floor: 2,
                        houses: [
                          {
                            no: '7101',
                            area: '102.21',
                            status: 'protocol',
                          },
                          {
                            no: '2102',
                            area: '102.21',
                            status: 'private',
                          },
                          {
                            no: '2103',
                            area: '102.21',
                            status: 'private',
                          },
                          {
                            no: '2104',
                            area: '102.21',
                            status: 'protocol',
                          },
                          {
                            no: '2105',
                            area: '102.21',
                            status: 'protocol',
                          },
                        ],
                      },
                    ],
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
          <td>buildingData</td> 
          <td>楼栋和单元的数据</td>
          <td>[]</td>
          <td>是</td>
          <td>参考示例data中的buildingData</td>
       </tr>
         <tr>
             <td>mode</td> 
             <td>左侧楼栋列表展示模式</td>
             <td>tree</td>
             <td>否</td>
             <td>list | tree</td>
          </tr>
           <tr>
               <td>placeholder</td> 
               <td>树模式需要提交一个placeholder</td>
               <td>''</td>
               <td>否</td>
               <td>'请输入预售证号'</td>
            </tr>
           <tr>
               <td>headShow</td> 
               <td>是否显示右侧列表头部</td>
               <td>true</td>
               <td>否</td>
               <td>true | false</td>
            </tr>
           <tr>
               <td>explainShow</td> 
               <td>是否显示右侧列表头部(颜色标识部分)</td>
               <td>true</td>
               <td>否</td>
               <td>true | false</td>
            </tr>
           <tr>
               <td>houseData</td> 
               <td>房屋数据</td>
               <td>[]</td>
               <td>否</td>
               <td>数据格式参考 data 中的 houseData</td>
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
             <td>getBuildingInfo</td> 
             <td>选择了某一个单元后触发</td>
             <td>unitData 包含单元信息</td>
          </tr> 
        </tbody>
    </table>





