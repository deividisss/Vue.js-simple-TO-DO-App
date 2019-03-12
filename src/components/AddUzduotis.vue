<template>
    <div>
        <form @submit="addUzduoti">
            <input type="text" v-model="title" name="title" placeholder="Pridėti užduotis....">
            <input type="submit" value="Pridėti" class="btn">
        </form> 
    </div>
</template>

<script>
// import uuid from 'uuid';
export default {
    name: "PridėtiUžduotį",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addUzduoti(e) {
            e.preventDefault();
            const naujaUzduotis = {
                // id: uuid.v4(),
                title: this.title,
                completed: false
            }
            //Siunčiam parent elementui sukurta nauja užduoti
            this.$emit('add-nauja-uzduoti', naujaUzduotis);
        }
    }
}
</script>

<style scoped>
  form {
    display: flex;
  }
  input[type="text"] {
    flex: 10;
    padding: 5px;
  }
  input[type="submit"] {
    flex: 2;
  }
  
  .btn {
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }
  .btn:hover {
    background: #666;
  }
</style>
