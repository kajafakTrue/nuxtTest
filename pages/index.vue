<script setup lang="ts">
import VueMermaidString from 'vue-mermaid-string'
import endent from 'endent'
import { computed, onMounted, nextTick } from 'vue'

const purchasesDiagram = computed(() => {
  return `
    classDiagram
        class Purchase["Закупка"]
        class Customer["Заказчик"]
        class Supplier["Поставщик"]
        
        Purchase --> Customer
        Purchase --> Supplier
        

        click Purchase call handleDiagramClick("Purchase", "purchase")
        click Customer call handleDiagramClick("Customer", "customer")
        click Supplier call handleDiagramClick("Supplier", "supplier")
  `
})

async function handleDiagramClick(nodeId, nodeType: string) {
  console.log(await nodeId.srcElement.innerText)
}
</script>
<template>

    <VueMermaidString

    :value="purchasesDiagram"
    @click="handleDiagramClick"

    :options="{ theme: 'dark', class: {hideEmptyMembersBox: false, hideEmptyMembers: false, hideEmptyAttributes: false, hideEmptyMethods: false, hideEmptyProperties: false, hideEmptyConstructors: false, hideEmptyClasses: false, hideEmptyInterfaces: false, hideEmptyEnums: false, hideEmptyTypes: false, hideEmptyPackages: false, hideEmptyModules: false, hideEmptyNamespaces: false, hideEmptyObjects: false, hideEmptyFunctions: false, hideEmptyVariables: false, hideEmptyConstants: false, hideEmptyPropertiesBox: true
  } }"

  />
</template>          