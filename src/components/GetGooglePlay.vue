<template>
  <div
    class="py-4 p-st"
    :class="{
      'bg-light': !nightMode,
      'bg-dark2': nightMode,
      'text-light': nightMode,
    }"
  >
    <div class="container">
      <div
        class="text-center"
        data-aos="fade"
        data-aos-once="true"
        data-aos-duration="1000"
      >
        <span
          class="title text-center"
          :class="{ pgray: !nightMode, 'text-light': nightMode }"
          >.. it's free!</span
        >
      </div>
      <hr
        width="50%"
        :class="{ pgray: !nightMode, 'bg-secondary': nightMode }"
      />
      <div class="center-items">
          <div cli class="col-xl-6 col-bg-6 col-md-6 col-sm-12 text-center">
            <button class="btn"
             @click="open('googleplay')">
              <img :src="getPhoto" />
            </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import info from "../../info";

export default {
  name: "GetGooglePlay",
  props: {
    nightMode: {
      type: Boolean,
    },
  },
  data() {
    return {
      getPhoto:info.getPhoto,
      googleplay: info.links.googleplay,

    };
  },methods: {
    open(link) {
      switch (link) {
        case "googleplay":
          window.open(this.googleplay, "_blank");
          break;
      }
    },
  },
};
</script>

<style scoped>
img {
  max-width: 300px;
  max-height: 800px;
}
.btn{
  background-color: transparent;
}
.center-items{
  display: flex;
  align-items: center;
  justify-content: center;
}
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
  font-weight: 400;
}

.title3 {
  font-size: 16px;
  font-weight: 400;
}

.pinput {
  font-size: 18px;
  outline: none;
  border: none;
  border-radius: 7px;
  padding: 10px;
  width: 50%;
  transition: all 1s;
  background-color: #b3b3cc;
}



.pgray-dark {
  background-color: #3c4148 !important;
}

@media screen and (max-width: 1000px) {
  .pinput {
    width: 90%;
  }
  .pinput {
    width: 90%;
  }


}
</style>
