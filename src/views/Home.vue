<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
      <keep-alive>
        <component
          v-bind:is="currentTabComponent"
          v-bind="currentProperties"
          @selected="selected"
          class="tab"
        >
        </component>
      </keep-alive>
      <button @click="changeComponent">Переключить</button>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import HelloAsync from '@/components/HelloAsync.vue'

export default {
  name: 'home',
  components: {
    HelloWorld,
    HelloAsync
  },
  data() {
    return {
      books: [
        { id: 1, name: 'Harray potter 1', authorId: 1 },
        { id: 2, name: 'Harray potter 2', authorId: 1 },
        { id: 3, name: 'Harray potter 3', authorId: 1 },
        { id: 4, name: 'Harray potter 4', authorId: 2 },
        { id: 5, name: 'Harray potter 5', authorId: 2 },
        { id: 6, name: 'Harray potter 6', authorId: 2 },
        { id: 7, name: 'Harray potter 7', authorId: 2 },
        { id: 8, name: 'Harray potter 8', authorId: 3 },
        { id: 9, name: 'Harray potter 9', authorId: 3 },
        { id: 10, name: 'Harray potter 10', authorId: 3 },
        { id: 11, name: 'Harray potter 11', authorId: 1 },
        { id: 12, name: 'Harray potter 12', authorId: 1 },
        { id: 13, name: 'Harray potter 13', authorId: 1 },
      ],
      selectedBooks: [],
      currentTab: 'world'
    }
  },
  methods: {
    selected(selected) {
      this.selectedBooks = selected
    },
    changeComponent() {
      this.currentTab == 'world' ? this.currentTab = 'async' : this.currentTab = 'world'
    }
  },
  computed: {
    currentTabComponent() {
      return 'hello-' + this.currentTab.toLowerCase()
    },
    currentProperties() {
      if(this.currentTab == 'world') {
        return {
          items: this.books, 
          disableTo: 2
        }
      }
    }
  },
}
</script>
