<script setup>
const props = defineProps({
    movieTitle: {
        type: Object,
        default: () => { }
    },
    isEdit:false
})
</script>
<template>
    <div class="container mt-5">
        <div class="card">
            <div class="card-header">
                <h4 class="text-center" v-if="!isEdit">Add Movie</h4>
                <h4 class="text-center" v-else>Edit Movie</h4>
            </div>
            <div class="card-body">
                <form>
                <div class="row mb-3">
                    <div class="col-md-4">
                        <label for="name" class="form-label">Name</label>
                        <input type="text" class="form-control text-capitalize" id="name" v-model="movieTitle.title"
                            required>
                    </div>
                    <div class="col-md-4">
                        <label for="type" class="form-label">Type</label>
                        <select id="type" class="form-select" v-model="movieTitle.type" required>
                            <option value="">Select</option>
                            <option value="MOVIE">Movie</option>
                            <option value="SHOWS">Shows</option>
                        </select>
                    </div>
                </div>
                <div class="row mb-3">
                    <div class="col-12">
                        <label for="desc" class="form-label">Description</label>
                        <input type="text" class="form-control text-capitalize" id="desc" placeholder="Movie Description"
                            v-model="movieTitle.desc">
                    </div>
                </div>
                <div class="row mb-3">
                    <div class="col-md-4">
                        <label for="releaseYear" class="form-label">Release Year</label>
                        <input type="number" class="form-control" id="releaseYear" v-model="movieTitle.release_year"
                            required>
                    </div>
                    <div class="col-md-4">
                        <label for="ageCertification" class="form-label">Age Certification</label>
                        <input type="text" class="form-control text-uppercase" id="ageCertification"
                            v-model="movieTitle.age_certification">
                    </div>
                    <div class="col-md-4">
                    <label for="runtime" class="form-label">Runtime</label>
                    <input type="number" class="form-control" id="runtime" v-model="movieTitle.runtime">
                </div>
            </div>
            
            <div class="row mb-3">
                <div class="col-md-6">
                <label for="productionCountries" class="form-label">Production Countries</label>
                <input type="text" class="form-control text-uppercase" id="productionCountries"
                    v-model="movieTitle.production_countries">
            </div>
            <div class="col-md-6">
                <label for="genres" class="form-label">Genres</label>
                <input type="text" class="form-control" id="genres" v-model="movieTitle.genres">
            </div>
            </div>
            <div class="row mb-3">
                <div class="col-12">
                <button type="submit" class="btn btn-secondary">Save</button>
            </div>
            </div>
        </form>
        </div>
    </div>
    </div>
</template>
