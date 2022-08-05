<template>
    <div class="main">
        暂无活动哈~
        <!-- <drap-component>
            <div>okokokok</div>
        </drap-component> -->

        <a href="localhost:7000/1.css" download="text">下载docx</a>
<!--        <div @click="returnDocx" class="return">返回一个docx文件</div>-->
<!--        <div @click="down">瞎子问党</div>-->

    </div>
</template>

<script>
    // import drapComponent from "../components/drapComponent";
    import {
        getDocx
    } from "../axios/user";
    export default {
        name: "activity",
        // components:{
        //     drapComponent
        // }
        methods: {
            returnDocx() {
                getDocx().then(result => {
                    console.log(result)
                    var blob = new Blob([result.data.msg], {type: 'application/vnd.openxmlformats-officedocument.wordprocessingml.document'});
                    // var blob = new Blob(result.data.msg);
                    console.log(blob)
                    let url = window.URL.createObjectURL(blob)
                    
                    let link = document.createElement('a'); //创建a标签
                    link.style.display = 'none'; //样式无
                    link.href = url; //设置请求的url
                    // 指定文件名&文件类型(后缀名)
                    let fileName = `word文档.doc`;
                    // let fileName = `压缩包.zip`;
                    link.setAttribute('download', fileName);
                    link.click(); //操作执行该a标签
                    // 释放创建的对象(创建的新的URL必须通过该方法释放)
                    window.URL.revokeObjectURL(url);

                    // let blob = new Blob(result.data)
                    // console.log(blob)
                    // const blobUrl = window.URL.createObjectURL(blob);
                    // const a = document.createElement('a');
                    // a.style.display = 'none';
                    // a.download = title;
                    // a.href = blobUrl;
                    // a.click();
                    // document.body.removeChild(a);
                })
            },
            down() {
                window.open('http://localhost:7000/(2017)粤71行终253号行政判决书.doc', '_self');
            }
        },
    }
</script>

<style scoped>
    .return {
        cursor: pointer;
    }

    .main {
        padding-top: 60px;
        min-height: calc(100vh - 60px);
        min-width: 60vw;
        font-size: 50px;
        background: linear-gradient(to bottom, #1D2B64, #F8CDDA);
        line-height: calc(80vh);
        text-align: center;
        font-weight: 100;
    }
</style>