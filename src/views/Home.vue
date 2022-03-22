<template>
  <div class="home_wrap">
    <h3 class="announcementTitle">最新公告</h3>
    <div class="announcement"></div>
    <div class="ratingBarFrame">
      <div class="ratingBar">
        <p>評分</p>
        <star-rating
          :increment="1"
          :max-rating="5"
          inactive-color="#E5E5E5"
          active-color="#F6DC66"
          :star-size="130"
          @update:rating="setRating"
        >
        </star-rating>
        <div class="QRCode_picture">
          <img src="@/assets/QRCode.svg" alt="" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import StarRating from "vue-star-rating";
import { ref } from "vue";
import axios from "axios";

export default {
  components: {
    StarRating,
  },
  setup() {
    const rating = ref(0);

    function setRating(parmValue) {
      rating.value = parmValue;
      axios
        .post("http://localhost:8000/rating", {
          rating: rating.value,
        })
        .then((res) => {
          console.log(res);
        })
        .catch((err) => {
          console.log(err);
        });
      console.log(rating.value);
    }
    return {
      rating,
      setRating,
    };
  },
  //   mounted(){
  //   axios.get('http://localhost:8000').then(data) => {
  //     rating.value = ref.value
  //   }
  // }
};
</script>

<style type="text/css" src="@/assets/style.css"></style>
