<template>
  <div class="hello">
    <div class="form-group">
        <input ref="uploadfile" type='file' name="file" @change="uploadfile" webkitdirectory >
    </div>

    <el-carousel 
    :loop="false"
    :interval="1000"
    indicator-position="none">
      <el-carousel-item v-for="(item,index) in pictures" :key="index">
        <img :src="item">
      </el-carousel-item>
    </el-carousel>
  </div>
</template>

<script>
// import imgs from '../static/imgs'
export default {
  name: 'HelloWorld',
  data () {
    return {
      imgsUrl: [],
      fileArray: [],
      pictures: []
    }
  },
  methods: {
    uploadfile () {
      this.fileArray = this.$refs.uploadfile.files;
      // console.log('this.fileArray---', this.$refs.uploadfile.files)
      
      for( let item in this.fileArray) {
        // console.log('item===', item, this.fileArray[item].webkitRelativePath)
        this.imgsUrl.push(this.fileArray[item].webkitRelativePath)
      }
      this.imgsUrl.pop()
      this.imgsUrl.pop()
      this.imgsUrl.forEach((i)=>{
      this.pictures.push('../static/'+ i)
      })
      console.log('pictures===', this.pictures)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
