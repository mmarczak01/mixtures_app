
<template>
      <Menubar :model="items" class="menuBar">
          <template #item="{ item, props }">
              <router-link v-ripple class="flex items-center" v-bind="props.action" :to="item.to">
                  <span :class="item.icon" />
                  <span class="ml-2">{{ item.label }}</span>
              </router-link>
          </template>
      </Menubar>
</template>

<script>

import Menubar from 'primevue/menubar';
import { RouterLink } from 'vue-router';
export default {
  components: { Menubar, RouterLink },
  data() {
      return {
          items: [
              {
                  label: 'Home',
                  icon: 'pi pi-home',
                  to: '/'
              },
              {
                  label: 'Mixin',
                  icon: 'pi pi-filter',
                  to: '/mixin'
              },
              {
                  label: 'About',
                  icon: 'pi pi-info',
                  to: 'about'
              }
          ]
      };
  }
};
</script>

<style lang="scss">
.menuBar {
  border-radius: 1rem;
  box-shadow: $box-shadow;
  overflow: hidden;
}
</style>