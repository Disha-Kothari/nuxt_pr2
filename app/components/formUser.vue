<script setup>

const props=defineProps({
    user:{
        type:Object,
        default:()=>{}
    }
}) 

</script>
<template>
        <form>
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
            
        </form>
</template>