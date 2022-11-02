<template>
  <div :class="{ 'bg-white': !nightMode, 'bg-dark': nightMode }" class="p-st">
    <div class="container py-4">
      <div
        class="text-center"
        data-aos="fade"
        data-aos-once="true"
        data-aos-duration="1000"
      >
        <span
          class="title text-center"
          :class="{ pgray: !nightMode, 'text-light': nightMode }"
          >But wait, there's more!</span
        >
      </div>
      <hr
        width="50%"
        :class="{ pgray: !nightMode, 'bg-secondary': nightMode }"
      />
      <br />
      <div class="row">
        <div
          class="col-xl-4 col-bg-4 col-md-4 col-sm-12 text-center pb-5 px-4"
          v-for="(feature, idx) in features" 
          :key="feature.title"
          data-aos="fade-up"
          data-aos-offset="10"
          data-aos-delay="30"
          :style="{ 'transition-delay': idx / 4.2 + 's' }"
          data-aos-duration="500"
          data-aos-easing="ease-in-out"
          data-aos-mirror="true"
          data-aos-once="true"
        >
        <div v-if="feature.title!=''">
          <div class="bg-div"><i :class="feature.icon"></i></div>
          <div class="title2 pt-2">{{ feature.title }}</div>
          <hr 
            width="50%"
            :class="{ pgray: !nightMode, 'bg-secondary': nightMode }"
          />
          <span class="title3">{{ feature.info.join(", ") }}</span>
        </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import info from "../../info";

export default {
  name: "Features",
  props: {
    nightMode: {
      type: Boolean,
    },
  },
  data() {
    return {
      features: info.features,
    };
  },
};
</script>

<style scoped>
.title {
  font-size: 30px;
  font-weight: 500;
}
.title1 {
  font-size: 24px;
  font-weight: 400;
}

.title2 {
  font-size: 20px;
  font-weight: 500;
}

.title3 {
  font-size: 16px;
  font-weight: 400;
}

.fa {
  color: #8585ad;
  font-size: 40px;
  transition: all 0.5s;
}

.fas {
  color: #8585ad;
  font-size: 40px;
  /* font-weight: bold; */
  transition: all 0.5s;
}
</style>
