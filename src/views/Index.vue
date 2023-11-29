<template>
    <div>
      <HedearComponent/>

        <FormComponent @formData="getData"/>
        {{ emitingForm }}
        <br/>
        <SliderComponent/>
        <br>
        <DialogComponent/>
        <br>
         <ConditinalExample/>
        <ListComponent/>
        <!-- eent ekak triger wenne -->
        <!-- function eken wenne data refer karana ekak -->

        <!-- @emitingData athanin ganna massage -->
        <!-- parent component eke trigger wena function eka  -->
        <!-- emiting kiyana data eka trigger wela get data ekata pass wenawa -->
       <!-- getemitdata kiyanne function trigger weemak wnene data ganimak -->
        <EmitComponent @emitingData="getEmitData"/>

        <center><span class="text-danger">{{ emitedData  }}</span></center><br/>



        <center><v-btn @click="submit">post data</v-btn></center><br/>
        <v-btn @click="check">{{changebuttonData }}</v-btn>
        <br>
        <span class="text-danger font-weight">{{getAgoTime }}</span>

    </div>
</template>
<script>
// ada date eka ganan libray eka
import moment from "moment";
import axios from "axios";
import FormComponent from '@/components/FormComponent.vue';
import SliderComponent from '@/components/SliderComponent.vue';
import DialogComponent from '@/components/DialogComponent.vue';
import ConditinalExample from '@/components/ConditinalExample.vue';
import ListComponent from '@/components/ListComponent.vue';
import EmitComponent from '@/components/EmitComponent.vue';


export default{
  // parent to child props pass karnne mulinma variable all karnawa
  data(){
    return{
      propData:"hey",
      emitedData:"watiing data",
      emitingForm:{},
      btnName:"",
      // date object ekak
      today: new Date('Sun Nov 26 2023 17:17:27'),
  };
  },
    components: {
    FormComponent,
    SliderComponent,
    DialogComponent,
    ConditinalExample,
    ListComponent,
    EmitComponent



},
async created(){
 await this.fetchApiData();
},
// realtime variable ekak refresh karanna use karanwa
// computed property realtime update wenawa
computed:{
  // function ekak widiyta hadanne but ethanin ganne variable ekak widyata value eka change wenne
// btn variable eka computed eka athule kothan ahari tiynawda kiyala balala update wenawa
// realtime use wenne
changebuttonData(){
  return this.btnName;
},

getAgoTime(){
  // date ekata adala function acecce karnane moment use karnawa
return moment(this.today).fromNow();
},

},
mounted(){
  setInterval(
    ()=>{
      this.today= new Date('Sun Nov 26 2023 17:17:27');
    },3000
  );
},
methods:{
  // hama welema data insert karnnne object ekak widiyaata
 async submit(){
    // payload = {
    //   firstname:"sger",
    //   lastname:"eger"

   await axios.post("https://reqres.in/api/users", this.emitingForm)
  },
  async update(){
    // payload = {
    //   firstname:"sger",
    //   lastname:"eger"

   await axios.put("https://reqres.in/api/users", this.emitingForm)
  },

  // emiting data eka gannawa eka parent eke emitng value ekat equeal karanwa
  getEmitData(data){
    this.emitedData = data;
  },
  getData(data){
    this.emitingForm=data;
  },


 async fetchApiData(){
    const res = await axios.get("https://reqres.in/api/users");
    console.log(res.data);
  },
  // button eke method eka call karanwa eke variable eka
  // chanege karnawa e welawema button ekata adalawa computed method ekak tiynawada kiyala balala e welawema update karanwa
// check function
  check(){
this.btnName="sdverver";
  },
},
};
</script>
