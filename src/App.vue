<template>
  <div id="app">
        <span class="fileinput-button">
            <span>上传</span>
            <input @change="changeFile()"  ref="FileEvent" type="file">
        </span>
        <div v-html="img"></div>
  </div>

</template>

<script>


export default {
  name: 'App',
  data(){
    return {
      img:""
    }
  },
  methods:{
    changeFile(){
              var that = this;
              var file = this.$refs.FileEvent.files[0];
              console.log(file)
              if(!/image\/\w+/.test(file.type)){
                alert("文件必须为图片！");
                return false;
              }
               var reader = new FileReader();
               reader.readAsDataURL(file);
               reader.onload = function(e){
               that.img= '<img src="'+this.result+'" style="width:3rem;height:3rem;" alt=""/>'
              }
             
    }
  }
}
</script>

<style scoped>
       .fileinput-button {
            position: relative;
            display: inline-block;
        }

        .fileinput-button input{
            position: absolute;
            right: 0px;
            top: 0px;
            opacity:0;
        }
</style>
