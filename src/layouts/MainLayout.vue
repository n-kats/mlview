<template>
  <q-layout view="hHh lpR fFf">
    <q-header bordered class="bg-primary text-white">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="left = !left" />
        <q-toolbar-title>
          MLViewer
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="left" side="left" overlay behavior="desktop" bordered>
      <TreeNavi />
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

  </q-layout>
</template>

<script>
import TreeNavi from '../components/TreeNavi'

export default {
  components: {
    TreeNavi
  },
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
