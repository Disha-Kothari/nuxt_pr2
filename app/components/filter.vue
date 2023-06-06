<script setup>
// const props = defineProps(['showType', 'searchMovieName'])
const emit =defineEmits(['searchTitle'])
// const newEmittedData="emited_data"
// const emit = defineEmits(['response'])
// emit('response', 'hello from child')
// function performemit(){
//     emit("emitted-data",newEmittedData)
// }
const title=ref('')
function filterType(){
}

</script>
<template>
    <div style="display: inline-block; width: 400px;">
        <!-- <div class="dropdown">
            <button class="btn btn-secondary dropdown-toggle" type="button" data-bs-toggle="dropdown" aria-expanded="false">
                Filter Show Type
            </button>
            <ul class="dropdown-menu">
                <li class="dropdown-item" >All</li>
                <li class="dropdown-item">Movie</li>
                <li class="dropdown-item">Show</li>
            </ul>
        </div> -->
        <!-- <form class="d-flex" role="search" > -->
            <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search"  v-model="title" >
            <button class="btn btn-outline-success"  @click="$emit('searchTitle',title)">Search</button>
        <!-- </form> -->

        <!-- <input type="text" placeholder="Custom text Input"
     @change="$emit('customChange',$event.target.value)">
     <button @click="$emit('customChange',newEmittedData)">Emit Data</button>  -->

     <!-- <emits @customChange="logChange"  @newEmitedData="emitted-data"  @response="(msg)=>childMsg=msg"/> -->
    </div>
</template>
