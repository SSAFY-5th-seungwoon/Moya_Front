<template>
  <!-- <img class="swiper-slide" :src="imgSrc"/> -->
  <div
    :class="[imageClass, imageState]" 
    :style="computedStyle" 
    :data-width="imageWidth" 
    :data-height="imageHeight" 
    :data-state="imageState"
  >
    <h2>{{ movie.title }}</h2>
    <div class="size">
      <star-rating :rating="parseFloat(movie.vote_average) / 2" :read-only="true" :increment="0.01"/>
      <!-- <span>7</span>
      <span>8</span>
      <span>9</span>
      <span>10</span> -->
    </div>
    <div class="color">
      <h3>{{ movie.release_date }}</h3>
    </div>
    <router-link :to="{name : 'MovieDetail', params : {movie_pk : movie.id }}">Detail</router-link>
  </div>
</template>

<script>
import StarRating from 'vue-star-rating'
import lazyMixin from '@/mixins/lazyMixin'


export default {
  name : 'MoviesSliderItem',
  components : {
    StarRating,
  },
  mixins : [lazyMixin],
  data : function(){
    return {
      imageClass : "swiper-slide contentBx"
    }
  }, 
  props : {
    movie : {
      type : Object
    }
  },
  computed : {
    backgroundImage : function(){
      return "https://image.tmdb.org/t/p/w500"+this.movie.poster_path
    },

  }
}
</script>

<style>

</style>