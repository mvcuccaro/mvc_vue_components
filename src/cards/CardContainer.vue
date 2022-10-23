<template>
    <div class="cards_container">
      <slot></slot>
    </div>
</template>

<script>
export default {
  props:['cards-per-row']
}
</script>

<style>
.cards_container {
  display:flex;
  flex-wrap:wrap;
  flex-direction:row;
  overflow-y: auto;
  height:100%;
  gap:10px;
}
</style>