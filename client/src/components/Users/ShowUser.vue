<template>
    <div>
        <div>
            <h1>Get User Bt Id</h1>
            <p>User ID: {{ user.id }}</p>
            <p>ชื่อ-นามสกุล: {{ user.name }} - {{ user.lastname }}</p>
            <p>email: {{ user.email }}</p>
            <p>password: {{ user.password }}</p>
            <p>status: {{ user.status }}</p>
            <p>type: {{ user.type }}</p>
            <p><button v-on:click="navigateTo('/users/')">กลับ</button></p>

        </div>
    </div>
</template>
<script>
import UsersService from '@/services/UsersService';

export default {
        data () {
            return {
                user: null
            }
        },
        async created () {
            try {
                let userId = this.$route.params.userId
                this.user = (await UsersService.show(userId)).data
            }catch (error) {
                console.log (error)
            }
        },
        methods: {
            navigateTo (route) {
                this.$router.push(route)
            },
        }

    }
</script>
<style scoped>

</style>