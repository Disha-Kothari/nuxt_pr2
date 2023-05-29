<script setup>
const user=reactive({
    city:'',
    street_nm:'',
    street_address:'',
    zip_code:'',
    state:'',
    country:''
})

async function insertUser(){
    console.log(user)
    const { error} = await useAsyncData(
  'create User',
  () => $fetch(`/users`, { 
    baseURL: 'http://localhost:3000',
    method:'POST',
    body:JSON.stringify(user)
    })
  );
  console.log(error)
}
</script>
<template>
    <h1>Create User</h1>
    <div>
        <!-- <form @submit.prevent="insertUser">
            <div >
            <label for="city">City</label>
            <input type="text" id="city" v-model="user.city">
        </div>

            <div>
            <label for="street_name">Street</label>
            <input type="text" id="street_name" v-model="user.street_nm">
        </div>

            <div>
            <label for="address">Address</label>
            <input type="text" id="address" v-model="user.street_address">
        </div>

            <div>
            <label for="zipcode">ZipCode</label>
            <input type="number" id="zipcode" v-model="user.zip_code">
        </div>
            
            <div>
            <label for="state">State</label>
            <input type="text" id="state" v-model="user.state">
        </div>

        <div>
            <label for="country">Country</label>
            <input type="text" id="country" v-model="user.country">
        </div>
            <button type="submit">Save</button>
        </form> -->
        <FormUser @submit.prevent="insertUser" v-bind="{user:user}" ></FormUser>
    </div>
    
</template>