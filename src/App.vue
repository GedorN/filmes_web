<template lang="pug">
  v-app
    core-filter
    core-toolbar
    core-drawer
    core-view
</template>

<style lang="scss">
@import '@/styles/index.scss';

/* Remove in 1.2 */
.v-datatable thead th.column.sortable i {
  vertical-align: unset;
}
</style>
