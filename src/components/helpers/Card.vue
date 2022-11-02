<template>
  <div class="my-3 mx-3 col-xl-12 col-bg-12 col-md-12 col-sm-12 text-center">
   
        <img
          class="card-img-top rounded"
          :src="endingNote.pictures[0].img"
          alt="Card image cap"
        />
    
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    endingNote: {
      type: Object,
    },
    nightMode: {
      type: Boolean,
    },
  },
};
</script>

<style scoped>


.rounded{
  object-fit: cover;
    border-radius: 50%;
    height: 90%;
    width: 90%;
    margin-top: 10px;
    margin-bottom: 10px;
    border: 2px solid rgb(205, 205, 205);
  }

</style>
