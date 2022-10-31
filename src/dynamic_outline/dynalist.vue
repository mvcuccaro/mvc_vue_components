<template>
  <div>
    <div class="dynalist_container">
      <div class="dynalist-list-side">
        <ul>
          <li v-for="item in list_items" :key="item.title" @click="makeVisible(item)" class="dynalist-list-item-container">{{item.title}}</li>
        </ul>
      </div>
      <div class="dynalist-content-side">
        <slot></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'dynalist-container',
  data() {
    return {
      list_items:[]
    }
  },
  methods:{
    mountListItem(list_item) {
      this.list_items.push(list_item);
    },
    makeVisible(list_item){
      this.list_items.forEach(i => {
        i.visible = false;
      })
      list_item.visible = true;
    }
  },
  created(){
    this.$on('item-mounted', list_item => {
      this.mountListItem(list_item);
    });
  },
  mounted(){
    this.list_items[0].visible = true;
  }
}
</script>

<style>
.dynalist_container {
  display: flex;
  flex-direction: row;
  gap:4px;
}

.dynalist-content-side {
  border:1px solid #000000;
  flex: 0 0 auto;
  width:80%;
  text-align:left;
}

.dynalist-list-side {
  border:1px solid #000000;
  width:20%
}

.dynalist-list-item-container {
  min-height:40px;
}

</style>
