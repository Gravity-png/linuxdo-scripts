<template>
  <div class="item">
    <div class="tit">{{ sort }}. 自定义论坛 logo</div>
  </div>
  <input
    type="text"
    v-model="textarea"
    @input="handleChange"
    placeholder="输入logo图链接，如: https://xxx.com/images.png"
  />
</template>

<script>
import $ from 'jquery'
export default {
  props: {
    value: {
      type: String,
      default: '',
    },
    sort: {
      type: Number,
      required: true,
    },
  },
  data() {
    return {
      textarea: this.value,
    }
  },
  watch: {
    value(newValue) {
      this.textarea = newValue
    },
  },
  methods: {
    handleChange() {
      this.$emit('update:value', this.textarea)
    },
    init() {
      $('.d-header .title a').html(`<img src="${this.textarea}">`)
    },
  },
  created() {
    if (this.textarea && this.textarea != '') {
      this.init()
    }
  },
}
</script>

<style lang="less" scoped>
.item {
  border: none !important;
}
</style>
