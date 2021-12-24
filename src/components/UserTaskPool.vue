<template>
    <div>
        <UserTaskUnit
            v-for="taskObj in taskArr"
            :key="taskObj.id"
            :taskObj="taskObj"
            :del_task="del_task"
            :do_task="do_task"
        ></UserTaskUnit>
    </div>
</template>

<script>
import UserTaskUnit from './UserTaskUnit';

export default {
    name: 'UserTaskPool',
    props:['taskArr','del_task','do_task'],
    components: { UserTaskUnit },
};
</script>

<style scoped>

</style>