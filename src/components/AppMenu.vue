
<template>
      <Menubar :model="items" class="menuBar">
          <template #item="{ item, props }">
              <a v-ripple class="flex items-center" v-bind="props.action" :to="item.to">
                  <span :class="item.icon" />
                  <span class="ml-2">{{ item.label }}</span>
              </a>
          </template>
      </Menubar>
</template>

<script>

import Menubar from 'primevue/menubar';
export default {
  components: { Menubar },
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
                  icon: 'pi pi-star',
                  to: 'mixin'
              },
              {
                  label: 'About',
                  icon: 'pi pi-envelope',
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
  box-shadow: 0 20px 40px 0 rgba(107,154,212,.3);
  overflow: hidden;
}
</style>