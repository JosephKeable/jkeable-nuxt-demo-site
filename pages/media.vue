<template>
  <VContainer>
    <div class="d-flex align-content-start flex-wrap">
      <VCard v-for="item in media" :key="item.id" class="mx-3 mt-3" width="300px" outlined>
        <VImg
          color="surface-variant"
          height="200"
          width="300"
          :src="item.thumbnail"
          cover
        />
        <VCardTitle>{{ item.title }}</VCardTitle>
        <VCardText>
          <p>File Type: {{ item.file_type }}</p>
          <p>Size: {{ item.size }}</p>
        </VCardText>
      </VCard>
    </div>
  </VContainer>
</template>

<script setup>
const media = [
  { id: 1, title: "Media1.mp4", file_type: "video/mp4", size: "15MB", thumbnail: "https://picsum.photos/id/1/200/300" },
  { id: 2, title: "Media2.mp4", file_type: "video/mp4", size: "20MB", thumbnail: "https://picsum.photos/id/2/200/300" },
  { id: 3, title: "Media3.mp4", file_type: "video/mp4", size: "25MB", thumbnail: "https://picsum.photos/id/3/200/300" },
  { id: 4, title: "Media4.mp4", file_type: "video/mp4", size: "30MB", thumbnail: "https://picsum.photos/id/4/200/300" },
  { id: 5, title: "Media1.mp4", file_type: "video/mp4", size: "15MB", thumbnail: "https://picsum.photos/id/5/200/300" },
  { id: 6, title: "Media2.mp4", file_type: "video/mp4", size: "20MB", thumbnail: "https://picsum.photos/id/6/200/300" },
  { id: 7, title: "Media3.mp4", file_type: "video/mp4", size: "25MB", thumbnail: "https://picsum.photos/id/7/200/300" },
  { id: 8, title: "Media4.mp4", file_type: "video/mp4", size: "30MB", thumbnail: "https://picsum.photos/id/8/200/300" },
];
</script>
<style scoped></style>
