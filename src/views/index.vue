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
          <option v-for="option in options" v-bind:value="option.value" :key="option">
            {{ option.text }}
          </option>
      </select>
    </div>
      <div class="text-muted text-left mb-4 tip">
        *必須為數字
      </div>
  </div>

  <!-- 表格 -->
  <div class="tab-pane fade show active container" id="pills-history" role="tabpanel" aria-labelledby="pills-history-tab">
    <div class="table-responsive">
      <table class="table table-striped">
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
          <tr>
            <td class="">
              2020-12-17
            </td>
            <td>
              2020-12-30
            </td>
            <td>
              31066814-5ae0-400c-a1a5-c8e94cbc8381
            </td>
            <td>
              <div class=""><i class="fas fa-check-circle"></i></div>
            </td>
            <td>
              <div class=""><i class="fas fa-trash"></i></div>
            </td>
          </tr>
          <tr>
            <td class="">
              2020-12-17
            </td>
            <td>
              2020-12-30
            </td>
            <td>
              31066814-5ae0-400c-a1a5-c8e94cbc8381
            </td>
            <td>
              <div class=""><i class="fas fa-times-circle"></i></div>
            </td>
            <td>
              <div class=""><i class="fas fa-trash"></i></div>
            </td>
          </tr>
          <tr>
            <td class="">
              2020-12-17
            </td>
            <td>
              2020-12-30
            </td>
            <td>
              31066814-5ae0-400c-a1a5-c8e94cbc8381
            </td>
            <td>
              <div class=""><i class="fas fa-times-circle"></i></div>
            </td>
            <td>
              <div class=""><i class="fas fa-trash"></i></div>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</div>


</div>
</template>

<script>

export default {
  name: "",
  props: {},
  data: function() {
    // 資料
    return {
      src: "" ,//追蹤 store用
      selected: 'A',
        options: [
        { text: '全部', value: 'A' },
        { text: '使用中', value: 'B' },
        { text: '未使用', value: 'C' }
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