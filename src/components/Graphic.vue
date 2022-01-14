<template>
    <div id="graphic">
        <div id="input_img">
            <ul>
                <li><input type="file" id="image"/><p @click="uploadImage" id="p_SC">上传</p></li>
                
            </ul>
        </div>

        <div id="all_text">
            <span id="iocn"><img src="../assets/icon/添加文本.png"></span>
        </div>
    </div>
</template>

<script>
const AV = require("leancloud-storage");
AV.init({
  appId: "Nnw0osu8lszy5nvcvVksH9Vj-MdYXbMMI",
  appKey: "2SMLhpbv4gAQsP33Qg1dr05z",
  serverURL: "https://nnw0osu8.api.lncldglobal.com",
});

export default {
    methods:{
        uploadImage:function () {
            const avatarUpload = document.getElementById('image').files[0];
            const file = new AV.File(avatarUpload.name, avatarUpload);

            //保存文件
            file.save().then((file) => {
                console.log(`文件保存完成。URL：${file.url}`);
            }, () => {
                // 保存失败，可能是文件无法被读取，或者上传过程中出现问题
            });
        }
    }
}
</script>

<style scoped>
    #graphic {
        width: 400px;
        display: inline;
        border: 5px solid gray
    }

    #input_img {
        width: 401px;
        height: 200px;
        border-bottom: 5px solid gray;
    }

    #image {
        color: transparent;
    }

    #samp_sc{
        width: 10px;
        height: 10px;
        border: 1px solid gray;

    }

    #p_SC {
        margin-top: 0px;
        border: 1px solid gray;
        border-radius: 3px;
        padding: 1.5px 4px 1.5px 4px;
        background-color: rgb(241, 241, 241);
        color:black;
        font-size: 14px;
    }

    li {
        list-style: none;
        margin-top: 8px;
        display: flex;
        flex-direction: row;
    }

    #all_text{
        display: flex;
        justify-content: flex-end;
        margin-top: 20px;
    }
  
    #iocn {
        width: 40px;
        height: 40px;
        border: 1px solid rgb(245, 241, 241);
        border-radius: 50%;
        display: flex;
        justify-content: center;
    }

    #iocn img{
        width: 25px;
        height: 25px;
        margin-top: 7.8px;
    }
</style>