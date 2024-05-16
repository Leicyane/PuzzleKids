<template>
   <button class="btn">{{ title }}</button>
</template>
<script lang="js">
import Vue from 'vue'

export default Vue.extend({
  props: {
      title: String,
  },
  data() {
    return {}
  },
})
</script>
<style lang="scss" scoped>
.btn{
    width: 100%;
    height: 2.8rem;
    background-color: #9133B7;
    color: white;
    border: none;
    border-radius: 4px;
  }
</style>