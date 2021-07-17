<template>
  <div class="info_form">
    <el-form
      :inline="true"
      :model="formInline"
      class="demo-form-inline"
      @keyup.native.prevent
    >
      <el-form-item label="姓名">
        <el-input v-model="formInline.user" placeholder="你的名字？"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="onSubmit">提交</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>
<script>
export default {
  name: "InfoForm",
  data() {
    return {
      formInline: {
        user: "",
      },
    };
  },
  methods: {
    onSubmit() {
      this.$emit("submitInfo", this.formInline);
    },
  },
};
</script>

<style scoped>
</style>
