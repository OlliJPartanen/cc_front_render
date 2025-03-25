<script setup>

import UserReview from './components/UserReview.vue';
</script>

<template>
  <header>
    <div  class="main_header_style col-m-12 col-t-12 col-12">
      <h1>Heavy metal sentiment analyzer</h1>
      <img alt="mainImage" src="/mainImage.jpg" />
    </div>
  </header>
    
  <div class="col-m-12 col-t-12 col-12 review_style" >
    <UserReview></UserReview>
  </div>



</template>

<style scoped>

*{
    box-sizing: border-box;
    font-family: 'Times New Roman', Times, serif
}

/* mobile-screen */
@media only screen and (width < 750px) {
    .col-m-0 {width: 0%; display: none;}
    .col-m-1 {width: 8.33%;}
    .col-m-2 {width: 16.66%;}
    .col-m-3 {width: 25%;}
    .col-m-4 {width: 33.33%;}
    .col-m-5 {width: 41.66%;}
    .col-m-6 {width: 50%;}
    .col-m-7 {width: 58.33%;}
    .col-m-8 {width: 66.66%;}
    .col-m-9 {width: 75%;}
    .col-m-10 {width: 83.33%;}
    .col-m-11 {width: 91.66%;}
    .col-m-12 {width: 100%;}

}

/*tablet-screen */
@media only screen and (min-width: 750px) {
    .col-t-0 {width: 0%;}
    .col-t-1 {width: 8.33%;}
    .col-t-2 {width: 16.66%;}
    .col-t-3 {width: 25%;}
    .col-t-4 {width: 33.33%;}
    .col-t-5 {width: 41.66%;}
    .col-t-6 {width: 50%;}
    .col-t-7 {width: 58.33%;}
    .col-t-8 {width: 66.66%;}
    .col-t-9 {width: 75%;}
    .col-t-10 {width: 83.33%;}
    .col-t-11 {width: 91.66%;}
    .col-t-12 {width: 100%;}

}

/* PC-screen */
@media only screen and (min-width: 1450px) {
    .col-0 {width: 0%;}
    .col-1 {width: 8.33%;}
    .col-2 {width: 16.66%;}
    .col-3 {width: 25%;}
    .col-4 {width: 33.33%;}
    .col-5 {width: 41.66%;}
    .col-6 {width: 50%;}
    .col-7 {width: 58.33%;}
    .col-8 {width: 66.66%;}
    .col-9 {width: 75%;}
    .col-10 {width: 83.33%;}
    .col-11 {width: 91.66%;}
    .col-12 {width: 100%;}

}

img {
    max-width: 50%;
    max-height: 50%;
}

.main_header_style 
{
  padding: auto;
  margin-block: 15px;
  background-color: rgb(0, 0, 0);
  text-align: center;
}

.review_style
{
  padding: auto;
  margin-block: 15px;
  background-color: rgb(31, 10, 11);
  text-align: center;
}

</style>
