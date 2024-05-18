<template>
    <h1>Result is {{ result }} ms</h1>
  <h1>{{ message}}</h1>
</template>

<script>
export default {
    data(){
      return{
        message:null,
      }
    },
    props:['result'],
    mounted(){
     if(this.result < 200){
      this.message='You are awesome ';
     }
     else if(this.result > 200 && this.result < 500){
        this.message='You are normal'
     }
     else{
        this.message='You are slow'
        
     }
    }

}
</script>

<style>

</style>