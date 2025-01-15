<script>

export default{
     data(){
        return{
            auto:{
                modell:"",
                kaucio:0,
                kilometerdij:0,
                napidij:0,
                leiras:""
            },
            autok:[]
        }
     },
     methods:{
        mentes(){
            this.autok.push(this.auto);
            this.auto={
                modell:"",
                kaucio:0,
                kilometerdij:0,
                napidij:0,
                leiras:""
            }
            this.$emit("autokkuld",this.autok);
        }
     }   
}

</script>

<template>

        <div class="card">
        <div class="card-body">
            <h4 class="card-title text-center">Új autó rögzítése</h4>
            <p class="card-text">
                <div class="mb-3">
                    <label for="modell" class="form-label">Autó modellje</label>
                    <input type="text" class="form-control" id="modell" v-model="auto.modell">
                </div>
                <div class="mb-3">
                    <label for="kaucio" class="form-label">Kauciós összeg</label>
                    <input type="number" class="form-control" id="kaucio" value="0" v-model="auto.kaucio">
                </div>
                <div class="mb-3">
                    <label for="kilometerdij" class="form-label">Kilométerdíj</label>
                    <input type="number" class="form-control" id="kilometerdij" value="0" v-model="auto.kilometerdij">
                </div>
                <div class="mb-3">
                    <label for="napidij" class="form-label">Napidíj</label>
                    <input type="number" class="form-control" id="napidij" value="0" v-model="auto.napidij">
                </div>
                <div class="mb-3">
                    <label for="leiras" class="form-label">Autó leírása</label>
                    <textarea class="form-control" id="leiras" rows="2" v-model="auto.leiras"></textarea>
                </div>
            </p>
            <input type="button" value="Mentés" class="btn btn-primary w-100" @click="mentes()">
        </div>
        </div>

     

</template>

<style scoped>

</style>
