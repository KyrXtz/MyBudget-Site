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
          >Get started now ...</span
        >
      </div>
      <hr
        width="50%"
        :class="{ pgray: !nightMode, 'bg-secondary': nightMode }"
      />

      <div class="row">
        <div
          class="col-xl-4 col-bg-4 col-md-6 col-sm-12"
          v-for="(endingNote, idx) in endingNotes"
          :key="endingNote.name"
        >
          <Card
            :style="{ 'transition-delay': (idx % 3) / 4.2 + 's' }"
            :endingNote="endingNote"
            @show="showModalFn"
            data-aos="fade-up"
            :nightMode="nightMode"
            data-aos-offset="100"
            data-aos-delay="10"
            data-aos-duration="500"
            data-aos-easing="ease-in-out"
            data-aos-mirror="true"
            data-aos-once="true"
          />
        </div>
      </div>

    </div>
  </div>
</template>

<script>
import Card from "./helpers/Card";
import info from "../../info";

export default {
  name: "EndingNotes",
  components: {
    Card
  },
  props: {
    nightMode: {
      type: Boolean,
    },
  },
  data() {
    return {
      all_info: info.endingNotes,
      endingNotes: [],
      showModal: false,
      showDesignModal: false,
      modal_info: {},
      design_modal_info: {},
      number: 3,
      showBtn: "show more",
      shower: 0,
      data: [
        '<div class="slide">Slide 1</div>',
        '<div class="slide">Slide 2</div>',
        '<div class="slide">Slide 3</div>',
      ],
    };
  },
  created() {
    for (var i = 0; i < this.number; i++) {
      this.endingNotes.push(this.all_info[i]);
    }
  },
  watch: {
    number() {
      this.endingNotes = [];
      for (var i = 0; i < this.number; i++) {
        this.endingNotes.push(this.all_info[i]);
      }
    },
  },
};
</script>

<style scoped>
.title {
  font-size: 30px;
  font-weight: 500;
}
</style>
