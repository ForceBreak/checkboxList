<template>
  <div class="hello">
    <ul>
      <li v-for="(item, index) in items" :key="item.id">
        <input 
          type="checkbox" 
          v-model="selected" 
          :name="item.id" 
          :value="item"
          :disabled="itemsCopy[index].disable"
        >
        <label :for="item.id">{{item.name}}</label>
      </li>
    </ul>
  </div>
</template>

<script>

export default {
  name: 'hello-world',
  props: {
    items: {
      type: Array,
      default:
        function () {
          return [
            { id: 1, name: 'Harray potter 1', authorId: 1 },
            { id: 2, name: 'Harray potter 2', authorId: 1 },
          ]
        } 
    },
    disableTo: {
      type: Number,
      default: 2
    }
  },
  data() {
    return {
      selected: [],
      itemsCopy: []
    }
  },
  watch: {
    selected(oldVal, newVal) {
      if(this.selected.length == this.disableTo) {
        this.itemsCopy.forEach(e => {
          if(!Boolean(this.selected.indexOf(e) != -1)) {
            e.disable = true
          }
        })
      }else{
        this.itemsCopy.forEach(e => e.disable = false)
      }
      this.$emit('selected', this.selected)
    }
  },
  created() {
    this.items.forEach( e=> {
      this.itemsCopy.push( Object.assign(e, {disable: false})) 
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
li{
  list-style-type: none;
}
</style>
