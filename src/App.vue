<template>
  <h1>Website Builder</h1>
  <div class="sideBySide">

  <!-- this is a div baked into the top level because I was running short on time.
  Also I haven't quite mastered emitting events from components -->
    <div class="Editor">
      <h2>Editor</h2>
      <div v-for="(section, index) of sections" :key="index">
        <label>Heading:</label> <input type="text" v-model="section.heading">
        <button @click="swapSections(index-1, index)">↑</button>
        <button @click="swapSections(index, index+1)">↓</button>
        <ul>
          <li v-for="(item, index) of section.items" :key="index">
            <!-- will have to do some work here to support different of items -->
            <label>Name:</label> <input type="text" v-model="item.name">
            <label>Description:</label> <input type="text" v-model="item.description">
          </li>
        </ul>
        <hr>
      </div>
    </div>

    <Preview :sections="sections"/>
  </div>
</template>

<script>
// import Preview from './components/Preview.vue'
import Preview from './components/Preview.vue'

export default {
  name: 'App',
  components: {
    Preview
  },
  methods: {
    swapSections(first, second){
      if (first < 0 || second >= this.sections.length) return;
      const temp = this.sections[first];
      this.sections[first] = this.sections[second]
      this.sections[second] = temp;
    }
  },
  data() {
    return {
          sections: [
              {
                  heading: "my first heading",
                  items: [
                      {"type": "BasicItem", "name": "first", "description": "lots of words here and such. Probably even more."},
                      {"type": "BasicItem", "name": "second", "description": "lots of words here and such. Probably even more."},
                      {"type": "BasicItem", "name": "third", "description": "lots of words here and such. Probably even more."},
                      ]
              },

              {
                  heading: "a great heading here 2",
                  items: [
                      {"type": "BasicItem", "name": "a", "description": "lots of words here and such. Probably even more."},
                      {"type": "BasicItem", "name": "b", "description": "lots of words here and such. Probably even more."},
                      {"type": "BasicItem", "name": "c", "description": "lots of words here and such. Probably even more."},
                      ]
              }
              ]
          }
              
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.sideBySide{
  display: inline-flex;
  width: 100%;
}
.Editor input{
  width: 50px;
}
.Editor {
  width: 25%;
}
.Preview{
  width:  75%;
}
</style>
