<template>
  <div class="poster-creator">
    <h1>Poster Generator</h1>
    <div class="fake-form" v-if="showForm">
      <div class="form-item form-item-template">
        <label for="subtitle">Template</label>
        <select id="template" v-model="template">
          <option value="tt" selected>Jamstack Fridays with T&T</option>
          <option value="pm">Product Meetup</option>
        </select>
      </div>
      <div class="template" v-if="template === 'tt'">
        <div class="form-item-wrap">
          <h2>Jamstack Fridays with T&T</h2>
          <div class="form-item">
            <label for="subtitle">Sub Title</label>
            <input
              type="text"
              id="subtitle"
              placeholder="Subtitle here"
              v-model="tt.subtitle"
            />
          </div>
          <div class="form-item">
            <label for="maintitle">Main Title</label>
            <input
              type="text"
              id="maintitle"
              placeholder="Main title here"
              v-model="tt.maintitle"
            />
          </div>
          <div class="form-item">
            <label for="dudes">
              <input type="checkbox" id="dudes" v-model="tt.dudes" /> Show dudes
            </label>
          </div>
        </div>
        <div class="logo-wrap">
          <img
            width="300"
            src="../assets/tt.png"
            alt="Jamstack Fridays with T&T"
          />
        </div>
      </div>
      <div class="template" v-if="template === 'pm'">
        <div class="form-item-wrap">
          <h2>Product Meetup</h2>

          <div class="form-item">
            <label for="maintitle">Main Title</label>
            <input
              type="text"
              id="maintitle"
              placeholder="Main title here"
              v-model="pm.maintitle"
            />
          </div>
          <div class="form-item">
            <label for="subtitle">Sub Title</label>
            <input
              type="text"
              id="subtitle"
              placeholder="Subtitle here"
              v-model="pm.subtitle"
            />
          </div>
          <div class="form-item">
            <label for="logo">
              <input type="checkbox" value="logo" id="logo" v-model="pm.logo" />
              Show Logo
            </label>
          </div>
          <div class="form-item">
            <label>People</label>

            <label for="lars">
              <input
                type="checkbox"
                value="lars"
                id="lars"
                v-model="pm.people"
              />
              Lars
            </label>
            <label for="tim">
              <input type="checkbox" value="tim" id="tim" v-model="pm.people" />
              Tim
            </label>
          </div>
        </div>
        <div class="logo-wrap">
          <img
            width="150"
            src="../assets/uniform-logo.png"
            alt="Jamstack Fridays with T&T"
          />
        </div>
      </div>
      <div class="form-item">
        <button @click="createImage(template)">Generate poster image</button>
      </div>
    </div>
    <div class="poster-output" v-if="!showForm">
      <generated-img :data="imageGeneratorProps" />
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
      showForm: true,
      template: "tt",
      tt: {
        subtitle: "",
        maintitle: "",
        dudes: true,
      },
      pm: {
        subtitle: "",
        maintitle: "",
        people: [],
        logo: true,
      },
    };
  },

  methods: {
    createImage(template) {
      this.showForm = false;
      this.imageGeneratorProps = {
        template,
        ...this[template],
      };
    },
  },
};
</script>

<style>
.poster-creator {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  color: #1d3557;

  max-width: 800px;
  margin: 5em auto 0;
  width: 90%;
}

.poster-output {
  margin: 1rem 0 0 0;
}

h2 {
  margin: 0 0 1rem 0;
}

.fake-form {
  border: 1px solid #ddd;
  padding: 1rem;
  background: #f1f1f1;
  border-radius: 0.3rem;
}

.template {
  padding: 1rem;
  border: 1px solid #ddd;
  background: #fff;
  border-radius: 0.3rem;
  margin: 0 0 1rem 0;
  display: flex;
}

.logo-wrap {
  flex: 1;
  width: 100%;
  align-content: center;
  display: flex;
  align-items: center;
  justify-content: center;
}

label {
  display: block;
  margin: 0 0 0.5rem 0;
}

.form-item {
  margin: 0 0 2rem 0;
}

.form-item:last-child {
  margin: 0;
}

.form-item-template {
  margin: 0 0 1rem 0;
}

input,
select,
button {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  border-radius: 0.3rem;
}

input[type="text"],
select {
  border: 1px solid #ddd;
  padding: 1rem;
  width: 300px;
}

button {
  border: none;
  background: #1d3557;
  color: #fff;
  padding: 1rem;
  font-size: 1rem;
  cursor: pointer;
}

button:hover {
  background: #161e2e;
}
</style>
