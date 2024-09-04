<template>
  <div class="sidebar">
    <p class="sidebar-label">{{ label }}</p>

    <div v-for="(menuItems, index) in menu" :key="index">
      <!-- Menu Without Subitems -->
      <q-item clickable tag="a" :to="menuItems.link" v-if="!menuItems.subItems">
        <q-item-section v-if="menuItems.icon" avatar>
          <q-icon :name="menuItems.icon" />
        </q-item-section>

        <q-item-section>
          <q-item-label>{{ menuItems.title }}</q-item-label>
        </q-item-section>
      </q-item>

      <!-- Menu With Subitems -->
      <q-expansion-item icon="folder" :label="menuItems.title" expand-separator v-if="menuItems.subItems">
        <q-list class="sidebar-dropdown">
          <q-item clickable v-ripple v-for="(items, index) of menuItems.subItems" :key="index" :to="items.link">
            <q-item-section avatar>
              <q-icon name="chevron_right" />
            </q-item-section>

            <q-item-section>
              <q-item-label>{{ items.title }}</q-item-label>
            </q-item-section>
          </q-item>
        </q-list>
      </q-expansion-item>
    </div>
  </div>
</template>

<script setup lang="ts">
defineOptions({
  name: 'EssentialLink'
});

type Menu = {
  title: string;
  link?: string;
  icon?: string;
  subItems?: Menu[];
}

export interface EssentialLinkProps {
  label?: string;
  menu: Menu[];
};

defineProps<EssentialLinkProps>()
</script>
