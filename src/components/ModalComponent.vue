<template>
  <div class="modal">
    <button @click="close">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        class="icon icon-tabler icon-tabler-x"
        width="22"
        height="22"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="currentColor"
        fill="none"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <path stroke="none" d="M0 0h24v24H0z" fill="none" />
        <line x1="18" y1="6" x2="6" y2="18" />
        <line x1="6" y1="6" x2="18" y2="18" />
      </svg>
    </button>

    <div class="inner-modal" :style="{'width': width+'px' }">
      <div class="modal-image">
        <img
          :src="image.urls.regular"
          :style="{'width': width+'px', 'height': height + 'px' }"
          @click="close"
          :alt="image.alt_description"
        />
      </div>
      <div class="modal-text">
        <div class="name">{{image.user.name}}</div>

        <div class="location">{{image.user.location}}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    image: {
      type: Object,
    },
  },
  data() {
    return {
      height: "0px",
      width: "0px",
    };
  },
  methods: {
    close() {
      this.$emit("closeModal");
    },
    setSize(width, height) {
      if (window.innerHeight > window.innerWidth) {
        let factor = width / window.innerWidth;
        this.width = width / (factor + .5);
      } else {
        let factor = height / window.innerHeight;
        this.width = width / (factor + 2);
        this.height = height / (factor + 2);
      }
    },
  },
  created() {
    this.setSize(this.image.width, this.image.height);
  },
};
</script>

<style>
</style>