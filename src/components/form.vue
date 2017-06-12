<template>
    <div class="row" id="translateForm">
        <div class="col-md-6 col-md-offset-3">
            <form id="transform" class="form-inline well" v-on:submit="formSubmit">
                <input class="form-control" type="text" v-model="textToTranslate" placeholder="Enter a Word">
                <select class="form-control" v-model="language">
                <option value="it">Italian</option>
                <option value="en">English</option>
                <option value="fr">French</option>
            </select>
                <input class="btn btn-primary" type="submit" value="Traducir">
            </form>
        </div>
    </div>
</template>

<script>

export default {
  name: 'translateForm',
  data(){
      return{
          textToTranslate:'',
          language:''
      }
  },
  created(){
      this.language= 'it';
  },
  methods: {
      formSubmit(e){
          this.$emit('formSubmit', this.textToTranslate, this.language);
          e.preventDefault();
          
      }
  }
}
</script>

<style>

#transform{
    border-radius: 10px;
    border: 1px #fff solid;
}
</style>