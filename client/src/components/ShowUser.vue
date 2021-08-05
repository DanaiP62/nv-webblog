<template>
    <div>
        <h1>Show User</h1>
        <p>ID : {{ user.id }} </p>
        <p>ชื่อ - นามสกุล {{user.name}} - {{user.lastname}}</p>
        <p>Email : {{user.email}} </p>
        <p>Password : {{user.password}}</p>
    </div>
</template>
<script>
import UserService from '@/service/UserService'
export default {
    data() {
        return {
            user: null,
        };
    },
    async created() {
        try {
            let userId = this.$route.params.userId;
            this.user = (await UserService.show(userId)).data
        } catch (error) {
            console.log(error);
        }
    },
};
</script>
<style scoped>
</style>