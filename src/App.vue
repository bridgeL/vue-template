<template>
    <div id="app">
        <Face />
        <NavigationBar :open_label="open_label" :labelSel="labelSel"/>
        <MsgPool :labelSel="labelSel" />
    </div>
</template>

<script>
import Face from "@/components/Face.vue";
import NavigationBar from "@/components/NavigationBar";
import MsgPool from "@/components/MsgPool";

export default {
    name: "App",
    data() {
        return {
            labelSel: sessionStorage.getItem('labelSel')||"首页",
        };
    },
    components: {
        Face,
        NavigationBar,
        MsgPool,
    },
    methods: {
        open_label(label) {
            this.labelSel = label;
            sessionStorage.setItem('labelSel',label)
        },
    },
};
</script>
<style>
#app {
    text-align: center;
}
html {
    background: rgb(243, 242, 242);
}
</style>