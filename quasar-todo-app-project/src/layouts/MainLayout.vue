<template>
  <q-layout view="lHh Lpr lFf">
    <q-header>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />
      </q-toolbar>
      <div class="q-px-lg q-pt-xl q-mb-md">
        <div class="text-h3">Todo</div>
        <div class="text-subtitle1">{{ todaysDate }}</div>
      </div>
      <q-img src="../assets/images/todo.jpg" class="header-image absolute-top" />
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      :width="250"
      :breakpoint="600"
    >
      <q-scroll-area
        style="
          height: calc(100% - 192px);
          margin-top: 192px;
          border-right: 1px solid #ddd;
        "
      >
        <q-list padding>
          <q-item clickable v-ripple to="/" exact>
            <q-item-section avatar>
              <q-icon name="list" />
            </q-item-section>

            <q-item-section> Todo </q-item-section>
          </q-item>

          <q-item clickable v-ripple to="/about" exact>
            <q-item-section avatar>
              <q-icon name="help" />
            </q-item-section>

            <q-item-section> About </q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>

      <q-img
        class=" avatar-background-image absolute-top"
        src="../assets/images/mountains.jpg"
        style="height: 192px"
      >
        <div class="absolute-bottom bg-transparent">
          <q-avatar size="56px" class="q-mb-sm">
            <img class="avatar-image"
              src="../assets/images/khashayar.jpeg"
            />
          </q-avatar>
          <div class="text-weight-bold">Khashayar Shomali</div>
          <div class="">@shomalikhashayar</div>
        </div>
      </q-img>
    </q-drawer>

    <q-page-container>
      <keep-alive>
        <router-view />
      </keep-alive>
    </q-page-container>
  </q-layout>
</template>

<script>
import { date } from "quasar";

import EssentialLink from "components/EssentialLink";

export default {
  name: "MainLayout",

  components: {
    EssentialLink,
  },

  data() {
    return {
      leftDrawerOpen: false,
    };
  },
  computed: {
    todaysDate() {
      let timeStamp = Date.now();
      return date.formatDate(timeStamp, "dddd D MMMM");
    },
  },
};
</script>

<style lang="scss">
.header-image {
  height: 100%;
  z-index: -1;
  opacity: 0.2;
  filter: grayscale(100%);
}
.text-subtitle1 {
  padding-left: 5px;
  font-size: 14px;
  color: rgba(255, 255, 255, 0.616);
}

.avatar-image{
  border: 1px solid rgb(255, 255, 255);
}



</style>
