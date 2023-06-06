<template>
    <div id="carouselExampleIndicators" class="carousel slide mx-auto col-10 align-items-center py-5">
  <div class="carousel-indicators">
    <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="0" class="active" aria-current="true" aria-label="Slide 1"></button>
    <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="1" aria-label="Slide 2"></button>
    <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="2" aria-label="Slide 3"></button>
  </div>
  <div class="carousel-inner">
    <div class="carousel-item active">
      <img src="../assets/img/img5.jpg" class="d-block w-100 img" alt="...">
    </div>
    <div class="carousel-item">
      <img src="../assets/img/Img2.jpg" class="d-block w-100 img" alt="...">
    </div>
    <div class="carousel-item">
      <img src="../assets/img/Img3.jpg" class="d-block w-100 img" alt="...">
    </div>
  </div>
  <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide="prev">
    <span class="carousel-control-prev-icon" aria-hidden="true"></span>
    <span class="visually-hidden">Previous</span>
  </button>
  <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide="next">
    <span class="carousel-control-next-icon" aria-hidden="true"></span>
    <span class="visually-hidden">Next</span>
  </button>
</div>
</template>
<style scoped>
#carouselExampleIndicators .carousel-item img {
  object-fit: cover;
  object-position: top-center; 
  height: 75vh;
  overflow: hidden;
 }
</style>