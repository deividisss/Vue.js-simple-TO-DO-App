<template>
  <div id="app">
    <AddUzduotis v-on:add-nauja-uzduoti="pridUzduoti"/>
    <!-- Nusiunčiam į  ./components/Uzduotys-->
    <Uzduotys v-bind:uzd_Obj_Mas="uzduociu_Objiektu_Masyvas"
     v-on:del-uzduotis-Item="deleteUzduotis" />
  </div>
</template>

<script>
import Uzduotys from '../components/Uzduotys';
import AddUzduotis from '../components/AddUzduotis';
import axios from 'axios';
export default {
  name: 'Home',
  components: {
    Uzduotys,
    AddUzduotis
  },
  //Data is a function which returns an array of objects
  data() {
    return {
      uzduociu_Objiektu_Masyvas: []
    }
  },
  methods: {
    deleteUzduotis(id){
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}
      `)
        .then(res => this.uzduociu_Objiektu_Masyvas = 
        this.uzduociu_Objiektu_Masyvas.filter(uzduociu_Objiektu_Masyvas => uzduociu_Objiektu_Masyvas.id !==id))
        .catch(err => console.log(err));
    },
      pridUzduoti(naujaUzduotis) {
        const { title, completed } = naujaUzduotis;

        axios.post('https://jsonplaceholder.typicode.com/todos', {
          title,
          completed
        })
          .then(res => this.uzduociu_Objiektu_Masyvas 
        = [...this.uzduociu_Objiektu_Masyvas, res.data])
          .catch(eerr => console.log(err));
/*         this.uzduociu_Objiektu_Masyvas 
        = [...this.uzduociu_Objiektu_Masyvas, naujaUzduotis];
        this.title = ''; */
    }
  },
  created(){
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10')
      .then(res => this.uzduociu_Objiektu_Masyvas = res.data)
      .catch(err => console.log(err));
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
    
  }
</style>
