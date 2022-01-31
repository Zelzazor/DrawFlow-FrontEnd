<template>
  <div id="app">
    <div class="menu">
      <button @click="AddNumberNode">Number Node</button>
      <button @click="AdditionNode">Addition Node</button>
    </div>
    <div id="drawflow"></div>
    
  </div>
  
</template>

<script>
import Vue from 'vue'
/*eslint-disable */
import NumberNode from './components/NumberNode.vue'
import AdditionNode from './components/AdditionNode.vue'
import Drawflow from 'drawflow'
import styleDrawflow from 'drawflow/dist/drawflow.min.css' // eslint-disable-line no-use-before-define
/*eslint-enable */


export default {
  name: 'App',
  data() {
    return {
      editor: null,
    }
  },
  mounted() {
    const id = document.getElementById("drawflow");
    this.editor = new Drawflow(id, Vue);
    this.editor.start();
    const props = {};
    const options = {};
    this.editor.registerNode('NumberNode', NumberNode, props, options);
    this.editor.registerNode('AdditionNode', AdditionNode, props, options);
    const data = {};
    this.editor.addNode('Name', 0, 1, 150, 300, 'Class', data, 'NumberNode', 'vue');
    this.editor.on('connectionCreated', (id)=>{
      console.log(id);
    })
  },
  methods: {
    AddNumberNode() {
      const data = {};
      this.editor.addNode('Number', 0, 1, 150, 300, 'Class', data, 'NumberNode', 'vue');
    },

    AdditionNode() {
      const data = {};
      this.editor.addNode('Number', 2, 1, 150, 300, 'Class', data, 'AdditionNode', 'vue');
    }
  },

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
#drawflow {
  width: 100%;
  height: 500px;
  border: 1px solid red;
}

</style>
