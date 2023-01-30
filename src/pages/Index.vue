<template>
  <q-page class="flex flex-center">
    <img
      alt="Quasar logo"
      src="~assets/quasar-logo-vertical.svg"
      style="width: 200px; height: 200px"
    >
    <q-tree
      ref="qtree"
      :dark="tree.dark"
      :filter="tree.filter"
      :nodes="tree.nodes"
      node-key="nodeKey"
      @update:selected="update_selected">
      <template v-slot:header-root="prop">
        <div class="row items-center">
          {{ prop.node.label }}
          <q-badge
            v-if="prop.node.children.length > 0"
            :color="badge.color"
            :text-color="badge.text_color"
            class="q-ml-sm">
            {{ prop.node.children.length }}
          </q-badge>
          <q-badge
            v-if="prop.node.hasOwnProperty('fileCount')"
            :text-color="badge.text_color"
            class="q-ml-sm"
            color="warning">
            {{ prop.node.fileCount }}
          </q-badge>
        </div>
      </template>
    </q-tree>
  </q-page>
</template>

<script>
import {defineComponent} from 'vue';
import * as tree from 'src/utils/tree.js';

export default defineComponent({
  name: 'PageIndex',
  data() {
    return {
      tree: {
        dark: false,
        filter: '',
        nodes: tree,
      }
    }
  },
  methods: {
    update_selected(val) {
      this.$log.info('update_selected', val)
    },
  },
  beforeMount() {
    // console.dir(this)
    // console.dir(this.$log)
    // console.dir(this.$log.info)
    this.$log.info('info')
    this.$log.debug(this.$axios.defaults)
  }
})
</script>
