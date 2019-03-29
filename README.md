# myfirst-github
<template>
  <div class="blogAdd wrap blog">
      <form role="form" @submit.prevent="blogadd">
        <div class="form-group">
            <label for="name">名称</label>
            <input type="text" class="form-control" v-model="title" id="name" placeholder="请输入标题">
        </div>
        <div class="form-group">
            <label for="inputfile">请输入文章内容</label>
            <textarea  class="form-control" cols="30" rows="10" v-model="body"></textarea>
        </div>
        <button type="submit" class="btn btn-default">提交</button>{{success}}
        </form>
  </div>

</template>

<script>
export default {
  name: 'blogAdd',
  data(){
      return{
          title:"",
          body:"",
          success:""
      }
  },
  methods:{
    blogadd(){
        // let _this = this;
        // let xhr = new XMLHttpRequest();
        // xhr.open('POST','https://www.hzbiz.net/1203/vueapi/blogadd.php',true);
        // xhr.setRequestHeader("Content-Type","application/x-www-form-urlencoded");
        let data="title="+this.title+"&body="+this.body+"&action=1";
        // xhr.send(data);
        // xhr.onreadystatechange=function(){
        //     if(this.status==200 && this.readyState == 4){
        //         let json = JSON.parse(this.responseText);
        //         _this.success = json.message;
        //     }
        // }    
        this.axios.post("https://www.hzbiz.net/1203/vueapi/blogadd.php",data)
        .then(
            (text)=>{
                console.log(text)
                this.success = text.data.message
            }
        )
        .catch(
            (err)=>{
                console.log(err)
            }
        )
    }
  },
  props:{
      msg:String
  }
}
</script>


<style scoped>

</style>

