<template>
  <div class="container">
    <div>
      <logo />
      {{ node }}
      <nvwa-node :node-data="nodeData" />
    </div>
  </div>
</template>

<script lang="ts">
import framebus from 'framebus'
import Vue from 'vue'
import Logo from '~/components/Logo.vue'
import NvwaNode from '~/components/NvwaNode.vue'

export default Vue.extend({
  components: {
    Logo,
    NvwaNode
  },
  data: () => ({
    nodeData: {
      type: 'root',
      props: {},
      children: [
        {
          type: 'component',
          props: { tag: 'image', src: '12312312' },
          children: []
        },
        {
          type: 'component',
          props: { tag: 'image', src: '1231231' },
          children: []
        },
        {
          type: 'component',
          props: { tag: 'text', text: '123123213' },
          children: [
            {
              type: 'component',
              props: { tag: 'text', text: '333333' },
              children: []
            }
          ]
        }
      ]
    }
  }),
  mounted() {
    // framebus.on('change', (data) => {
    //   this.node = data.node
    // })
  },
  methods: {}
})
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
