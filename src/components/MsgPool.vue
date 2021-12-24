<template>
    <div>
        <div v-show="labelSel == '首页'">
            <br />
            <div class="row">
                石灰岩（Limestone）简称灰岩，以方解石为主要成分的碳酸盐岩 。有时含有白云石、粘土矿物和碎屑矿物，有灰、灰白、灰黑、黄、浅红、褐红等色，硬度一般不大，与稀盐酸有剧烈的化学反应。按成因分类属于沉积岩
            </div>
            <br />
            <br />
            <a href="https://github.com/bridgeL/github.bridgeL.io">Github</a>
        </div>

        <div v-show="labelSel == '实验室'">
            <div
                class="row"
                v-for="(htmlLink, index) in labLinkArray"
                :key="index"
            >
                <div class="index">{{ index }}</div>
                <a class="title" :href="htmlLink.href">{{ htmlLink.title }}</a>
            </div>
        </div>

        <div v-show="labelSel == '归档'">
            <div
                class="row"
                v-for="(htmlLink, index) in htmlLinkArray"
                :key="index"
            >
                <div class="index">{{ index }}</div>
                <a class="title" :href="htmlLink.href">{{ htmlLink.title }}</a>
                <div class="tags">
                    <div v-for="(t, i) in htmlLink.tags" :key="i">
                        [{{ t }}]
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Msgpool",

    data() {
        return {
            htmlLinkArray: [
                {
                    href: "/lab/cube riddle",
                    title: "原神方块类谜题解密器",
                    tags: ["js", "genshin"],
                },
                {
                    href: "/lab/cyberpunk",
                    title: "网络疯子模拟器",
                    tags: ["js", "cyberpunk", "labor"],
                },
                {
                    href: "/lab/artifact",
                    title: "原神圣遗物筛选(转载)",
                    tags: ["vue", "genshin"],
                },
            ],
        };
    },
    computed: {
        labLinkArray() {
            return this.htmlLinkArray.filter(
                (h) => h.tags.indexOf("labor") >= 0
            );
        },
    },
    props: ["labelSel"],
    mounted() {},

    methods: {},
};
</script>

<style scoped>
.row {
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    width: 400px;
    margin: 10px auto;
}
.index {
    width: 20px;
}
.title {
    width: 200px;
}
a {
    color: rgb(103, 134, 119);
}
.tags {
    width: 200px;
    display: flex;
    justify-content: flex-end;
    font-size: 10px;
}
</style>