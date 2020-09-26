<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated>
      <q-toolbar>

      <q-btn dense flat round icon="menu" @click="leftDrawerOpen = !leftDrawerOpen" />

        <q-toolbar-title>
          WONDER.LEGAL CLONE
        </q-toolbar-title>

        <q-btn flat round dense icon="more_vert" />

      </q-toolbar>
    </q-header>


    <q-drawer
        v-model="leftDrawerOpen"

        :mini="miniState"
        @mouseover="miniState = false"
        @mouseout="miniState = true"
        mini-to-overlay

        :width="200"
        :breakpoint="500"
        bordered
        content-class="bg-grey-3"
      >
        <q-scroll-area class="fit">
          <q-list padding>
            <q-item clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="home" />
              </q-item-section>

              <q-item-section>
                HOME
              </q-item-section>
            </q-item>

            <q-item clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="star" />
              </q-item-section>

              <q-item-section>
                TEMPLATES
              </q-item-section>
            </q-item>

            <q-item clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="send" />
              </q-item-section>

              <q-item-section>
                SEND
              </q-item-section>
            </q-item>

            <q-separator />

            <q-item clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="account_box" />
              </q-item-section>

              <q-item-section>
                PROFILE
              </q-item-section>
            </q-item>
          </q-list>
        </q-scroll-area>
      </q-drawer>


    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>

export default {
  name: 'MainLayout',
  data () {
    return {
      leftDrawerOpen: true,
      miniState: true
    }
  }
}
</script>
