<template>
  <div class="card my-2 col-2">
    <a href="#" class="text-decoration-none">
      <img :src="image" class="card-img-top" />
    </a>
    <div class="card-body">
      <h5 class="text-center">
        {{ title }}
      </h5>
    </div>
    <div class="card-footer">
      <div class="card-text text-center">{{ rank }}</div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["title", "id", "image", "rank"],
};
</script>
