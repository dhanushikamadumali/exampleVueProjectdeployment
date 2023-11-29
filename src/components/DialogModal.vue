<template>
  <div>
      <v-card :title="title">
        <FormComponent :FormData="FormData" @FormData="formdata"/>
        <br/>
        <br/>
      </v-card>

  </div>
</template>
<script>
import FormComponent from '@/components/FormComponent.vue';
// import { stringify } from 'postcss';

export default{
components:{
  FormComponent,
},
data(){
return{
form:{}
};

},
// parent eken ena titke eka
// parent component eken ena list comonent eka access karnawa
// props:{
// title:String,
// FormData:Object,

// },
methods: {
  getData(data){
    this.form = data;
    this.$emit("formData",this.form);

  }
},
}

</script>
