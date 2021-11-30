<template>
  <ol class="breadcrumb">
    <li class="breadcrumb-item" v-for="(item, index) in list" v-bind:key="index">
      <span class="active" v-if="isLast(index)">{{ showName(item) }}</span>
      <nuxt-link :to="item" v-else>{{ showName(item) }}</nuxt-link>
    </li>
  </ol>
</template>

<script>
export default {
  props: {
    list: {
      type: Array,
      required: true,
      default: () => []
    }
  },
  methods: {
    isLast (index) {
      return index === this.list.length - 1
    },
    showName (item) {
      if (item.meta && item.meta.label) {
        item = item.meta && item.meta.label
      }
      if (item.name) {
        item = item.name
      }
      return item
    }
  }
}
</script>
