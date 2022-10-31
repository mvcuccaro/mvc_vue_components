<template>
<div>
  <div v-if="visible">
    <slot></slot>
  </div>
</div>
</template>

<script>
export default {
  name: "dynalist_item.vue",
  props:['title', 'subtitle'],
  data(){
    return {
      visible: false
    }
  },
  mounted() {
    this.$parent.$emit('item-mounted', this)
  }
}
</script>

<style scoped>

</style>