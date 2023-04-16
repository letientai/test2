<template lang="">
  <div class="card">
    <!-- sử dụng Dynamic Slot Names -->
    <slot :name="post.mediaType"></slot>
    <slot name="default" test="5" >Không có tiêu đề</slot>
    <button @click="showDetails">Xem chi tiêt</button>

    <!-- Di chuyển modal tới body -->
    <teleport to="body">
      <modal-detail v-show="checkModal" @closeModel="closeModal">
        <template v-slot:image>
          <img :src="post.src" alt="" />
        </template>
        <template v-slot:video>
          <video :src="post.src" controls></video>
        </template>
        <template v-slot:content>
          <h1>{{ post.title }}</h1>
          <p style="white-space: pre-line">{{ post.content }}</p>
        </template>
      </modal-detail>
    </teleport>
    
  </div>
</template>
<script>
import modal from "./modal.vue";
export default {
  name: "blog-post",
  components: {
    "modal-detail": modal,
  },
  props: {
    item: Object,
  },
  data() {
    return {
      post: this.item,
      checkModal: false,
    };
  },
  methods: {
    showDetails() {
      this.checkModal = true;
    },
    closeModal() {
      this.checkModal = false;
    },
  },
};
</script>

<style scoped>
.card {
  width: 220px;
  background-color: antiquewhite;
  padding: 10px;
  margin: 0px 30px 20px;
}
button {
  border: none;
  padding: 5px;
  background-color: rgb(167, 167, 167);
  color: white;
  cursor: pointer;
}

button:hover {
}
</style>
