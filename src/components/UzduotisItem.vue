<template>
    <div class="Uzduotis-Item" v-bind:class="{'is-complete':loop_uzd_Obj_Mas_Item.completed}">
       <!-- new code -->
      <p>
        <input type="checkbox" v-on:change="markComplete">
        Užduotis: {{loop_uzd_Obj_Mas_Item.title}}
        <!-- su $emit paleidžiam iventa pavadinimu ,,del-todo" kuriam priskirim uzdoties kuria norim istrint id -->
        <button @click="$emit('del-uzduotis-Item', loop_uzd_Obj_Mas_Item.id)" class="del">x</button>
        </p>
    </div>
</template>

<script>

export default {
    name: "UzduotisItem",
    props: ["loop_uzd_Obj_Mas_Item"],
    methods: {
      markComplete() {
        console.log(123);
        this.loop_uzd_Obj_Mas_Item.completed = !this.loop_uzd_Obj_Mas_Item.completed;
      }
    }


}
</script>

<style scoped>
    .Uzduotis-Item {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
    overflow: auto;
  }
  .is-complete {
    text-decoration: line-through;
  }
  .del {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  }
</style>
