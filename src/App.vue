<template>

<div id="app">
<TodoHeader></TodoHeader>
<TodoInput v-on:addTodo="addTodo"></TodoInput>
<TodoList v-bind:propsdata="todoItems" v-on:removeTodo="removeTodo"></TodoList> <!--하위 컴포넌트로 데이터 보낼때: v-bind:props속성이름="상위컴포넌트의 데이터 속성" -->
<TodoFooter v-on:removeAll="clearAll"></TodoFooter> <!--하위 이벤트를 받을때 : v-on:하위에서 지정한 이벤트 명="상위컴포넌트의 메서드명" -->
</div>

</template>

<script>
//  위에 생성한 컴포넌트 내용을 올바르게 인식하려면 스크립트 부분에 파일을 불러오는 코드를 추가해야 한다.
// import 불러올 파일의 내용이 담길 객체 from '불러올 파일 위치';
import TodoHeader from './components/TodoHeader.vue';
import TodoInput from './components/TodoInput';
import TodoList from './components/TodoList';
import TodoFooter from './components/TodoFooter';




/*
컴포넌트 등록 방법
components:{
    '컴포넌트 이름':컴포넌트 내용
}
*/
export default{
    components:{
        'TodoHeader':TodoHeader,
        'TodoInput':TodoInput,
        'TodoList':TodoList,
        'TodoFooter':TodoFooter
    },
    data(){
        return{
          todoItems:[]
        }   
    },created(){
        if(localStorage.length>0){
            for(var i=0;i<localStorage.length;i++){
                this.todoItems.push(localStorage.key(i));
            }
        }
    },
    methods:{
        addTodo(todoItem){
            //로컬 스토리지에 데이터를 추가하는 로직
            localStorage.setItem(todoItem,todoItem);
            this.todoItems.push(todoItem);
        },
        clearAll(){
            localStorage.clear();
            this.todoItems=[];
        },removeTodo(todoItem,index){
            localStorage.removeItem(todoItem);
            this.todoItems.splice(index,1);
        }
    }
}
</script>

<style>
body{
    text-align:center;
    background-color:#F6F6F8;
}
input{
    border-style:groove;
    width:200px;
}
button{
    border-style:groove;
}
.shadow{
    box-shadow:5px 10px 10px rgba(0,0,0,0.03)
}
</style>
