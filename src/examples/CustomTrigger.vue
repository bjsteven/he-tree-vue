<!-- this is an example -->
<template lang="pug">
.CustomTrigger
  h2 Custom Trigger
  Tree(:value="treeData" ref="tree" triggerClass="trigger")
    div(slot-scope="{node, index, path, tree}")
      button.trigger drag
      div(style="width:.5em;height:1em;display:inline-block;")
      b(v-if="node.children && node.children.length > 0" @click="tree.toggleFold(node, path)") {{node.$folded ? '+' : '-'}}&nbsp;
      input(type="checkbox" :checked="node.$checked" @change="tree.toggleCheck(node, path)")
      | &nbsp;
      span {{node.text}}
</template>

<script>
import * as hp from 'helper-js'
import Tree from '@/components/Tree.vue'
import fold from '@/plugins/fold.js'
import check from '@/plugins/check.js'
import Draggable from '@/plugins/draggable/Draggable.vue'

const MixedTree = Tree.mixPlugins([fold, check, Draggable])

export default {
  components: {Tree: MixedTree},
  data() {
    return {
      treeData: [
        {text: 'node 1', $droppable: true, children: [
          {text: 'node 1-0'},
        ]},
        {text: 'node 2', $droppable: true, children: [
          {text: 'node 2-0'},
        ]},
        {text: 'node 3', $droppable: true, children: [
          {text: 'node 3-0'},
        ]},
        {text: 'node 4', $droppable: true, children: [
          {text: 'node 4-0'},
        ]},
        {text: 'node 5', $droppable: true},
        {text: 'node 6', $droppable: true},
        {text: 'node 7', $droppable: true},
        {text: 'node 8', $droppable: true},
        {text: 'node 9', $droppable: true},
      ],
    }
  },
  // computed: {},
  // watch: {},
  methods: {},
  // created() {},
  mounted() {
  },
}
</script>

<style>
.CustomTrigger .trigger{
}
</style>
