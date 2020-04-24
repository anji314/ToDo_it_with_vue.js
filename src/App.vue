<template>

<div id="app">
<TodoHeader></TodoHeader>
<TodoInput></TodoInput>
<TodoList></TodoList>
<TodoFooter></TodoFooter>
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
