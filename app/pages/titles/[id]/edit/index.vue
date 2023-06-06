<script setup>

const config = useRuntimeConfig();
const route = useRoute()
const titleId = route.params.id
let orgData={}
let movieTitle = reactive({
  title: '',
  type: '',
  desc: '',
  release_year: '',
  age_certification: '',
  runtime: '',
  genres: '',
  production_countries: ''
})
getTitle(titleId);

async function getTitle(titleId) {
  const { data: title_credits, pending, error } = await useAsyncData(
    'Fetch Title',
    () => $fetch(`${config.apiBase}/titles/${titleId}`, {
      baseURL: `${config.base_url}`,
    }),
  )
  // {pick:['title']},
  // console.log(data.value.data.title)
  // console.log(error)
  // console.log(title_credits.value.data.title)
  movieTitle.title = title_credits.value.data.title.title
  movieTitle.type = title_credits.value.data.title.type
  movieTitle.desc = title_credits.value.data.title.desc
  movieTitle.release_year = title_credits.value.data.title.release_year
  movieTitle.age_certification = title_credits.value.data.title.age_certification
  movieTitle.runtime = title_credits.value.data.title.runtime
  movieTitle.genres = title_credits.value.data.title.genres
  movieTitle.production_countries = title_credits.value.data.title.production_countries
  // console.log(movieTitle);
orgData=Object.assign(orgData, movieTitle);
// console.log("Orgdata copy");
// console.log(orgData)
}
async function editTitle() {
      const updatedTitle = {}
      if (movieTitle.title != orgData.title) {
        updatedTitle.title = movieTitle.title
      }
      if (movieTitle.type != orgData.type) {
        updatedTitle.type = movieTitle.type
      }
      if (movieTitle.desc != orgData.desc) {
        updatedTitle.desc = movieTitle.desc
      }
      if (movieTitle.release_year != orgData.release_year) {
        updatedTitle.release_year = movieTitle.release_year
      }
      if (movieTitle.release_year != orgData.release_year) {
        updatedTitle.release_year = movieTitle.release_year
      }
      if (movieTitle.age_certification != orgData.age_certification) {
        updatedTitle.age_certification = movieTitle.age_certification
      }
      if (movieTitle.runtime != orgData.runtime) {
        updatedTitle.runtime = movieTitle.runtime
      }
      if (movieTitle.genres != orgData.genres) {
        updatedTitle.genres = movieTitle.genres
      }
      if (movieTitle.production_countries != orgData.production_countries) {
        updatedTitle.production_countries = movieTitle.production_countries
      }
  
  if (Object.keys(updatedTitle).length!=0){
    const { error } = await useAsyncData(
      'Edit Title',
      () => $fetch(`${config.apiBase}/titles/${titleId}`, {
        baseURL: `${config.base_url}`,
        method: 'PATCH',
        body: JSON.stringify(orgData)
      })
    );
    if (error.value != null) {
      alert("Movie Edited Sucessfully")
    }

    for(const key in updatedTitle){
        orgData[key]=updatedTitle[key]
    }
}
}
</script>
<template>
  <FormTitle @submit.prevent="editTitle" v-bind="{ movieTitle: movieTitle }" :isEdit="true"></FormTitle>
</template>
