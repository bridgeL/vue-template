<template>
    <div>
        <input ref="userinput" type="text" placeholder="输入你要做的事，enter添加" @keyup.enter="add">
    </div>
</template>

<script>
    import { nanoid } from "nanoid";
    export default {
        name: 'Top',
        methods: {
            add(e) {
                var content = (e.target.value).replace(/^\s+|\s+$/g, '')
                if (content) {
                    this.add_task({ id: nanoid(), content: content, done: false })
                }
                e.target.value = ""
            },
            focus_input(){
                var e = this.$refs['userinput']
                e.focus()
            }
        },
        props: ['add_task']
    };
</script>

<style scoped>
    input {
        /* -webkit-appearance: none;
        -moz-appearance: none; */
        outline: none;

        font-size: 14px;
        height: 27px;
        margin:10px;
        width: 300px;
    }

    input:focus {
        border:2px solid;

        transition: border linear .2s, box-shadow linear .5s;

        -moz-transition: border linear .2s, -moz-box-shadow linear .5s;

        -webkit-transition: border linear .2s, -webkit-box-shadow linear .5s;

        border-color: rgba(93, 149, 242, .75);

        box-shadow: 0 0 8px rgba(93, 149, 242, .105);

        -moz-box-shadow: 0 0 8px rgba(93, 149, 242, .5);

        -webkit-box-shadow: 0 0 8px rgba(93, 149, 242, 3);

    }
</style>