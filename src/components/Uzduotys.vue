<template>
    <div>
        <!--Atvaizduojam masyva elemntus -->
        <!-- v-bind:key priskir unikalu id -->
        <div v-bind:key="loop_uzd_Obj_Mas.id" v-for="loop_uzd_Obj_Mas in uzd_Obj_Mas">
              <!-- Nusiunčiam į  ./UzduotisItem -->
              <UzduotisItem v-bind:loop_uzd_Obj_Mas_Item="loop_uzd_Obj_Mas" 
              v-on:del-uzduotis-Item="$emit('del-uzduotis-Item',loop_uzd_Obj_Mas.id)"/>
        </div>
    </div>
</template>

<script>

import UzduotisItem from './UzduotisItem';
export default {
    name: "Uzduotys",
    components: {
        UzduotisItem
    },
// props [kintamojo pavadinims] kuri pasijama iš './App';
    props: ["uzd_Obj_Mas"]
}
</script>

<style scoped>

</style>
