<template>
  <div class="wrapper">
    <div class="title-form">Nhập thông tin</div>
    <div class="form-add">
      <div class="field">
        <input
          type="text"
          v-model="blogAdd.title"
          class="input"
          placeholder="Tiêu đề"
        />
      </div>
      <div class="field">
        <!-- <p style="white-space: pre-line">{{ blogAdd.content }}</p> -->
        <textarea
          v-model="blogAdd.content"
          class="input"
          placeholder="Nội dung"
          rows="6"
        ></textarea>
      </div>
      <div class="field">
        <input
          type="text"
          v-model="blogAdd.src"
          placeholder="Nguồn ảnh"
          class="input"
        />
      </div>
      <div class="field">
        <select v-model="blogAdd.mediaType" class="select">
          <option value="image" >Image</option>
          <option value="video">Video</option>
        </select>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  expose: ["blogAdd"],
  data() {
    return {
      blogAdd: {
        title: "",
        content: "",
        src: "",
        mediaType: "image",
      },
    };
  },

};
</script>

<style>
.wrapper {
  background-color: antiquewhite;
  width: 100%;
  padding: 10px 0;
}
.title-form {
  text-align: center;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
  font-size: 30px;
  font-weight: bold;
}
.form-add {
  display: block;
  width: 100%;
  background-color: antiquewhite;
}

.field {
  width: 80%;
  margin: 20px auto;
}

.input {
  width: 90%;
  padding: 15px 10px;
  outline: none;
  border: none;
}

.select {
  width: 95%;
  padding: 15px 10px;
  outline: none;
  border: none;
}
</style>
