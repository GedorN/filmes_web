<template lang="pug">
  v-content
    #core-view
      v-fade-transition(mode='out-in')
        router-view
    core-footer(v-if="$route.name !== 'Maps'")
</template>

<script>
export default {
  metaInfo () {
    return {
      title: 'Vuetify Material Dashboard by CreativeTim'
    }
  }
}
</script>

<style>
#core-view {
  padding-bottom: 100px;
}
</style>
