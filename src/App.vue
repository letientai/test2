<template>
  <div class="title">THE BLOG</div>
  <div class="content">
    <div class="listBlogs">
      <blog-post v-for="(item, index) in blogs" :key="index" v-bind:item="item">
        <template v-slot:image>
          <img :src="item.src" alt="" />
        </template>
        <template v-slot:video>
          <video :src="item.src" controls></video>
        </template>
        <template v-slot:default>
          <p style="height: 30px">{{ item.title }}</p>
        </template>
      </blog-post>
    </div>

    <div class="form">
      <form-add ref="formAdd" />
      <div class="btn btn-add" v-on:click="handleAddBlog">Thêm Blog</div>
    </div>
    <!-- <div class="btn btn-add">Add Blog</div> -->
  </div>
</template>

<script>
import blogPost from "./components/blogPost.vue";
import formAdd from "./components/formAdd.vue";

export default {
  name: "App",
  components: {
    blogPost,
    formAdd,
  },
  data() {
    return {
      blogs: [
        {
          title: "Nền văn hóa ẩm thực lâu đời",
          content:
            "Ngày nay, dân tộc Việt vẫn luôn gìn giữ những đặc sắc văn hóa ẩm thực truyền thống mà ông cha ta để lại. Tuy nhiên, không phải vì thế mà nói nền ẩm thực của nước ta đã lỗi thời, lạc hậu. Kế thừa và phát huy truyền thống, người Việt lại tiếp tục sáng tạo và đón nhận những tinh hoa ẩm thực từ các nước để làm nên những món ăn độc đáo.",
          mediaType: "image",
          src: "https://img.tastykitchen.vn/resize/764x-/2021/01/31/am-thuc-viet-nam-0-f7ac.jpg",
        },
        {
          title: "Công nghệ đơn giản logo thương hiệu",
          content:
            "Pikbest cung cấp tài liệu tải xuống miễn phí Công Nghệ đơn Giản Logo Thương Hiệu Màn Hình đồ Họa Treo Tường Mẫu AE Chủ đề của tác phẩm này là Video, Kịch bản sử dụng là , Số hình ảnh là 1771163, Định dạng là AEP,bạn nên mở tập tin này bằng Photoshop CC, tài liệu này là Video, Kích thước là 83277908",
          mediaType: "video",
          src: "https://pic.pikbest.com/19/86/46/64f888piCxAe.mp4_10s.mp4",
        },
        {
          title: "Hương vị hài hòa, tốt cho sức khỏe",
          content:
            "Từ những món đơn giản cho đến cầu kỳ, người Việt Nam đều có sự phối hợp hài hòa giữa ngũ vị chua, cay, mặn, ngọt, đắng. Chính vì vậy mà những du khách nước ngoài thường rất bất ngờ và ấn tượng bởi cách chế biến, tẩm ướp gia vị của người Việt. Ẩm thực Việt được tạo nên từ triết lý âm - dương tương tự như các nước Châu Á",
          mediaType: "image",
          src: "https://img.tastykitchen.vn/resize/764x-/2021/01/31/am-thuc-viet-nam-0-f7ac.jpg",
        },
        {
          title: "Phong phú, đa dạng",
          content:
            "Việt Nam được đánh giá là một trong những quốc gia có nền ẩm thực phong phú và đa dạng trên thế giới. Việt Nam có 63 tỉnh thành với 54 dân tộc anh em sinh sống dọc theo chiều dài đất nước từ Bắc vào Nam. Mỗi nơi, mỗi dân tộc lại có những cách chế biến món ăn từ nguyên liệu khác nhau",
          mediaType: "image",
          src: "https://img.tastykitchen.vn/resize/764x-/2021/01/31/am-thuc-viet-nam-1-6291.jpg",
        },
        {
          title: "Sinh hoạt ăn uống của người Việt",
          content:
            "Một trong những đặc điểm nổi bật về ẩm thực Việt Nam trong mắt du khách quốc tế là sinh hoạt ăn uống của người dân. Những văn hóa ăn uống từ lâu đời và vẫn được phát huy trong thời buổi hiện nay của dân tộc Việt Nam",
          mediaType: "video",
          src: "https://pic.pikbest.com/00/07/48/17h888piCavx.mp4_10s.mp4",
        },
        {
          title: "Sinh hoạt ăn uống của người Việt",
          content:
            "Một trong những đặc điểm nổi bật về ẩm thực Việt Nam trong mắt du khách quốc tế là sinh hoạt ăn uống của người dân. Những văn hóa ăn uống từ lâu đời và vẫn được phát huy trong thời buổi hiện nay của dân tộc Việt Nam",
          mediaType: "image",
          src: "https://img.tastykitchen.vn/resize/764x-/2021/01/31/am-thuc-viet-nam-0-f7ac.jpg",
        },
      ],
    };
  },
  methods: {
    handleAddBlog() {
      if (
        !Object.values(this.$refs.formAdd.blogAdd).some((item) => item == "")
      ) {
        this.blogs.push(this.$refs.formAdd.blogAdd);
        this.$refs.formAdd.blogAdd = {};
      } else {
        alert("Yêu cầu nhập đủ thông tin");
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  position: relative;
}
.title {
  text-align: center;
  font-family: "Courier New", Courier, monospace;
  font-size: 40px;
  font-weight: bold;
}
img {
  width: 100%;
}
video {
  width: 100%;
  height: 145px;
}
.content {
  width: 85%;
  margin: 30px auto;
  display: flex;
}
.listBlogs {
  display: flex;
  flex-wrap: wrap;
  /* margin: 20px auto; */
  width: 75%;
}
.form {
  width: 25%;
}
.btn-add {
  background-color: antiquewhite;
  display: flex;
  align-items: center;
  color: #4d4d4d;
  font-weight: bold;
  justify-content: center;
  cursor: pointer;
  padding: 20px;
  margin-top: 10px;
}
.btn-add:hover {
  background-color: rgb(241, 224, 200);
}
</style>
