<template>
<selection>
<ul>
<li v-for="(todoItem,index) in propsdata"  class="shadow">
<i class="checkBtn fa fa-check" aria-hidden="true"></i>
{{ todoItem }}
<span class="removeBtn" type="button" @click="removeTodo(todoItem,index)">
<i class="fa fa-trash-o" aria-hidden="true"></i>
</span>
</li>
</ul>
</selection>


</template>

<script>
export default{
    props:['propsdata'],   // 상위 컴포넌트에서 데이터를 받을때사용하는 속성 : pros:['props속성이름']
    /* 더이상 사용x = propsdata로 받았기 때문
    data(){
        return {
            todoItems : []
            }
    },*/
    /*
    이부분은 app.vue로 이동한다!
    created(){
        if(localStorage.length>0){
            for(var i=0;i<localStorage.length;i++){
                this.todoItems.push(localStorage.key(i));
            }
        }
    },*/
     methods:{
        removeTodo(todoItem,index){
            this.$emit('removeTodo',todoItem,index);
           // localStorage.removeItem(todoItem);  이건 상위에서 해도되고 하위도 된다!
            //this.todoItems.splice(index,1); 이젠 하위에선 반영이 안되니 app.vue로 이동!
        }
    }

}
</script>

<style>
ul{
    list-style-type:none;
    padding-left:0px;
    margin-top:0;
    text-align:left;
}
li{
    display:flex;
    min-height:50px;
    height:50px;
    line-height:50px;
    margin:0.5rem 0;
    padding: 0 0.9rem;
    background: white;
    border-radius:5px;
}
.checkBtn{
    line-height:45px;
    color:#62acde;
    margin-right:5px;
}
.removeBtn{
    margin-left:auto;
    color:#de4343;
}
</style>
