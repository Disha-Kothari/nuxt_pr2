<template>
<NuxtLayout>
  <Craousel></Craousel>
</NuxtLayout>
</template>
<!-- <<script setup>
const config = useRuntimeConfig();
const perpage = ref(8);
const page_no = ref(12);

const { data: titles } = await useAsyncData(
  "titles",
  () =>
    $fetch(`${config.apiBase}/titles`, {
      baseURL: `${config.base_url}`,
      params: {
        perpage: perpage.value,
        page_no: page_no.value,
      },
    }),
  { watch: [page_no] }
);

const previous = () => {
  if (page_no.value != 1) {
    page_no.value = page_no.value - 1;
  }
};

const next = () => {
  page_no.value = page_no.value + 1;
};
</script>
<template>
  <div class="container section">
    <div class="row">
      <h2 class="text-center">List of Movies/Shows</h2>
    </div>
    <div v-if="!titles.data.title.length" class="row mx-1">
      <div class="col-12">
        <h3 class="text-center">No Data Found</h3>
      </div>
    </div>
    <div v-else class="row">
      <div v-for="title in titles.data.title" :key="title.id" class="col-12 col-md-6 col-lg-4 col-xl-3 my-2">
        <div class="card h-100 featured-box featured-box-primary featured-box-effect-1 hover-effect-1">
          <div>
            <img src="../../assets/img/img4.jpeg" class="card-img-top img mx-auto" alt="..." />
          </div>
          <div class="card-body">
            <h4 class="card-header card-title text-center text-truncate">
              <strong class="font-weight-extra-bold">{{ title.title }}({{ title.id }})</strong>
            </h4>
            <p class="card-text movie-desc">{{ title.desc }}</p>
            <div class=" text-center">
              <NuxtLink to="#" class="btn btn-secondary btn-sm me-1 opacity-75 btnCustom">Details</NuxtLink>
              <NuxtLink to="#" class="btn btn-success btn-sm me-1 opacity-75 btnCustom">Edit</NuxtLink>
              <NuxtLink to="#" class="btn btn-danger btn-sm me-1 opacity-75 btnCustom">Delete</NuxtLink>
            </div>
          </div>
        </div>
      </div>
      <div class="row justify-content-center">
        <button v-if="page_no > 1" class="col-2 btn" @click="previous()">
          Previous
        </button>
        <button v-if="(titles.length = perpage)" class="col-2 btn" @click="next()">
          Next
        </button>
      </div>
    </div>
  </div>
</template>
<style scoped>
.featured-box .box-content:not(.box-content-border-0) {
  border-top-width: 4px;
  border-top: 4px;
}

.featured-box-primary .box-content {
  border-top-color: #9f2229;
}

.hover-effect-1 {
  box-shadow: 10px 10px 74px -15px transparent;
  transition: ease transform 300ms, ease box-shadow 300ms;
}

.hover-effect-1:hover {
  box-shadow: 10px 10px 74px -15px rgba(0, 0, 0, 0.4);
  transform: translate3d(0, -8px, 0);
}

.featured-box {
  background: #fff;
  box-sizing: border-box;
  border-bottom: 1px solid #dfdfdf;
  border-left: 1px solid #ececec;
  border-radius: 8px;
  border-right: 1px solid #ececec;
  box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.05);
  position: relative;
  text-align: center;
  z-index: 1;
}

.featured-box-primary .box-content {
  border-top-color: #9f2229;
}

.featured-box .box-content {
  border-top: 1px solid rgba(0, 0, 0, 0.06);
  border-top-width: 4px;
  position: relative;
}

.featured-box-primary h4 {
  color: #9f2229;
}

.text-color-dark .text-dark {
  color: #212529 !important;
}

.featured-box h4 {
  font-size: 1.3em;
  font-weight: 400;
  letter-spacing: -0.7px;
}

.font-weight-normal {
  font-weight: 400 !important;
}

.text-dark {
  color: #212529 !important;
}

.text-5 {
  font-size: 1.5em !important;
}

.text-dark {
  color: #343a40 !important;
}

.font-weight-normal {
  font-weight: 400 !important;
}

.movie-desc {
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
  min-height: 70px;
}

.img {
  object-fit: cover;
  height: 250px;
}

.btnCustom {
  width: 75px;
}
</style> -->
