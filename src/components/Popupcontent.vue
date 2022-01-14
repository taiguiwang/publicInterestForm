<template>
    <div id="app">
        <div id="app_zi">
            <div id="shangChuan-img">
                <p>上传图片</p>
            </div>

            <div id="image">
                <div>图片</div>
                <div id="image-ul">
                    <ul>
                        <li><input type="file"></li>
                    </ul>
                    <img src="../assets/logo.png" alt="">
                </div>
            </div>

            <div>
                <ul>
                    <li>图片描述</li>
                    <li><input type="text" placeholder="请描述一下图片"></li>
                </ul>
            </div>

            <button>确定</button>
        </div>
    </div>
</template>

<style scoped>
#app {
    width: 800px;
    height: 400px;
    z-index: 9999;
    background-color: gray;
    position: absolute;
    top: 15%;
    left: 25%;
    border-radius: 15px;
}

button {
    width: 60px;
    height: 30px;
    border:none;
    border: 1px solid gray;
    border-radius: 8px;
    margin-bottom: -20px;
    margin-top: 40px;
}
#app_zi {
    width: 800px;
    height: 400px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding-left: 10px;
}

#shangChuan-img p{
    margin: -40px 0 60px 0;
    font-weight: 600;
}

#app_zi div {
    display: flex;
    /* align-content: center; */
    justify-content: center;
}

#image {
    display: flex;
    flex-direction: column;
}

#image-ul {
    display: flex;
    justify-content: center;
}

#image img{
    width: 100px;
    height: 100px;
}

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
</style>