<template>
    <div>
        <Top ref="top" :add_task="add_task"></Top>
        <UserTaskPool
            :taskArr="taskArr"
            :del_task="del_task"
            :do_task="do_task"
        ></UserTaskPool>
        <Footer
            :taskArr="taskArr"
            :del_all_done_task="del_all_done_task"
            :set_all_task="set_all_task"
        ></Footer>
    </div>
</template>

<script>
import Footer from "./components/Footer";
import Top from "./components/Top";
import UserTaskPool from "./components/UserTaskPool";

export default {
    name: "App",

    data() {
        return {
            taskArr: JSON.parse(localStorage.getItem("taskArr")) || [],
        };
    },
    components: { Footer, Top, UserTaskPool },
    methods: {
        add_task(taskObj) {
            this.taskArr.unshift(taskObj);
        },
        del_task(taskID) {
            this.taskArr = this.taskArr.filter(
                (taskObj) => taskObj.id != taskID
            );
        },
        del_all_done_task() {
            this.taskArr = this.taskArr.filter((taskObj) => !taskObj.done);
        },
        do_task(taskID) {
            this.taskArr.forEach((taskObj) => {
                if (taskObj.id == taskID) taskObj.done = !taskObj.done;
            });
        },
        set_all_task(done) {
            this.taskArr.forEach((taskObj) => {
                taskObj.done = done;
            });
        },
    },
    mounted() {
        var e = this.$refs["top"];
        e.focus_input();
    },
    watch: {
        taskArr: {
            deep: true,
            handler(value) {
                localStorage.setItem("taskArr", JSON.stringify(value));
            },
        },
    },
};
</script>