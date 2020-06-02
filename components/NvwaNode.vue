<template>
  <div v-if="nodeData && nodeData.children.length">
    <div v-for="(val, i) in nodeData.children" :key="i">
      <component
        :is="`NVWA_${val.props.tag.toUpperCase()}`"
        v-bind="val.props"
      ></component>
      <Nvwa v-if="val.children.length" :node-data="val" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'Nvwa',
  components: {
    NVWA_IMAGE: () => import('./Image.vue'),
    NVWA_TEXT: () => import('./Text.vue')
  },
  props: ['nodeData']
}
</script>

<style></style>
