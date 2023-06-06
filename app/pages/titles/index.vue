<script setup>

const config = useRuntimeConfig();
const perpage = ref(8);
const page_no = ref(12);

const modalVisible= ref(false)
const id=ref(1)


const { data: titles,refresh } = await useAsyncData(
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

function showModal(val){
  modalVisible.value = true;
  id.value=val
}

async function deleteData(){
    const {deletedData,error}=await useAsyncData(
  'delete title',
  () => $fetch(`${config.apiBase}/titles/${id.value}`  , { 
    method:'DELETE',
    baseURL: `${config.base_url}`,
    })
);
if(error!=null){
    modalVisible.value=false;
    refresh();
}
}
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
          <div class="box-content p-2">
            <img src="../../assets/img/img4.jpeg" class="card-img-top img mx-auto" alt="..." />
          </div>
          <div class="card-body">
            <h4 class="card-header card-title text-center text-truncate">
              <strong class="font-weight-extra-bold">{{ title.title }}({{ title.id }})</strong>
            </h4>
            <p class="card-text movie-desc">{{ title.desc }}</p>
            <div class=" text-center">
              <NuxtLink :to='"/titles/"+title.id' class="btn btn-secondary btn-sm me-1 opacity-75 btnCustom">Details</NuxtLink>
              <NuxtLink to="#" class="btn btn-success btn-sm me-1 opacity-75 btnCustom">Edit</NuxtLink>
              <button @click="showModal(title.id)" class="btn btn-danger btn-sm me-1 opacity-75 btnCustom">Delete</button>
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
    <ModalDialog :show="modalVisible" :id="id" @close="()=>modalVisible=false">
    <template #body>Are You Sure To Delete this Record</template>
    <template #footer>
      <button class="btn btn-danger" @click="deleteData()">Yes</button>
    </template>
    </ModalDialog>

    <nav aria-label="Page navigation" class="col">
          <ul class="pagination justify-content-center">
            <li class="page-item">
              <NuxtLink
                class="page-link customLinkColor"
                href="#"
                aria-label="Previous"
                :disabled="page_no > 1"
                @click="previous()"
              >
                <span aria-hidden="true">&laquo;</span>
              </NuxtLink>
            </li>
            <li class="page-item">
              <span class="page-link customLinkColor" href="#">{{
                page_no
              }}</span>
            </li>
            <li class="page-item">
              <NuxtLink
                class="page-link customLinkColor"
                href="#"
                aria-label="Next"
                :disabled="titles.length < perpage"
                @click="next()"
              >
                <span aria-hidden="true">&raquo;</span>
              </NuxtLink>
            </li>
          </ul>
        </nav>
  </div>
</template>
<style scoped>
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
.featured-box {
  border-top-width: 4px;
}

.featured-box-primary  {
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
</style>
