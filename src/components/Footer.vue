<template>
    <div class="unit" v-show="taskArr.length">
        <input type="checkbox" v-model="checkValue">
        <div class="msg">已完成{{finish}}/全部{{taskArr.length}}</div>
        <button v-show="finish" @click="btn_click">删除所有已完成</button>
    </div>
</template>

<script>
    export default {
        name: 'Footer',
        computed: {
            finish() {
                return this.taskArr.reduce((cnt, taskObj) => { return cnt + taskObj.done }, 0)
            },
            checkValue:{
                get(){
                    return this.finish==this.taskArr.length
                },
                set(value){
                    this.set_all_task(value)
                }
            }
        },
        props: ['taskArr', 'del_all_done_task','set_all_task'],
        methods: {
            btn_click() {
                if (confirm('确定删除全部已完成吗？')) {
                    this.del_all_done_task()
                }
            },
        }
    };
</script>

<style scoped>
    .unit {
        display: flex;
        flex-direction: row;
        align-items: center;
        margin: 10px;
    }

    .msg {
        width: 150px;
    }

    input {
        background-color: -internal-light-dark(rgb(255, 255, 255), rgb(59, 59, 59));
    }
</style>