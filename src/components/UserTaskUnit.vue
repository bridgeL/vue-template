<template>
    <div class="unit">
        <input type="checkbox" :checked="taskObj.done" @click="task_click">
        <div class="content" :class="contentStyle" @click="task_click">
            {{taskObj.content}}
        </div>
        <button @click="btn_click">删除</button>
    </div>
</template>

<script>
    export default {
        name: 'UserTaskUnit',
        props: ['taskObj','del_task','do_task'],
        computed: {
            contentStyle() {
                return this.taskObj.done?"done":""
            },
        },
        methods: {
            btn_click() {
                if(confirm('确定删除吗？')){
                    this.del_task(this.taskObj.id)
                }
            },
            task_click(){
                this.do_task(this.taskObj.id)
            }
        },
    };
</script>

<style scoped>
    div.content {
        width: 215px;
    }

    .done {
        text-decoration-line: line-through;
    }

    .unit {
        display: flex;
        flex-direction: row;
        width: 300px;
        margin: 10px;
    }

    button{
        opacity: 0;
        height: 25px;
    }

    .unit:hover button{
        opacity: 1;
    }
</style>