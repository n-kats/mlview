<template>
  <q-tree
    :nodes="tree"
    node-key="label"
    default-expand-all
  >
    <template v-slot:default-header="prop">
      <div class="row items-center">
        <q-icon :name="prop.node.icon || 'share'" color="orange" size="28px" class="q-mr-sm" />
        <div class="text-weight-bold text-primary">{{ prop.node.label }}</div>
      </div>
    </template>

    <template v-slot:default-body="prop">
      <div v-if="prop.node.story">
        <span class="text-weight-bold">This node has a story</span>: {{ prop.node.story }}
      </div>
      <span v-else class="text-weight-light text-black">This is some default content.</span>
    </template>
  </q-tree>
</template>

<script>
export default {
  name: 'TreeNavi',
  data () {
    var treeItems = []
    for (var i = 0; i < 5; i++) {
      var children = []
      for (var j = 0; j < i; j++) {
        children.push({
          label: 'child_' + i + '_' + j,
          header: 'generic',
          body: 'body_' + i + '_' + j,
          story: 'story_' + i + '_' + j
        })
      }
      treeItems.push({
        label: 'item' + i,
        header: 'root',
        'children': children
      })
    }

    return {
      left: true,
      tree: treeItems
    }
  }
}
</script>

<style>
</style>
