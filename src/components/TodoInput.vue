<template>

<div>
<input type="text" v-model="newTodoItem">
<button v-on:click="addTodo">추가</button>
</div>
</template>

<script>
export default{
data(){
    return {
        newTodoItem:''
    }
},
methods: {
    addTodo(){
       localStorage.setItem(this.newTodoItem,this.newTodoItem); 
       //setItem()은 로컬 스토리지에 데이터를 추가하는 API 
       // (키,값)
    }
}
}
</script>

<style>

</style>
