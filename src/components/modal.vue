<template lang="">
  <div class="container" @click="closeModel">
    <div class="model" @click.stop>
      <div class="content-blog">
        <slot name="content" ></slot>
      </div>
      <!-- <div class="image">
        <slot :name="post.mediaType"></slot>
      </div> -->
    </div>
  </div>
</template>

<script>
export default {
  name: "model-detail",

  methods: {
    closeModel() {
      this.$emit("closeModel");
    },
  },

};
</script>

<style scoped>
.container {
  width: 100%;
  position: fixed;
  top: 0;
  left: 0;
  height: 100%;
  background: rgba(0.1, 0.1, 0.1, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
}
.model {
  width: 1000px;
  /* height: 700px; */
  padding: 15px;
  display: flex;
  justify-content: space-between;
  background-color: white;
}
/* .image {
  width: 45%;
}
.content-blog {
  width: 50%;
} */
</style>
