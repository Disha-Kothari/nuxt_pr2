<script setup>
const props=defineProps(['page_no','perPage','itemCount'])

</script>
<template>
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
                :disabled="itemCount < perPage"
                @click="next()"
              >
                <span aria-hidden="true">&raquo;</span>
              </NuxtLink>
            </li>
          </ul>
        </nav>
</template>
