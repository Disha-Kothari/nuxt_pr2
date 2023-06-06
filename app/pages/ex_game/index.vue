<script setup>


const selectedUser=ref(1)
let bot=ref(1)
bot.value = Math.floor(Math.random()*3)+1
let result=""
function Result(){
    if (selectedUser.value==bot.value){
        result="tie"
    }
    else if ((selectedUser.value===1 && bot.value!=3) || (selectedUser.value===2 && bot.value!=1) || (selectedUser.value===3 && bot.value!=2))
    {
        result="User Won"
    }
    else{
        result="bot won"
    }
}
</script>
<template>
    <h1>Select User</h1>
    <select id="selectID"></select>
</template>
