<template>
    <div class="footer">
        <label>
            <input type="checkbox" v-model="ischeck"/>
            <span>已完成{{finishedCount}}件</span> / 总共{{todos.length}}件
        </label>
        <button class="btn" @click="delFinishedTodo">清除已完成任务</button>
    </div>
</template>

<script>
    export default {
        name: "footer",
        props:{
            todos:Array,
            selcetAll:Function,
            delFinishedTodo:Function
        },
        computed:{
            finishedCount(){
                return this.todos.reduce((total,todo)=> total+(todo.finished?1:0),0)
            },
            ischeck:{
                get(){
                    return this.finishedCount===this.todos.length && this.todos.length>0
                },
                set(value){
                    this.selcetAll(value)
                }
            }
        }
    }
</script>

<style scoped>
    .footer{
        margin-top: 20px;
        margin-bottom: 10px;
    }
    .btn{
        padding: 3px;
        position: relative;
        float: right;
        background-color: orange;
        color: white;
        border: orange 1px solid;
        border-radius: 3px;
        cursor: pointer;
    }
    .btn:hover{
        background: red;
    }
</style>