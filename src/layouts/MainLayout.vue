<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-toolbar-title class="toolbar-title">
          Dollar Conversion
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'MainLayout',
})
</script>

<style lang="scss" scoped>
.toolbar-title {
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
