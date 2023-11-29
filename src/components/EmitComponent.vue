<template>
<div>
<center> <v-btn color="blue" elevation="12"  @click="emiting()" >Emiting data</v-btn></center>

</div>
</template>
<script>


export default {
  data() {
    return{
      emitingData:"emited",
    };

  },
  methods:{
    emiting(){
      // child to parent data pass karnne emiting walin
      // "emitingData "->kiyanne massage eka
      // this.emiting data->data ekaa
      // this.emitingdata eken massage eka otomaticaly bind karanawa
      this.$emit("emitingData",this.emitingData);
    },
  },
}
</script>
