<template>
  <vue-mermaid-string :value="diagram" @node-click="handleNodeClick" />
</template>

<script>
import endent from 'endent'

export default {
  computed: {
    diagram() {
      return endent`
        classDiagram
        Animal <|-- Duck
        Animal <|-- Fish
        Animal <|-- Zebra
        class Duck {
          +String beakColor
          +swim()
          +quack()
        }
        click Duck
      `
    }
  },
  methods: {
    handleNodeClick(nodeId) {
      if (nodeId === 'Duck') {
        alert('Duck node clicked!')
        // Your custom JS logic here
      }
    }
  }
}
</script>
