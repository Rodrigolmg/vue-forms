<template>
    <div class="name-surname">
        <input class="user-fullname" type="text" placeholder="Nome" ref="userName" :value="value.name" 
            @input="getFullName()">
        <input class="user-fullname" type="text" placeholder="Sobrenome" ref="userSurname" 
            :value="value.surname" @input="getFullName()">
    </div>
</template>

<script>

export default {
    props: ['value'],
    methods:{
        getFullName(){
            this.$emit('input', {
                name: this.$refs.userName.value,
                surname: this.$refs.userSurname.value
            })
        }
    }
}
</script>

<style scoped>

    .name-surname{
        width: 98.4%;
    }

    .user-fullname {
        margin-bottom: 5px;
        border-radius: 6px;
        border: 1px solid #8080804D;
        outline: none;
        height: 2.3rem;
        width: 100%;
        display: block;
        font-size: 1em;
        padding-left: 10px;
    }

    .user-fullname:focus {
        border: 1px solid #0000004D;
    } 
</style>


