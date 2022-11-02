<template>
  <div class="bg-secondary">
    <div class="container py-3">
      <div class="row pt-1 align-items-center">
        <div
          class="col-xl-6 col-bg-6 col-md-6 col-sm-12 pbelow"
          style="color: white;"
        >
          <span>© 2022 Copyright: Kyr Xtz</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: "Footer"
};
</script>

<style scoped>
span {
  font-weight: 500;
}

@media screen and (max-width: 580px) {
  .pbelow {
    padding-bottom: 20px;
    text-align: center;
  }
}
</style>
