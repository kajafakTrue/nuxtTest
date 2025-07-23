<script setup lang="ts">
import VueMermaidString from 'vue-mermaid-string'
import endent from 'endent'
import { computed } from 'vue'


function handleNodeClick(nodeId) {
  console.log('Clicked node:', nodeId)
}
const diagram = computed(() => {
  return endent`
        classDiagram
        Animal <|-- Duck
        Animal <|-- Fish
        class Duck {
          +String beakColor
          +swim()
          +quack()
        }
      `
})
</script>

<template>
  <VueMermaidString

    :value="diagram"

    :options="{ theme: 'dark' }"
    @node-click="handleNodeClick"
  />
</template>
