<template>
<div>
  <div class="text-left header">
    <div class="container">賓果後台管理</div>
  </div>

  <div class="container">
    <div class="form-group mt-4">
      <label for="lname" class="d-inline-block">新增</label>
      <input type="text" class="form-control mx-sm-3 d-inline-block" placeholder="筆數">
      <label for="lname" class="d-inline-block">筆序號</label>
      <button type="submit" class="btn btn-primary mb-2 d-inline-block ml-2 mr-5">新增</button>

      <select v-model="selected" class="form-control filterSelect d-inline-block">
          <option v-for="(option, i) in options" v-bind:value="option.value" :key="i">
            {{ option.text }}
          </option>
      </select>
      <button type="button" class="btn btn-info float-right downloadBtn">下載</button>
    </div>
      <div class="text-muted text-left mb-4 tip">
        *必須為數字
      </div>
  </div>

  <!-- 表格 -->
  <div class="tab-pane fade show active container" id="pills-history" role="tabpanel" aria-labelledby="pills-history-tab">
    <div class="table-responsive">
      <table class="table table-striped text-center">
        <thead>
          <tr>
            <th scope="col">開始日期</th>
            <th scope="col">預計過期日</th>
            <th scope="col">序號</th>
            <th scope="col">是否啟用</th>
            <th scope="col">刪除</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(item, i) in itemList" :key="i">
            <td class="">
              {{ item.created_date }}
            </td>
            <td>
              {{ item.end_date }}
            </td>
            <td>
              {{ item.token }}
            </td>
            <td>
              <div v-if="item.used==='true'">
                <i class="fas fa-check-circle"></i>
              </div>
              <div v-else>
                <i class="fas fa-times-circle"></i>
              </div>
            </td>
            <td>
              <div><i class="fas fa-trash"></i></div>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</div>

</template>

<script>
import $ from 'jquery'
export default {
  name: "",
  props: {},
  data: function() {
    // 資料
    return {
      src: "" ,//追蹤 store用
      selected: 'all',
        options: [
        { text: '全部', value: 'all' },
        { text: '使用中', value: 'used' },
        { text: '未使用', value: 'not_used' }
      ],

      itemList:[
        {
          created_date: '2020-12-18',
          end_date: '2020-12-30',
          token: 'fd4131c2-7247-4211-bb3c-cc0c79b5aea0',
          used: 'true'
        },
        {
          created_date: '2020-12-20',
          end_date: '2021-01-30',
          token: 'fd4131c2-7247-4211-bb3c-cc0c79b5aea0',
          used: 'false'
        },
        {
          created_date: '2020-12-10',
          end_date: '2021-02-03',
          token: 'fd4131c2-7247-4211-bb3c-cc0c79b5aea0',
          used: 'true'
        }
      ]
    };
  },
  components: {
    // f2ecommonMask //1.個別引入
  },
  watch: {
    //監聽值
  },
  computed: {
    //相依的資料改變時才做計算方法
  },
  methods: {
    // 初始

  },
  //BEGIN--生命週期
  beforeCreate: function() {
    //實體初始化
  },
  created: function() {
    //實體建立完成。資料 $data 已可取得，但 $el 屬性還未被建立。
    this.src = this.$options.__file ;
  },
  beforeMount: function() {
    //執行元素掛載之前。
  },
  mounted: function() {
    //元素已掛載， $el 被建立。
    console.log(window.customElements)

    // 下載功能
    let downloadBtn = document.querySelector(".downloadBtn");
    downloadBtn.addEventListener("click", downloadFile);
    function downloadFile() {
      //藉型別陣列建構的 blob 來建立 URL
      let fileName = "fileName.csv";
      const data = getRandomData();
      let blob = new Blob([data], {
        type: "application/octet-stream"
      });
      var href = URL.createObjectURL(blob);
      // 從 Blob 取出資料
      var link = document.createElement("a");
      document.body.appendChild(link);
      link.href = href;
      link.download = fileName;
      link.click();
      console.log('blob:',blob)
      console.log('href:',href)
    }

    function download(){ 
      axios({ 
          url:'https://source.unsplash.com/random/500x500', 
          method:'GET', 
          responseType: 'blob' 
      }) 
      .then((response) => { 
            const url = window.URL 
            .createObjectURL(new Blob([response.data])); 
              const link = document.createElement('a'); 
              link.href = url; 
              link.setAttribute('download', 'image.jpg'); 
              document.body.appendChild(link); 
              link.click(); 
        }) 
      } 

    //假資料
    function getRandomData() {
    var header = "RandomHeader";
    var data = "";
      for (let i = 0; i < 5; i++) {
        for (var j = 0; j < 2; j++) {
          if (j > 0) {
            data = data + ",";
          }
          data = data + "Item" + i + "_" + j;
        }
      }
      return header + data;
    }
  },
  beforeUpdate: function() {
    //當資料變化時被呼叫，還不會描繪 View。
  },
  updated: function() {
    //當資料變化時被呼叫，還不會描繪 View。
  },
  beforeDestroy: function() {
    //實體還可使用。
  },
  destroyed: function() {
    //實體銷毀。
  }
  //END--生命週期
};
</script>

<style lang="scss" scoped>
</style>