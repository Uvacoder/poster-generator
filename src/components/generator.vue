<template>
  <div class="poster-creator">
    <form @submit.prevent="onSubmit()">
      <div class="form-item">
        <label for="subtitle">Sub Title</label>
        <input
          type="text"
          id="subtitle"
          placeholder="subtitle here"
          v-model="subtitle"
        />
      </div>
      <div class="form-item">
        <label for="maintitle">Main Title</label>
        <input
          type="text"
          id="maintitle"
          placeholder="main title here"
          v-model="maintitle"
        />
      </div>
      <div class="form-item">
        <label for="dudes">
          <input type="checkbox" id="dudes" v-model="dudes" /> Show dudes
        </label>
      </div>
      <div class="form-item">
        <button type="submit">generate image</button>
      </div>
    </form>
    <div class="poster-output" v-if="formDataForImage.maintitle !== ''">
      <generated-img
        :subtitle="formDataForImage.subtitle"
        :maintitle="formDataForImage.maintitle"
        :dudes="formDataForImage.dudes"
      />
    </div>
  </div>
</template>

<script>
import generatedImg from "./generated-img";

export default {
  name: "HelloWorld",
  components: {
    generatedImg,
  },
  data() {
    return {
      subtitle: "",
      maintitle: "",
      dudes: true,
      formDataForImage: {
        subtitle: "",
        maintitle: "",
        dudes: true,
      },
    };
  },

  methods: {
    onSubmit() {
      this.formDataForImage = {
        subtitle: this.subtitle,
        maintitle: this.maintitle,
        dudes: this.dudes,
      };
    },
  },
};
</script>

<style>
.poster-creator {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  color: #2c3e50;

  max-width: 800px;
  margin: 5em auto 0;
  width: 90%;
}

form {
  border: 1px solid #eee;
  padding: 1rem 1rem 0 1rem;
}

label {
  display: block;
  margin: 0 0 0.5rem 0;
}

.form-item {
  margin: 0 0 2rem 0;
}

input[type="text"] {
  border: 1px solid #eee;
  padding: 1rem;
  width: 300px;
}
</style>
