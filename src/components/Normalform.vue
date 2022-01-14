<template>
    <div>
        <form action="#">
            <ul>
                <li id="functionNmae">组织名称</li>
                <li><input id="Organize_value" type="text"><samp id="Organize_span"><img src="../assets/icon/党组织_名称.png"></samp></li>

                <li id="functionNmae">创始人</li>
                <li><input id="Founder_value" type="text"></li>

                <li id="functionNmae">愿景</li>
                <li><input id="Vision_value" type="text"></li>

                <li id="functionNmae">地点</li>
                <li><input id="Location_value" type="text"></li>

                <li id="functionNmae">经纬度</li>
                <li><input id="LAL_value" type="text"></li>
            </ul>
            <button id="btn" @click="tiJiao">提交</button>
        </form>
    </div>
</template>
<script>
const AV = require("leancloud-storage");
// const { Query, User } = AV;
AV.init({
  appId: "SdXtqoa4Yd4znA5MwlFQYyXG-gzGzoHsz",
  appKey: "wwggQgtDEa9EG49u9dtcV5WR",
  serverURL: "https://sdxtqoa4.lc-cn-n1-shared.com",
});

export default {
    methods:{
        tiJiao(){
            var Organize = document.getElementById("Organize_value").value;
            var Founder = document.getElementById("Founder_value").value;
            var Vision = document.getElementById("Vision_value").value;
            var Location = document.getElementById("Location_value").value;
            var LAL = document.getElementById("LAL_value").value;

            // 声明 class
            const BasicInformation = AV.Object.extend('BasicInformation');
            // 构建对象
            const basicInformation = new BasicInformation();
            // 为属性赋值
            basicInformation.set('Organize', Organize);
            basicInformation.set('Founder', Founder);
            basicInformation.set('Vision', Vision);
            basicInformation.set('Location', Location);
            basicInformation.set('LAL', LAL);

            // 将对象保存到云端
            basicInformation.save().then((basicInformation) => {
            // 成功保存之后，执行其他逻辑
            console.log(`保存成功。objectId：${basicInformation.id}`);
            }, () => {
            // 异常处理
            });
        }
    }
}
</script>
<style scoped>
li{
    list-style: none;
    margin-top: 8px;
}

input{
    width: 300px;
    height: 30px;
    border: none;
    border: 1px solid gray;
    border-radius: 5px;
}

#functionNmae{
    margin-right: 250px;
    font-size: 16px;
    font-weight: 600;
}

#Organize_span img{
    width: 30px;
    height: 30px;
    margin-left: -35px;
    margin-bottom: -12px;
}
form {
    border: 5px gray solid;
    border-radius: 20px;
    padding: 20px 40px 20px 0px;
}
</style>