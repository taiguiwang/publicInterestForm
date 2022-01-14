<template>
  <div>
    <div>
      <form>
        <ul>
          <li>logo</li>
          <li><input type="file" id="avatar-upload"/></li>
        </ul>
        <button @click="dianJi" id="btn">上传图片</button>
      </form>
    </div>
    <div><Morelink /></div>
  </div>
</template>
<script>
import Morelink from "./Morelink.vue";
const AV = require("leancloud-storage");
// const { Query, User } = AV;
AV.init({
  appId: "SdXtqoa4Yd4znA5MwlFQYyXG-gzGzoHsz",
  appKey: "wwggQgtDEa9EG49u9dtcV5WR",
  serverURL: "https://sdxtqoa4.lc-cn-n1-shared.com",
});
export default {
  name: "Logolink",
  components: {
    Morelink,
  },
  methods: {
    dianJi() {
        const avatarUpload = document.getElementById('avatar-upload').files[0];

        const file = new AV.File(avatarUpload.name, avatarUpload);

        //保存文件
        file.save().then((file) => {
            console.log(`文件保存完成。URL：${file.url}`);
        }, () => {
            // 保存失败，可能是文件无法被读取，或者上传过程中出现问题
        });
    },
  },
};
</script>
<style scoped>
div {
  display: block;
}

li {
  list-style: none;
  margin-top: 8px;
}

form {
    border: 5px gray solid;
    border-radius: 20px;
    padding: 20px 40px 20px 0px;
}
</style>