<template>
  <div class="poster-creator">
    <h1>Uniform Poster Generator</h1>
    <p>Create poster images for different content creation projects.</p>
    <div class="fake-form" v-if="showForm">
      <div class="form-item form-item-template">
        <label for="subtitle">Template</label>
        <select id="template" v-model="template">
          <option value="tt" selected>Jamstack Fridays with T&T</option>
          <option value="pm">Product Meetup</option>
          <option value="cl">Change log</option>
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
                value="uniform-pm-lars"
                id="lars"
                v-model="pm.people"
              />
              Lars
            </label>
            <label for="tim">
              <input
                type="checkbox"
                value="uniform-pm-tim"
                id="tim"
                v-model="pm.people"
              />
              Tim
            </label>
            <label for="adam">
              <input
                type="checkbox"
                value="uniform-pm-adaml"
                id="adam"
                v-model="pm.people"
              />
              Adam L
            </label>
            <!-- <label for="kam">
              <input
                type="checkbox"
                value="uniform-pm-kam"
                id="kam"
                v-model="pm.people"
              />
              Kam
            </label>
            <label for="alex">
              <input
                type="checkbox"
                value="uniform-pm-alex"
                id="alex"
                v-model="pm.people"
              />
              Alex
            </label> -->
          </div>
        </div>
        <div class="logo-wrap">
          <img
            width="150"
            src="../assets/uniform-logo.png"
            alt="Uniform Product Meetup"
          />
        </div>
      </div>
      <div class="template" v-if="template === 'cl'">
        <div class="form-item-wrap">
          <h2>Uniform Change Log</h2>
          <div class="form-item">
            <label for="product">Product (+ version)</label>
            <input
              type="text"
              id="product"
              placeholder="Uniform Optimize 8.0.1"
              v-model="cl.product"
            />
          </div>
          <div class="form-item">
            <label for="date">Date</label>
            <input
              type="date"
              id="date"
              placeholder="2021-05-01"
              v-model="cl.date"
            />
          </div>
          <div class="form-item">
            <label for="sitecore">
              <input type="checkbox" id="sitecore" v-model="cl.sitecore" /> Show
              Sitecore logo
            </label>
          </div>
        </div>
        <div class="logo-wrap">
          <img
            width="150"
            src="../assets/uniform-logo.png"
            alt="Uniform Product Meetup"
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
      cl: {
        product: "Uniform Optimize 8.0.1",
        sitecore: false,
        date: new Date().toISOString().split("T")[0],
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
  max-width: 800px;
  margin: 5em 0 0;
  padding: 0 2rem;
}

h1 {
  font-size: 1.875rem;
  font-weight: 800;
  margin: 0;
  line-height: 45px;
}

.poster-output {
  margin: 1rem 0 0 0;
}

h2 {
  margin: 0 0 1rem 0;
}

p {
  margin: 0 0 1rem 0;
  color: rgb(111, 117, 130);
}

.fake-form {
  margin: 2rem 0 0 0;
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
input[type="date"],
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
