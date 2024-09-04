<template>
  <q-layout view="lHh Lpr lFf">
    <q-header class="header">
      <q-toolbar>
        <q-btn flat dense round icon="menu" aria-label="Menu" @click="toggleLeftDrawer" />

        <q-toolbar-title class="toolbar-title">
          QuasarApp
        </q-toolbar-title>

        <AvatarToggle />
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above class="sidebar" :width="275">
      <q-list>
        <div class="sidebar-logo-container">
          <div class="sidebar-logo">
            <img src="/images/lamsel-logo.png" alt="Sidebar Logo" />
          </div>
          <span class="sidebar-logo-description">Dinas Pariwisata Lampung Selatan</span>
        </div>

        <EssentialLink v-for="(link, index) in linksList" :key="index" v-bind="link" />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import EssentialLink, { EssentialLinkProps } from 'components/EssentialLink.vue';
import AvatarToggle from 'src/components/AvatarToggle.vue';

defineOptions({
  name: 'MainLayout'
});

const linksList: EssentialLinkProps[] = [
  {
    label: 'Home',
    menu: [
      {
        title: 'Dashboard',
        icon: 'dashboard',
        link: '/dashboard'
      }
    ],
  },
  {
    label: 'Essentials',
    menu: [
      {
        title: 'Essentials',
        icon: 'widgets',
        subItems: [
          {
            title: 'Buttons',
            link: '/buttons'
          },
          {
            title: 'Icons',
            link: '/icons'
          },
          {
            title: 'Typography',
            link: '/typography'
          },
          {
            title: 'Colors',
            link: '/colors'
          },
        ],
      },
    ],
  },
];

const leftDrawerOpen = ref(false);

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}
</script>
