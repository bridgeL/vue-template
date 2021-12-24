<template>
    <div>
        <div class="row">
            <div
                v-for="(label, index) in labelArr"
                :key="index"
            >
                <a href='./index' @click="label_click($event,label)">{{label}}</a>
            </div>
        </div>
        <hr />
        <div class="row small">
            <div
                v-for="(label, index) in labelArr"
                :key="index"
                :class="labelSel==label?'':'hide'"
            >
                s
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "NavigationBar",

    data() {
        return {
            labelArr: ["首页", "实验室", "归档"],
        };
    },

    props: ["open_label",'labelSel'],

    mounted() {},

    methods: {
        label_click(e,label){
            e.preventDefault()
            this.open_label(label)
        }
    },
};
</script>

<style scoped>
.row {
    display: flex;
    justify-content: space-around;
    align-items: center;
    width: 200px;
    margin: auto;
}
.small {
    font-size: 1px;
}
hr {
    width: 240px;
    margin-bottom: 0;
}
.hide {
    opacity: 0;
}
</style>