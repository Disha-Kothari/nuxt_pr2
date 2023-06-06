<script setup>
const config = useRuntimeConfig();
const perpage = ref(8);
const page_no = ref(12);
const route = useRoute()
const titleId = route.params.id

const { data: titles_credits } = await useAsyncData(
    "title & Credits",
    () =>
        $fetch(`${config.apiBase}/titles/${titleId}`, {
            baseURL: `${config.base_url}`,
        })
);
const title = titles_credits.value.data.title;
const credits = titles_credits.value.data.credits;
</script>

<template>
    <div class="container section">
        <div class="row">
            <h2 class="text-center">Movie/Show Details</h2>
        </div>

        <div v-if="!title" class="row mx-1">
            <div class="col-12">
                <h3 class="text-center">No Data Found</h3>
            </div>
        </div>
        <div v-else class="row">
            <div class="card h-100">
                <div>
                    <img src="../../assets/img/img4.jpeg" class="card-img-top img mx-auto" alt="..." />
                </div>
                <div class="card-body">
                    <h4 class="card-header card-title text-center text-truncate">
                        <strong class="font-weight-extra-bold">{{ title.title }}({{ title.type }})</strong>
                    </h4>
                    <p class="card-text movie-desc">Description: {{ title.desc }}</p>
                    <p class="card-text">Release-Year:{{ title.release_year }} </p>
                    <p class="card-text">Age-Certification:{{ title.age_certification }} </p>
                    <p class="card-text">Runtime:{{ title.runtime }}</p>
                    <p class="card-text">Genres:{{ title.genres }}</p>
                    <p class="card-text">production_countries:{{ title.production_countries }}</p>
                    <h3><strong class="font-weight-extra-bold">Credits</strong></h3>
                    <div class="accordion" id="accordionCredit">
                        <div v-for="credit in credits" :key="credit.title_id" class="accordion-item">
                            <!-- <div class="accordion-item"> -->
                            <div class="border-radius mb-1 border-0">
                                <div class="py-2 bg-color-quaternary">
                                    <h2 class="accordion-header">
                                        <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse"
                                            :data-bs-target="`#collapse${credit.person_id}`" aria-expanded="false"
                                            :aria-controls="`collapse${credit.person_id}`">
                                            {{ credit.name }}({{ credit.person_id }})
                                        </button>
                                    </h2>
                                </div>
                                <div :id="`collapse${credit.person_id}`" class="accordion-collapse collapse"
                                    data-bs-parent="#accordionCredit">
                                    <div class="accordion-body">
                                        <p>Character: {{ credit.character }}</p>
                                        <p>Role: {{ credit.role }}</p>
                                    </div>
                                </div>
                            </div>
                            <!-- </div> -->
                        </div>
                    </div>

                </div>
            </div>

        </div>


    </div>
</template>
<style scoped>
.img {
    object-fit: cover;
    height: 250px;
}

/* .accordion .card-header {
    padding: 0;
    border-radius: 0.25rem;
    border-bottom: 0;
    margin: -1px;
} */
.mb-1,
.my-1 {
    margin-bottom: 0.25rem !important;
}

.bg-color-quaternary,
.bg-quaternary {
    background-color: #eef0f4 !important;
}

.border-radius {
    border-radius: 4px !important;
}</style>