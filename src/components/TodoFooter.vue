<template>
<div class="clearAllContainer">
<span class="clearAllBtn" @click="clearTodo">Clear All</span>
</div>
</template>

<script>
export default{
    methods:{
        clearTodo(){
            this.$emit('removeAll'); // 상위 컴포넌트로 보내는 이벤트
            // localStorage.clear();
        }
    }

}
</script>

<style scoped>
.clearAllContainer{
    width: 8.5rem;
    height: 50px;
    line-height:50px;
    background-color:white;
    border-radius:5px;
    margin:auto ;
    text-align:center;
}
.clearAllBtn{
    color:#e20303;
    display: black;
   
}
</style>
