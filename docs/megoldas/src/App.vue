<script>

import newCar from './components/newCar.vue';

export default{
    data(){
      return{
        megmutat : false,
        autok:[]
      }
    },
    methods:{
      mutat(){
        this.megmutat = !this.megmutat;
      },
      autokkuld(autok){
        this.autok = autok;
        console.log(this.autok);
      }
    },
    components:{
      newCar
    }      

}

</script>

<template>

  <div class="container">
      <h2 class="text-center">Autókölcsönző</h2>
      <input type="button" class="btn btn-primary mb-4" value="Új autó rögzítése" @click="mutat()"> <br>
      <newCar v-if="megmutat" @autokkuld="autokkuld"/>
  </div>

</template>

<style scoped>

</style>
