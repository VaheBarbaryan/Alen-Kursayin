<script setup>
import { ref } from "vue"

const props = defineProps(['authUser'])

const emit = defineEmits(['submit'])

const newPassword = ref('')
const ConfirmNewPassword = ref('')

const onSubmit = () => {
   if(ConfirmNewPassword.value === '' || newPassword.value === '' || ConfirmNewPassword.value !== newPassword.value) {
        return false
   } else {
    emit('submit', newPassword)
   }
}

</script>

<template>
    <div class="new-password">
        <form class="new-password__wrapper">
            <label for="new_password">Նոր գաղտնաբառ</label>
            <input v-model="newPassword" type="password" id="new_password" placeholder="Նոր գաղտնաբառ">
            <label for="confirm_new_password">Նոր գաղտնաբառի հաստատում</label>
            <input v-model="ConfirmNewPassword" type="password" id="confirm_new_password" placeholder="Նոր գաղտնաբառի հաստատում">
            <button @click="onSubmit" type="button" class="submit">Հաստատել</button>
        </form>
    </div>
</template>

<style lang="scss" scoped>
.new-password {
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