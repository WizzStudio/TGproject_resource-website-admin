<template>
  <div class="home">
    <div class="navbar navbar-inverse" role="navigation" id="menu-nav">
      <div class="container">
        <div class="navbar-header">
          <a class="navbar-brand" href="#">学习资源网站·后台管理</a>
        </div>
      </div>
    </div>
    <!--欢迎-->
    <div class="container mainPart">

      <div class="page-header">
        <h1>欢迎使用后台管理系统 <small>感谢支持</small></h1>
      </div>

      <div class="row container">
        <div class="alert alert-success alert-dismissible col-md-6" role="alert">
          <button type="button" class="close" data-dismiss="alert" aria-label="Close"><span aria-hidden="true">&times;</span></button>
          <h5>后台管理注意事项 <br><small>我们默认遵守如下约定：请在第一段文字写下标题，请在第二段文字写下介绍内容</small></h5>
        </div>


        <div class="alert alert-info alert-dismissible col-md-6" role="alert">
          <button type="button" class="close" data-dismiss="alert" aria-label="Close"><span aria-hidden="true">&times;</span></button>
          <h5>后台管理注意事项 <br><small>请在前两段文字后放置图片，请在图片后放置分享链接</small></h5>
        </div>
      </div>

      <!--选择框-->
      <!--------------------------你只需要拿这里---------------------------------------->
      <div class="panel panel-default">
        <div class="panel-heading">方向：</div>
        <div class="panel-body">
          <select id="mainDirection" @click="changeText">
            <option>—请选择—</option>
          </select>
        </div>
      </div>
      <div class="panel panel-default">
        <div class="panel-heading">方向细分：</div>
        <div class="panel-body">
          <select id="SecDirection">
            <option>—请选择—</option>
          </select>
        </div>
      </div>
      <div class="components-container" style="margin-bottom: 100px">
        <div class="editor-container">
          <UE :defaultMsg=defaultMsg :config=config ref="ue"></UE>
        </div>
        <button @click="getUEContent()" class="btn btn-default" style="float:right;margin-top: 10px">获取内容</button>

      </div>
  </div>
</div>
</template>

<script>
  import UE from './components/Editer.vue';
  export default {
    components: {UE},
    data() {
      return {
        defaultMsg: '这里是UE测试',
        config: {
          initialFrameWidth: null,
          initialFrameHeight: 350
        },
        mainData:["Java Web", "PHP Web","Web 前端","产品经理","AI大数据"],
        secData:[
          ["java 语言学习", "J2EE","数据库","框架学习","java工具"],
          ["php 语言学习", "环境搭建","实现CURD","MVC编程模式","php框架学习"],
          ["HTML", "CSS","JavaScript","前端框架","前端工具"],
          ["产品策划", "产品设计","产品管理","产品运营"],
          ["Spark", "Hadoop","Storm","Kafka","Scala"]
        ]
      }
    },
    mounted(){
      /* 获取省对象*/
      var mainDirection = document.getElementById("mainDirection");
      var SecDirection = document.getElementById("SecDirection");
      /*实例化组*/
      for (let i = 0; i < this.mainData.length; i++) {
        var option = new Option(this.mainData[i], i);
        mainDirection.appendChild(option);
      }
    },
    methods: {
      getUEContent() {
          /* 获取省对象*/
          var mainDirection = document.getElementById("mainDirection");
          var SecDirection = document.getElementById("SecDirection");
          /*实例化组*/
          for (let i = 0; i < this.mainData.length; i++) {
            var option = new Option(this.mainData[i], i);
            mainDirection.appendChild(option);
          }
          var index = mainDirection.value;
          var city = this.secData[index];
          var pos = SecDirection.value;
          var tag = this.mainData[index];
          var sub_tag = city[pos];
          var content = this.$refs.ue.getUEContent();
        /* alert(content);
          alert(tag);
          alert(sub_tag);*/
          var postData = {
            'tag': tag,
            'sub_tag': sub_tag,
            'content': content
          };
          var postJson = JSON.stringify(postData);
          this.$http.post("http://127.0.0.1:8000/post_a/", postJson, {
              headers: {"Content-Type": "application/json"}
          })
            .then( res => {
              console.log(res.data)
            })
            .catch(err => {
              console.log(err);
            })
//          $.post("http://127.0.0.1:8000/post_a/",{"tag":"1","sub_tag":"2","content":"sf"}, function(ret){$('#result').html(ret.result)});

      },
      changeText() {
        var mainDirection = document.getElementById("mainDirection");
        var SecDirection = document.getElementById("SecDirection");
        //清空
        SecDirection.options.length = 1;
        //获取选择框的value值
        var index = mainDirection.value;
        let city = this.secData[index];
        for (var i = 0; i < city.length; i++) {

         var option = new Option(city[i], i);
         SecDirection.appendChild(option);
    }
  }

    }
  };
</script>

<style>
  body{
    margin: 0;
    background: url("./assets/background.png") repeat;
  }
  .mainPart{
    width: 1200px;
    margin: 0 auto;
  }
</style>
