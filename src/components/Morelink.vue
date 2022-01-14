<template>
<div id="form">
    <div class="add_view"> 更多链接&nbsp;<button @click="addRegex()" id="count" value=1> + </button>&nbsp;&nbsp;<button @click="Submit">确定</button></div>
      <div class="regex_modals">
        <div v-for="(item,index) in regexNameList"
          :key="index"
          class="regex_input">
          <div id="div-f">
                <div>链接</div>
                <div class="div">
                  <input class="input-calss" placeholder="请输入链接" id="input_link" v-model="item.name"/>
                </div>

                <div>描述</div>
                <div class="div">
                  <input class="input-calss" placeholder="描述" id="input_miaoSu" />
                </div>
          </div>
          <span class="delete" @click="deleteRegex(index)"><a> x </a></span>
        </div>
      </div>
</div>
</template>
<script>
//leancloud数据库
const AV = require("leancloud-storage");
AV.init({
  appId: "SdXtqoa4Yd4znA5MwlFQYyXG-gzGzoHsz",
  appKey: "wwggQgtDEa9EG49u9dtcV5WR",
  serverURL: "https://sdxtqoa4.lc-cn-n1-shared.com",
});

export default {
  data() {
    return {
      regexNameList: [
        {
          name: "",
        }
      ],
    };
  },
  methods: {
    // 添加一个模糊规则输入框
    addRegex() {
      //在当前组件里找class名为input-class的所以元素
      var count_input = document.querySelectorAll(".input-calss");
      //循环拿到input所以元素的个数进行for循环
      for( let i = 0; i < count_input.length; i++){
        //给input添加id
        count_input[i].id = 'input_' + i;
      }

      //添加边框高度（1、只添加一次）
      let x = 320;
      for(let y = 2;y <= count_input.length;y+=2){
           x+=220;
          document.getElementById("form").style.paddingBottom = x +"px";
      }

      //复制
      this.regexNameList.push({ name: ""});
    },
    // 删除相应模糊规则输入框
    deleteRegex(index) {
      if (this.regexNameList.length > 1) {
        this.regexNameList.splice(index, 1);
      } else {
        this.regexNameList[index].name = "";
      }

      //获取当前页面有多少个input
      var count_input = document.querySelectorAll(".input-calss");
      //拿到当前all的input除2在乘上每2个input的高度
      let all_input_height =(count_input.length / 2 )* 220;
      //判断当前有多少input，然后改对应的高度
      if(count_input.length ==2 ){
        document.getElementById("form").style.paddingBottom = 320 +"px";
      }else if(count_input.length > 2){
        all_input_height -= 120;
        document.getElementById("form").style.paddingBottom = all_input_height +"px";
      }

    },Submit(){
      // 判断当前组件一共有多少input
      var inputCount = document.querySelectorAll(".input-calss");
      let arr = [];
      // 循环全部input，拿inputID的值
      for(let i = 0;i <= inputCount.length;i++){
        // 拿到所有inputID的值
        let inputId = inputCount[i].id;
        //测试1
        arr.push(inputId);

        //把对应input的值存到leancloud数据库上
        //声明 class
        const MoreLinks = AV.Object.extend('MoreLinks');
        // 构建对象
        const moreLinks = new MoreLinks();

        // 为属性赋值
        let inputValue = inputCount[i].value;
        //用奇、偶数来判断是link还是Description
        if(arr.indexOf(arr[i]) % 2 == 0){
          moreLinks.set('link',inputValue);
        }else {
          moreLinks.set('Description',inputValue);
        }

        // 将对象保存到云端
        moreLinks.save().then((moreLinks) => {
        // 成功保存之后，执行其他逻辑
        console.log(`保存成功。objectId：${moreLinks.id}`);
        }, () => {
        // 异常处理
        });
      }
 
      // // 声明 class
      // const MoreLinks = AV.Object.extend('MoreLinks');
      // // 构建对象
      // const moreLinks = new MoreLinks();
      // // 为属性赋值
      // moreLinks.set('link1',x);

      // // 将对象保存到云端
      // moreLinks.save().then((moreLinks) => {
      // // 成功保存之后，执行其他逻辑
      // console.log(`保存成功。objectId：${moreLinks.id}`);
      // }, () => {
      // // 异常处理
      // });
    },
  },

};
</script>

<style scoped>
input{
    width: 300px;
    height: 30px;
    border: none;
    border: 1px solid gray;
    border-radius: 5px;
}

#input-m{
    width: 300px;
    height: 80px;
}

.regex_input{
    width: 350px;
    height: 40px;
    margin-top: 180px;
}

.regex_modals{
    width: 350px;
    height: 40px;
    display: flex;
    flex-direction: column;
}

#div-f{
    display: flex;
    flex-direction: column;
    border: 2px solid gray;
    border-radius: 10px;
    padding: 10px 10px 180px 10px;
}

.add_view{
    margin-top: 60px;
    margin-bottom: -160px;
}

a{
    border: 1px solid gray;
    border-radius: 5px;
    padding: 0px 9px 0px 9px;
    background-color: rgb(230, 227, 227);
    font-size: 20px;
}

.delete{
    margin-left: -15px;
    margin-top: 25px;
}
#form {
    border: 5px gray solid;
    border-radius: 20px;
    margin-top: 50px;
    padding-left: 40px;
    padding-right: 20px;
    padding-bottom: 320px;
}
</style>
