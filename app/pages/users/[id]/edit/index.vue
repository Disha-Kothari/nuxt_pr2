<script setup>
let user=reactive({
    city:'',
    street_nm:'',
    street_address:'',
    zip_code:'',
    state:'',
    country:''
})
const route=useRoute();
const id=route.params.id;
getUser(id);

async function getUser(id)
{
  const {data,pending, error} = await useAsyncData(
  'Fetch User',
  () => $fetch(`/users/${id}`, {    
    baseURL: 'http://localhost:3000',
    }),
    {pick:['address']},
    )
    console.log(data.value)
    // {user.city,user.street_nm,user.street_address,user.zip_code,user.state,user.country}=data.value.address
    user.city=data.value.address.city
    user.street_nm=data.value.address.street_name
    user.street_address=data.value.address.street_address
    user.zip_code=data.value.address.zip_code
    user.state=data.value.address.state
    user.country=data.value.address.country

    // console.log(data.value.address)   
    // console.log(user)   
    // // console.log(user)
}

async function editUser(){
   const { error} = await useAsyncData(
  'Edit User',
  () => $fetch(`/users/${id}`, { 
    baseURL: 'http://localhost:3000',
    method:'PUT',
    body:JSON.stringify(user)
    })
  );
  console.log(error)
}
</script>
<template>
    <h1>Edit User</h1>
    <FormUser v-bind="{user:user}" @submit.prevent="editUser" ></FormUser>
</template>