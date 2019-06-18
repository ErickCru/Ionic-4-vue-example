<template>
  <ion-card>
    <ion-card-header>
      <ion-label>{{post.title}}</ion-label>
    </ion-card-header>
    <ion-card-content>
      <template v-if="image.startsWith('https://')">
        <ion-img :src="image"></ion-img>
      </template>
      <template v-else>
        <ion-lab color="danger">No tiene imagen</ion-lab>
      </template>
      <ion-button color="tertiary" expand="full" @click="$router.go(-1)" style="margin-top: 1rem">Go Back</ion-button>
    </ion-card-content>
  </ion-card>
</template>

<script>
export default {
  props: ["post"],
  data() {
    return {
      image: ""
    };
  },
  mounted() {
    this.image = this.post.preview.images[0].source.url.replace(/&amp;/g, "&");
  }
};
</script>

