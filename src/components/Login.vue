<script setup>
import { ref } from "vue"

const props = defineProps(['authUser'])

const emit = defineEmits(['submit'])

const email = ref('')
const password = ref('')

const onSubmit = () => {
    if(props.authUser.email !== email.value || props.authUser.password !== password.value) {
        emit('submit', false)
    } else {
        emit('submit', true)
    }
}

</script>

<template>
  <form class="login">
    <div class="login__wrapper">
        <label for="email">Էլ․ փոստ</label>
        <input v-model="email" type="email" id="email" placeholder="Էլ․ փոստ">
        <label for="password">Գաղտնաբառ</label>
        <input v-model="password" type="password" id="password" placeholder="Գաղտնաբառ">
        <button @click="onSubmit" type="button" class="submit">Հաստատել</button>
    </div>
  </form>
</template>

<style lang="scss" scoped>
.login {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
    border-radius: 20px;
    &__wrapper {
        box-shadow: 0 10px 15px rgba(0,0,0, .1);
        padding:30px;
        width:400px;
        height:auto;
        overflow:hidden;
        background:#242424;
        border-radius:20px;
    }
    
    label {
        font-size:14px;
        color:gray;
        cursor:pointer;
    }

    label,
    input {
        float:left;
        clear:both;
    }

    input {
        margin:15px 0;
        padding:15px 10px;
        width:100%;
        outline:none;
        border:1px solid #bbb;
        border-radius:20px;
        display:inline-block;
        -webkit-box-sizing:border-box;
        -moz-box-sizing:border-box;
        box-sizing:border-box;
        -webkit-transition:0.2s ease all;
        -moz-transition:0.2s ease all;
        -ms-transition:0.2s ease all;
        -o-transition:0.2s ease all;
        transition:0.2s ease all;
        &:focus {
            border-color:cornflowerblue;
        }
    }
}

</style>