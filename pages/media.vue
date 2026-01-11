<template>
  <VContainer>
    <div class="d-flex">
      <VCard v-for="item in media" :key="item.id" class="mx-3" width="300px" outlined>
        <VImg
          color="surface-variant"
          height="200"
          src="https://cdn.vuetifyjs.com/docs/images/cards/purple-flowers.jpg"
          cover
        />

        <VCardTitle>{{ item.title }}</VCardTitle>
      </VCard>
    </div>
  </VContainer>
</template>

<script setup>
const media = [
  { id: 1, title: "Media 1" },
  { id: 2, title: "Media 2" },
  { id: 3, title: "Media 3" },
  { id: 4, title: "Media 4" },
];
</script>
<style scoped></style>
