<script setup>
const config = useRuntimeConfig();
const movieTitle=reactive({
    title:'',
    type:'',
    desc:'',
    release_year:'',
    age_certification :'',
    runtime:'',
    genres:'',
    production_countries:''
})
async function insertTitle(){
    const { error} = await useAsyncData(
  'create Title',
  () => $fetch(`${config.apiBase}/titles`, { 
    baseURL: `${config.base_url}`,
    method:'POST',
    body:JSON.stringify(movieTitle)
    })
  );
  if(error.value!=null){
        alert("Movie added Sucessfully")
        movieTitle.title=""
        movieTitle.type=""
        movieTitle.desc=""
        movieTitle.release_year=""
        movieTitle.age_certification=""
        movieTitle.runtime=""
        movieTitle.genres=""    
        movieTitle.production_countries=""
  }
}
</script>
<template>
    <FormTitle @submit.prevent="insertTitle" v-bind="{movieTitle:movieTitle}" :isEdit="false"></FormTitle>
</template>