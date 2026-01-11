<template>
  <VLayout full-height>
    <VAppBar color="black">
      <VAppBarNavIcon
        variant="text"
        @click.stop="drawer = !drawer"
      />
      <VToolbarTitle>{{ returnTitle }}</VToolbarTitle>
      <VMenu
        location="bottom"
        offset-y
      >
        <template #activator="{ props }">
          <VBtn icon="mdi-dots-vertical" variant="text" v-bind="props"/>
        </template>
        <VList>
          <VListItem
            v-for="item in contextItems"
            :key="item.value"
            :value="item.value"
            :prepend-icon="returnIcon(item)"
            @click="goToModule(item.value)"
          >
            <VListItemTitle>{{ item.title }}</VListItemTitle>
          </VListItem>
        </VList>
      </VMenu>
    </VAppBar>

    <VNavigationDrawer
      v-model="drawer"
      :location="$vuetify.display.mobile ? 'bottom' : undefined"
      temporary
    >
      <VList>
        <VListItem
          v-for="item in items"
          :key="item.value"
          :value="item.value"
          :prepend-icon="returnIcon(item)"
          @click="goToModule(item.value)"
        >
          <VListItemTitle>{{ item.title }}</VListItemTitle>
        </VListItem>
      </VList>
    </VNavigationDrawer>

    <VMain>
      <slot />
    </VMain>
  </VLayout>
</template>

<script setup>
import { ref } from "vue";
const route = useRoute()
const items = [
  {
    title: "Home",
    value: "home",
  },
  {
    title: "My Media",
    value: "media",
  },
  {
    title: "Account",
    value: "account",
  },
  {
    title: "Settings",
    value: "settings",
  },
];
const contextItems = [
  {
    title: "Logout",
    value: "logout",
  }
];
const drawer = ref(false);
const returnIcon = (item) => {
  switch (item.value) {
    case "home":
      return "mdi-home";
    case "media":
      return "mdi-folder-multiple-image";
    case "account":
      return "mdi-account";
    case "settings":
      return "mdi-cog";
    case "logout":
      return "mdi-logout";
  } 
};
const returnTitle = computed(() => {
  const path = route.path.replace("/", "");
  const currentItem = items.find((item) => item.value === path);
  return currentItem ? currentItem.title : "Home";
});
const goToModule = (module) => {
  console.log(`Navigating to ${module}`);
  if (module === "home") {
    // Navigate to home
   navigateTo("/");
  } else {
    // Navigate to module page
    navigateTo(`/${module}`);
  }
  drawer.value = false;
};
</script>
