<template>
  <div class="search-box">
    <a-form-model
      layout="inline"
      :model="searchForm"
      @submit="handleSubmit"
      @submit.native.prevent
    >
      <a-form-model-item label="检索关键字">
        <a-input
          v-model="searchForm.searchWord"
          placeholder="searchWord"
        ></a-input>
      </a-form-model-item>
      <a-form-model-item label="商品类目">
        <a-select
          show-search
          placeholder="请选择商品类目"
          style="width: 200px"
          allowClear
          @change="handleChange"
        >
          <a-select-option v-for="c in data" :key="c.id" :value="c.id">
            {{ c.name }}
          </a-select-option>
        </a-select>
      </a-form-model-item>
      <a-form-model-item>
        <a-button
          type="primary"
          html-type="submit"
        >搜索
        </a-button>
      </a-form-model-item>
    </a-form-model>
  </div>
</template>
<script>

export default {
  data() {
    return {
      searchForm: {
        searchWord: '',
        category: '',
      },
    };
  },
  props: ['data'],
  created() {
    // api.list().then((res) => {
    //   console.log(res.data);
    // });
  },
  methods: {
    // 表单提交触发
    handleSubmit() {
      this.$emit('submit', this.searchForm);
    },
    // 切换类目时触发的函数
    handleChange(val) {
      this.searchForm.category = val;
    },
  },
};
</script>
<style scoped>
  .search-box{
    margin: 20px;
  }
</style>
