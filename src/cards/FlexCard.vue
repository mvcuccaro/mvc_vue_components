<template>
  <div class="card" :style="c_styles">
    <div class="card_content">
      <slot name="title"></slot>
    </div>
    <div class="card_content">
      <slot></slot>
    </div>
    <div>
      <slot name="footer" class="card_footer"></slot>
    </div>
  </div>
</template>

<script>
export default  {
  mounted(){
    console.log(this.$parent._props.cardsPerRow)
  },
  computed:{
    c_styles(){
      let percent = (100 / this.$parent._props.cardsPerRow) - 1;
      return `flex: 0 1 ${percent}%`;
    }
  }
}
</script>

<style>
.card {
border:1px solid #000000;
min-width:200px;
flex: 0 1 33%;
display: flex;
flex-direction:column;
  text-align:left
}

.card_content {
flex: 1 1 auto;
}

.card_footer {
display: flex;
flex-direction: column;
margin-top:auto;
}
</style>
