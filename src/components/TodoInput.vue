<template>

<div class="inputBox shadow">
<input type="text" v-model="newTodoItem" placeholder="type what you have to do" v-on:keyup.enter="addTodo">
<span class="addContainer" v-on:click="addTodo">
<i class="addBtn fa fa-plus" aria-hidden="true"></i>

</span>

<modal v-if="showModal" @close="showModal = false">
<h3 slot="header">경고</h3>
<span slot="footer" @click="showModal = false">
할 일을 입력하세요.
<i class="closeModalBtn fa fa-times" aria-hidden="True"></i>
</span>
</modal>
</div>
</template>

<script>
import Modal from './common/Modal.vue';
export default{
data(){
    return {
        newTodoItem:'',
        showModal:false
    }
},
components:{
        Modal:Modal
    },
methods: {
     //setItem()은 로컬 스토리지에 데이터를 추가하는 API 
     // (키,값)
    addTodo(){
        if(this.newTodoItem !=''){
            var value = this.newTodoItem&&this.newTodoItem.trim(); //인풋 박스 앞뒤 공백 문자열 제거
           this.$emit('addTodo',value);
           //localStorage.setItem(value,value); 상위 컴포넌트가 하는 일이므로 삭제!
            this.clearInput();
        }else{
            this.showModal= !this.showModal;
        }
        
    },
    clearInput(){
            this.newTodoItem=''; // 인풋 박스의 입력 값을 초기화
    }
      
    }
    
}
</script>

<style>
input:focus{
    outline:none;
}
.inputBox{
    background :white;
    height:50px;
    line-height:50px;
    border-radius:5px;
}
.inputBox input{
    border-style:none;
    font-size: 0.9rem;
}
.addContainer{
    float:right;
    background:linear-gradient(to right,#6478FB,#8763FB);
    display:inline-block;
    width:3rem;
    border-radius: 0 5px 5px 0;
}
.addBtn{
    color:white;
    vertical-align:middle;
}

</style>
